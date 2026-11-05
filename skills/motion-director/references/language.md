# language.md — a film in the viewer's language

A film is made in one language, the language of the people who will watch it: every word on screen, the narration
and the captions. Settle it once with the other defaults ("Language: Brazilian Portuguese"); never mix languages on
screen except for names, product terms and quoted sources.

## Type

| Language | Family (`mo fonts add …`) | Weights |
|---|---|---|
| English, Portuguese, Spanish, French, German, Italian | any Latin family (Inter by default) | all |
| Simplified Chinese | Noto Sans SC; LXGW WenKai for a hand-drawn feel | 500–900 |
| Traditional Chinese | Noto Sans TC | 500, 800 |
| Japanese | Noto Sans JP | 500, 800 |
| Korean | Noto Sans KR | 500, 800 |

- Put the CJK family after the Latin one (`font-family: "Inter", "Noto Sans JP", sans-serif`): Latin letters and
  numbers keep the Latin design, the rest falls through.
- The CJK families are subsets of common characters (GB2312, Big5 level 1, JIS X 0208, KS X 1001 + modern Hangul).
  A rare character outside them falls back to a system font and looks different: look for it in the stills, then
  rewrite the word or load a full font for it.
- CJK text has no italics and no letter-spacing; use weight and size for emphasis.

## Layout

- Leave room for the longest language: Portuguese, Spanish, French and German run 20–35% longer than English; set
  boxes by the text they hold, never by the English length.
- Line breaks: Latin breaks at spaces; Chinese and Japanese break between any two characters but never before
  `，。、」）` or after `「（` (CSS `line-break: strict; word-break: normal`); Korean breaks at spaces
  (`word-break: keep-all`).
- Reading time: 0.3 s per word for languages with spaces, 0.1 s per character for Chinese and Japanese.

## Numbers, dates, money

Write them as the viewer writes them, computed from the variables with `Intl.NumberFormat` / `Intl.DateTimeFormat`
and the film's locale (`pt-BR`, `es`, `fr-FR`, `de-DE`, `ja-JP`, `zh-CN`, `zh-TW`, `ko-KR`):

| | en | pt-BR | de | fr | zh / ja |
|---|---|---|---|---|---|
| number | 1,234.5 | 1.234,5 | 1.234,5 | 1 234,5 | 1,234.5 |
| percent | 25% | 25% | 25 % | 25 % | 25% |
| date | Oct 24, 2026 | 24/10/2026 | 24.10.2026 | 24/10/2026 | 2026年10月24日 |

A currency stays the source's currency (a US price stays in dollars); never convert without a rate and its date.

## Sources in another language

The source is quoted in the film's language and marked as a translation; `sources.md` keeps the original words:

```markdown
| “Primeiro encontramos o valor do aumento…” (tradução nossa) | OpenStax Prealgebra 2e 6.2: "first we find the amount of increase…" (translated) |
```

Names of works, institutions and products stay as published.

## Voice

`mo voice film --text narration.txt --lang <language> --fit --check` picks the free voice for the language, then
hears every sentence back and lists any a listener would not catch
([voice.md](voice.md)):

| Language | Free voice | Note |
|---|---|---|
| English | Kokoro `af_heart` | |
| Portuguese (Brazil), Spanish, French | Kokoro `pf_dora`, `ef_dora`, `ff_siwis` | |
| Chinese, Traditional Chinese, Japanese, Korean, German | macOS `Tingting`, `Meijia`, `Kyoko`, `Yuna`, `Anna` | macOS only |

Where the free voice is a macOS one, tell the user once that their own recording, or their ElevenLabs or HeyGen
voice, will sound better; elsewhere, without macOS, those are the only options for these languages.

Write the script in the spoken language from the start, never translated word for word from English: numbers as
they are said, short sentences, the local way to address the viewer.
