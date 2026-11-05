# The film contract

Text a viewer reads lives in the markup or in a composition variable: a script may animate it, split it into
words or reveal it, but never write words that are in neither (`mo audit` checks the markup and the variables
against `sources.md`; a line that only a script knows is invisible to it and to the studio).

A project is a folder whose `index.html` is a composition: a root element with `data-composition-id`, `data-width` and `data-height`, and a paused GSAP timeline registered in `window.__timelines[<id>]`. The renderer drives it in the user's own Chrome. That file is the only source: write GSAP, Canvas, Three.js or SVG freely. Everything below is a few extra HTML attributes — no new format. A composition that ignores them still renders; it just can't be pointed at or edited in the studio.

```
my-film/
  index.html      the source
  vendor/         gsap.min.js, mo.js (runtime helpers) and other local libraries
  assets/         fonts, images, audio
  out/            renders from `mo render`; never overwritten
  .mo/            history, comment inbox, render log — maintained by the tools, safe to delete
```

## 1. Editable values are composition variables

Declare them on `<html data-composition-variables='[…]'>`. Types: `string`, `number` (`min`, `max`, `step`), `color`, `boolean`, `enum` (`options`). Optional `group` sorts them in the studio.

- `data-var-text="title"` replaces an element's text.
- `var(--accent)` in CSS — every scalar variable is also a CSS custom property on the root.
- `MO.vars()` once while building the timeline, for data, timing and logic (`window.__hyperframes.getVariables()` in older films still works).
- `data-mo-var="title"` on a container whose text a script builds (per-letter animation), so the studio can edit it in place on a double-click.

The studio and `mo set key=value` change only each variable's `default` value — every other byte stays as written. Good candidates: titles, numbers, colors, hold durations, data arrays (a string holding JSON). If a user might want to change it without you, make it a variable.

## 2. `data-mo-id` names what people can point at

```html
<h1 data-mo-id="title" data-var-text="title">…</h1>
```

Clicks and comments resolve to the smallest clearly visible element carrying an id, and comments arrive with that id and its source line. Keep ids stable when text changes. For things drawn on a canvas, register a region: `MO.region('cat', (t) => [x, y, w, h] /* composition px, or null when absent */, '猫')`.

## 3. Timeline labels `scene:<id>` are the scenes

```js
tl.addLabel('scene:intro', 0).addLabel('scene:chart', 3.2);
```

The studio draws them as the scene strip, and comments carry the scene they were made in.

## Timing

One paused timeline at `window.__timelines[<composition-id>]`. Without `data-duration` on the root, the film is as long as the timeline, so hold variables can change the length — end with the closing hold, e.g. `tl.to({}, { duration: V.endHold })`. Keep every position ≥ 0 (a negative position shifts the whole timeline), and remember `fromTo` renders its start state immediately (`immediateRender: false` or `set` at the moment when something must not exist earlier). The other way round, with `immediateRender: false` the element shows as the page draws it (a bar at full size, a card already up) until its tween starts: hide it from frame 0 in the CSS or with `tl.set(el, { autoAlpha: 0, scaleY: 0 }, 0)`, and check a still taken just before its tween.

## Runtime helpers — `vendor/mo.js`

- `MO.clock(tl, t => draw(t), duration)` — drive a frame-by-frame canvas/WebGL engine from the timeline.
- `MO.region(id, box(t), label)` — pickable canvas regions.
- `MO.cue('word', nth?, 'start'|'end')` — when a narration word is spoken (from `mo voice`); motion anchored to words follows a new recording automatically.
- `MO.vars()` — the variables.
- `MO.sfx(name, at, opts)` — a sound effect at `at` (returns `at`); `MO.music({ product, drop, ending, marks, bpm })` — a built-in direction, or `<script type="text/vnd.abc" id="mo-score">` — your own score, its `!mark:name!`s landing on `scene:name`; `MO.beat(n)` — n beats in seconds. `mo sound` synthesizes them into `assets/sound.wav` + `<audio id="mo-sound">` ([sound.md](sound.md)).

## The comment loop

1. The user presses C in the studio and clicks the frame. The comment records time, position, the object under the pointer, the scene and the current variables in `.mo/inbox.jsonl`.
2. `mo inbox <dir> --wait` blocks until there is one, claims it and prints the context with source lines.
3. You edit `index.html` (or `mo set`). The studio reloads at the same moment.
4. `mo done <id> --note "…"` — the user sees your note. They can answer "not quite" with more detail; the comment comes back to your inbox with the whole thread.
5. Every version lands in `.mo/history/`, whoever wrote it. `mo undo` steps back.
