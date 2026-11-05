# voice.md — narration

A film that teaches or explains is led by a voice; the picture follows the words. Settle the voice once, with the
other defaults: who speaks, in which language, from which source.

## Sources, in this order

| Source | When | Command |
|---|---|---|
| **The user's recording** | They have one, or will record the script | `mo voice film --audio take.wav --text narration.txt` |
| **ElevenLabs** | The user has an account and wants that voice | `mo voice --voices elevenlabs` to list, then `--voice elevenlabs:<voice_id>` (`@eleven_v3` etc. for another model) |
| **HeyGen** | The user has an account and wants that voice | `mo voice --voices heygen` to list, then `--voice heygen:<voice_id>` (`@starfish` for that engine) |
| **Local, free** | Nothing else; the default | `--lang <language>` picks it: Kokoro for English, Portuguese, Spanish, French; the macOS voice for Chinese, Japanese, Korean, German ([language.md](language.md)). Other English voices: `--voice am_michael`, `bf_emma`, `bm_george` |

- Cloud voices use the user's own key from their environment (`ELEVENLABS_API_KEY`, `HEYGEN_API_KEY`). Ask them to
  set it in their own shell. Never ask for a key in the chat, never write one into a file, a command or the project.
  The text is sent to that provider and billed to their account; say so once before the first call.
- Kokoro downloads its model once (~325 MB): `uv venv -p 3.12 ~/.cache/motion-skills/tts-venv && uv pip install -p
  ~/.cache/motion-skills/tts-venv/bin/python kokoro-onnx soundfile`. Without it `mo voice` falls back to macOS `say`.
- Never imitate a real person's voice, and never present a synthetic voice as a person. Credit it on screen or in the
  end line: "Narration: synthetic voice" (a cloud voice: "Narration: synthetic voice (ElevenLabs)"); a recording is
  credited only as the user wishes.

## The script

`narration.txt`, one sentence per line, written to be heard:

- Short sentences, one idea each; the words on screen are a subset of the words spoken, never a different text.
- Numbers as the viewer should hear them; write `4%` or `four percent`, not a range the voice will garble.
- A line `[pause 5]` holds five seconds of silence after the sentence before it: thinking time for a quiz, a beat
  before a reveal. It is not spoken and not captioned.
- A line `[at 12.5]` starts the next sentence at 12.5 s: for a film already cut to the music (a walkthrough, a
  launch), lay each line on its scene instead of retiming the picture. `mo voice` warns when a line runs into the next.
- At speed 1 Kokoro runs about 175 words a minute with the pauses between sentences (faster inside them): a 60-second
  film holds at most about 150 words, and 130 reads comfortably (numbers and decimals said aloud take longer).
  `--speed` slows any voice, keeping its pitch: 0.8 for a class (about 148 words a minute with breaths between steps), 0.85 for a dense explanation (about 150), 0.68 for a young child (about 120 words
  a minute). Never stretch the WAV afterwards, or the word cues drift. A lesson with three worked steps and a 5-second quiz pause runs 75–90 s: say so rather than rush.
- A voice reads one sentence much faster than the next (a long one fastest), so an average can hide a rushed page.
  `--max-wpm 140` (or the ceiling your director gives) measures each sentence as it is made and reads any over the
  ceiling again, slower, pitch kept (a sentence under six words is left as read, and none is slowed by more than a fifth: short lines are
  quick by nature, and the film's pace is what `mo qa` checks; a `[max-wpm N]` line goes as slow as it takes); a line `[max-wpm 95]` sets a lower ceiling for the sentences after it (the last
  line of a bedtime story), `[speed 0.6]` a speed. A sentence it still warns about reads better broken at a comma onto
  its own line.
- Never speed a voice up to fit a length. When the words do not fit, cut words (a detail can stay on screen without
  being said) or run a little long and say so in the delivery note.
- Names and hard words are where a synthetic voice slips: every name the film says (people, places, the company) and
  every old or unusual word is heard back with `--check`; where whisper hears it differently ("Rose" for Ros,
  "Larkspore" for Larkspur), respell it once with a line `[say Ros = Roz]` at the top of the script and run it again: the voice says the
  respelling, while the captions, the word cues and the screen keep the real spelling.

## Picture on the words

A word whisper hears that the script does not have ("he was on the point of drowning", "I plucked a leaf") is a
sound in the voice until a listener says otherwise: cut that sentence out alone, transcribe it again, and re-voice it
(join the line to the one before, or read it a little faster); never call it a transcript error in the note.

`mo voice film --text narration.txt --voice … --fit --check` writes the cues and the captions (`out/*.srt`), levels
the synthetic voice to −16 LUFS (`--lufs -14` for a feed short, where Instagram and TikTok normalise), and with `--check` hears every sentence back with whisper (`brew install whisper-cpp`)
and lists the ones a listener would not catch: rephrase those or change the voice. Always check a language you
cannot hear yourself. Then time the film from the words, not from bars:

```js
const C = MO.cue;                       // C('word'), C('word', 2) for the second time it is said
const S = { step1: C('Step') - 0.25, answer: C('Ten') - 0.3, end: MO.words().at(-1).end + 1.4 };
tl.addLabel('scene:step1', S.step1);    // scenes start as their first word is spoken
write('#working', C('Five') - 0.1);     // working appears as it is said
```

- `MO.cue('red')` takes the first time "red" is said as a whole word (not inside "scattered"); only when it is not
  said that often on its own does it fall back to a word containing it (`'doesn'` for "doesn't"). Matching ignores
  case, so `C('The')` is the first "the" anywhere. Prefer a phrase to counting: `C('how long')` is "how" where "how
  long" is said in a row, `C('first flight', 1, 'end')` the end of "flight" there; a miss tells you how often and when
  the word is said. Look at a still on every cue.
- `mo voice` writes the cues into `index.html` (`<script type="application/json" id="mo-cues">`, also in
  `assets/voice.words.json`), and `mo sound` writes the `<audio id="mo-sound">` element. If you generate the page
  from a source file, keep both blocks in the source, or run `mo voice` and `mo sound` again after each rebuild.
- Each scene starts on its first word; each figure lands on the word that names it (±0.2 s).
- Hold the last frame 1–1.5 s after the last word.
- Check it after the render: `mo qa film --pace 130-150 --hold 1.5`, or the range and hold your director gives. It
  measures the words a minute over the narration with its pauses (the way this page counts) and each scene while
  speaking, the gaps (under 0.25 s between sentences, under 0.8 s at a scene change, over 2 s that no `[pause]` asked
  for), the hold after the last word, a blank frame mid-film and a picture with nothing new for 12 s under the voice.
  Every ✗ is fixed before delivery: fewer or plainer words, `--max-wpm`, `[pause 0.6]` before a new scene.
- Re-run `mo sound film` after the voice: the score's marks follow the scene labels, and the music is ducked under
  every word and carved around 2 kHz, about 12 LU under the voice.

## Sound with a voice

- Music is a bed: quiet, few notes, no melody fighting the words; or none.
- Effects mark moments the voice leaves room for: a tick under a countdown, one soft hit on a reveal.
- Check the mix: `ffmpeg -i out/film.mp4 -af ebur128 -f null -` near −16 LUFS integrated (about −14 for a feed short); no word masked.
