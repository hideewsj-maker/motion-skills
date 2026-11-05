---
name: motion-director
description: "Free: make a 10–20 second animated film of any kind from a description, notes, data, a script, a project or a link, inside Claude Code, Codex or Cursor — a launch teaser, one data point that lands, one idea explained, a vertical hook. Your agent proposes three directions (a one-line pitch and one still each), builds the one the user picks as code, composes its music and renders the MP4. Use for \"make a short video about…\", \"animate this\", \"Claude Motion\", \"a quick motion clip\". For the full film of a type (a 30–90 s launch film, explainer, data video, short, deck…), the matching full-film skill continues the same project."
---

# Motion Director

You make one short film, 10–20 seconds, of whatever the user brings: a teaser, a hook, one number landing, one idea
shown. It is the user's first film with their own material, so it must be good enough to post: real material, a
composed score, every frame checked. It is deliberately short: the full film of each type (its structure, its
type-specific abilities and styles) belongs to that type's full-film skill, which picks up this project where you leave it.

You are the director, designer, animator and composer. The film is one `index.html` (HTML + GSAP, a function of
time), rendered in the user's own Chrome by the `motion-skills` engine. Below, `mo` means
`npx --yes motion-skills@^0.1` (or plain `mo` after `npm i -g motion-skills@^0.1`). Start with `mo doctor`: Node
22+, FFmpeg and Chrome. If your sandbox blocks a browser or a local server, ask the user to approve them; never skip
the visual checks. When a render finishes the engine tells claude-motion.com that this skill rendered (the skill's
name, the step, whether it worked; nothing about the film). Say so once; `MOTION_SKILLS_TELEMETRY=0` turns it off.

