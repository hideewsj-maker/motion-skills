# reference.md — learning from a film the user likes

"Make it like this." You cannot play the video: everything you know about it comes from numbers you measure and
pictures you extract and look at. Measure first, then look, and say which is which. Take the craft, never the
content.

## Get the film

- A file the user gives you: study it where it is (never move or edit their original).
- A link: ask before downloading anything (what, from where, how large). If it will not download or play, say so and
  ask for the file. Never describe a film you could not open.
- Stills or screenshots give palette, type and layout, not motion: ask whether a moving reference exists.
- Several references: give each one job ("type and palette from A, the pacing of B"), and do not mix looks just to use
  every reference.

## Measure

```bash
mo study ref.mp4                      # → study/ref/: study.md, study.json, contact sheets, shots/, cuts/
mo study ref.mp4 --at 3.2,7.5         # + 12 consecutive frames from each time: an entrance, a landing
```

`study.md` gives: format; shots, with hard cuts, soft cuts (a subject swapped on the same ground) and transitions that
replace the frame; shot lengths and cuts a minute; moves between holds, their ease shape (ease-out, ease-in,
ease-in-out, steady) and, for a pan, how far the content travels; the share of time the picture holds; palette and
tone; whether it loops; loudness, tempo and how many cuts and move starts sit on a beat.

A motion-graphics film often changes scene without replacing the frame (new type on the same ground): there are no cuts
to find, so read its rhythm from the moves and the sheet. Tempo from a listen is a guess; the measured one is the
number (a model "hearing" 120 BPM in a 128 BPM track is common).

## Look, in this order

1. **The sheets**: the whole film at once. What changes from tile to tile: type, layout, camera, colour?
2. **`shots/`** at 960 wide: the type (family class, weight, width, case, size against the frame height), margins,
   alignment, the grid. The frame that stands for a shot is its last before the cut, not the one you like best.
3. **`cuts/`**: how each cut or wipe works, frame by frame. "A square wipe" seen at sheet speed is often eight bars
   falling in turn, each with a bounce.
4. **`--at` strips** around the moments the brief cares about: what enters, in what order (product, then headline
   +0.1 s, then label +0.25 s), how far it travels, whether it overshoots, how long it holds before the next thing.
5. **Inside each shot**: what keeps moving while the shot "holds" (a glint, a drift, a counter). Missing this is how a
   remake becomes still pictures with transitions between them.

## Write it down: `reference.md` in the film's folder

One line per finding, each labelled:

```text
Source: ref.mp4, 1920×1080, 30 fps, 22.4 s, with sound.
Shots      14, median 1.4 s, 38 a minute; 9 of 13 cuts within 0.07 s of a beat (122 BPM).           [measured]
Entrance   3.20–3.70 s: card from y+60, opacity 0→1, scale 0.96→1.0, a slight overshoot.           [measured: at-3.20s]
Order      product → headline (+0.10 s) → label (+0.25 s).                                           [measured]
Hold       readable 3.85–6.10 s before the next move pulls the eye.                                  [measured]
Type       a grotesk, heavy, all caps, cap height about 1/9 of the frame.                            [estimated: shots/004]
Our film   our report screen enters the same way and holds 2.2 s.                                    [creative choice]
```

Measured is what `mo study` or a frame shows; estimated is what you judge from a picture (name the frame that would
settle it); a creative choice is yours. Then turn it into rules for this film, one line each.

## Take the craft, never the content

| Take (match it closely) | Never take |
|---|---|
| Palette relations: ground, ink, accent, contrast, saturation | Its logos, brand names, characters, mascots |
| Type feel: class, weight, width, case, tracking, scale | Its words, claims, numbers |
| Layout, margins, where the eye goes | Its footage, photos, drawings, 3D models |
| Motion: curves, durations, stagger, overshoot | Its music, voice or sound effects |
| Pacing, cut rhythm, transitions, camera language | Its frames, in the film or anywhere you deliver |
| Texture and finish: grain, blur, glow, animating on twos | |
| Sound energy: tempo, density of hits, loudness shape | |

With the user's own brand, map the reference's roles onto it (its accent becomes their accent) unless they ask for the
reference's palette. The reference is studied, never shipped: the `study/` folder stays out of what you deliver.

## Check yours against it

```bash
mo study film --compare ref.mp4       # your latest render and the reference, side by side in numbers
```

Shot length, cuts a minute, the share of time holding, ease shapes, tone, palette, loudness, tempo and cuts on the beat,
in two columns. A difference you meant is a creative choice; one you did not is the next fix. Then look at the same
moments of both, frame for frame.