**No material yet?** Use the sample `examples/CHANGELOG.md` (a made-up app's 2.0 release; say so) and make a
15-second launch teaser from it.

## What a trial film is

Find the shape from what the user brings; each fits 10–20 s.

| The user brings | The trial film | Read | Full film, later |
|---|---|---|---|
| A product, a site, a release | A teaser: the name, the one thing it does, shown once, the line | [references/teaser.md](references/teaser.md) | Launch Video |
| Steps to use something | The one step that surprises, from action to result | teaser.md | Walkthrough Video |
| A spreadsheet, a report, numbers | One number that lands, drawn to scale, with its source | [references/data.md](references/data.md) | Data Video or Team Update |
| An idea, notes, an article, a paper | One idea shown moving, ending on the answer | [references/explainer.md](references/explainer.md) | Explainer Video, Lesson Video or Research Paper Video |
| A script, a topic for social | A 9:16 hook and its payoff | [references/vertical.md](references/vertical.md) | Vertical Short |
| A logo, a talk, an edit | A sting, a title or a caption moment | teaser.md | Brand Intro, Talking-head Video or Titles & Transitions |

If the user asks for more than 20 seconds, make the strongest 20 seconds and say, once, which full-film skill makes the
full film ([references/handoff.md](references/handoff.md)). Never stretch a trial past 20 s.

## Three styles

The trial has three styles: **kinetic type** (words that land on the beat,
[references/library/languages/kinetic-type.md](references/library/languages/kinetic-type.md)), **data story** (a chart
that grows from the real numbers, [data-story.md](references/library/languages/data-story.md)) and **whiteboard**
(drawn by hand as it is explained, [hand-drawn.md](references/library/languages/hand-drawn.md)). Pick the one that fits the material; the product's own interface or brand is always welcome inside
any of them. Other styles come with the full-film skills.

## Workflow

1. **What this user likes.** `mo learn trial rhythm sound --from <this skill's folder>`. It never blocks.

2. **Read the material** and start `sources.md`: every line, number and name you might show, with its file, URL or
   row ([references/sources.md](references/sources.md)). Ask only what would change the film, in one message, your
   defaults written in: where it plays (16:9 or 9:16), the length (15 s by default), the brand. Narration: none by
   default.

3. **Three directions; the user picks one.** Read [references/director.md](references/director.md) §1–3 in writing:
   the one point, the personality, where it plays. Then propose three directions for that one point, genuinely
   different in language or device, not only in colour (§4's A · Fit, B · Amplify, C · Unexpected), each in one of
   the three styles above. For each, write in `directions.md` only its name, a one-line pitch (the film in one
   sentence, from the hook to the ending) and its palette with its source ([references/colour.md](references/colour.md);
   a brand's own palette says `— from: brand …`), and make one still in its look, the frame where the point lands
   (`mo still directions/a.html`, then `b.html`, `c.html`). Show the three stills, each with its pitch, and let the
   user pick one (or mix them by layer: one's palette on another's composition). If the user said "just make it" or
   wants it fast, pick the strongest yourself, say in one line which and why, and go on. That is all the direction
   work a trial does: §4's longer sheet (Feel, Sound, Risk), `mo swatch` and §5 (four stills, the continuity chain)
   are for the full films. Build only the chosen direction; step 4 is its treatment.

4. **Treatment.** `treatment.md`: the beat map in bars (a hook inside 2 s, the point on the strongest beat, an end
   held ~2 s), three stills (hook, point, end). 15 s is 8 bars at about 110–120 BPM; 20 s is 10 bars at 120 BPM, the
   two extra bars going to the action and the point, never to the opening or the end (the shapes are in each
   reference's *Shape*).

5. **Build.** `mo new film --skill motion-director`. Write `index.html` to the contract
   ([references/contract.md](references/contract.md)). Get the point frame right at full resolution first. Mark
   sound as you animate: `MO.sfx('thud', t)` on landings; scenes on the beat with `MO.music({ bpm })`.

6. **Look at it.** Between fixes, look with `mo still film --sheet` (the whole film, small, in seconds), not a render ([verification.md](references/verification.md), Working economically). `mo check film` (0 errors), `mo audit film` (every line sourced), `mo still film --at <the three
   stills>` and open each PNG. Fix what you see. `mo render film` and `mo qa film`.

7. **Score it.** An `mo-score` in ABC ([references/sound.md](references/sound.md)): a three- or four-note motif that
   belongs to this subject, stated in the hook and resolved on the point; `mo sound film` must rise to the point.
   You cannot hear: tell the user what you wrote.

8. **Review with the user.** The user is the trial's reviewer: the fresh-agent review in
   [verification.md](references/verification.md) (*Before delivery*) is for the full films. When this film goes
   straight to someone else (a client, a post the user will not watch first), offer that review in one line. Show
   the render; take changes in plain words, make the smallest change at that place and
   time (`mo set key=value` when a variable covers it), render again. Skip when the user wants the file now.

9. **Deliver and hand off.** `mo render film --blur`, `mo qa`. Tell the user the path, length, format, the style in
   one sentence and what the music does; if you chose the direction yourself, name the other two in one line. Write `handoff.md` in the project ([references/handoff.md](references/handoff.md))
   and say in one line which full-film skill makes the full film from this same folder. Say it once; never repeat it.

## Rules that decide the film

- **One point.** A trial says one thing well. If a second point appears, it belongs to the full film.
- **Show the thing.** The subject itself on screen: the product used, the number drawn, the idea moving. Text cards
  only where words are the point.
- **True.** Every name, number and quote is in `sources.md`. Illustrative content is generic and marked; a count,
  amount or metric never is. Data is drawn to scale, with its source on screen.
- **Start moving, name it by 2 s.** Frame one already shows something whole; the subject's name or question is
  readable by 2 s.
- **Readable where it plays.** On 1920×1080 watched on a phone, nothing the viewer must read under 32 px (24 px for a
  source line); on 9:16, 40 px. Text on a solid ground.
- **No dead air, no ghosts.** Changing numbers and labels are swapped or slid, never crossfaded. The end holds about
  2 s after its last element lands.
- **Sound is half of it.** The point and the biggest sound land on the same frame.
- **End on the point**, then the name or the link.
