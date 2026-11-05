# Craft, case by case

## Composition and explanation

First ask what the subject of this shot is, how big the screen is, what must be read, and what is different
before and after the change. Design key frames at the real frame size, to catch small text and crowding early.
"This button in the right half of the screenshot" guides a build better than "a stunning tech feel".

Keep style and composition apart: one set of colours, type and material can take different shot sizes, layouts
and motion. Mixing styles is a legitimate storytelling choice, but what each object is and what it stands for must
stay clear. Do not make every shot the same template just to keep things uniform.

Gather the real material before designing; interfaces, product shapes and how data was counted are facts too.
When something is missing, mark the gap; never fake an interface to show an operation that did not happen.

## Why things move

The most useful motion can be named with one verb: gather, split, align, connect, filter, reveal. Understanding
"what changed" should come mostly from the object changing, not from narration explaining an unrelated animation.

Carrying one object through the film saves the viewer from recognising things anew. Keep a hero across the film
only when the story needs it; "there must be a hero" must not become a mascot bolted onto every video.

A quick art piece can live on one main action plus a loop taken from its material: stars flowing, ink spreading,
colour blocks overprinting. A story reaction, settled text, reading a chart can be completely still. The amount
of motion is a diagnostic hint, not a quality score.

A transition can come from the next scene's signature material (a colour dot growing to fill the frame, paper
unfolding, a line extending), or simply be the camera moving through one world. Use a hard cut when it has a clear
rhythmic or semantic job.

## Camera and pacing

Write each move's target and reason. For information in a screenshot, flat zooming is usually enough; split into
parallax layers only when the depth relation is worth saying. When neighbouring focal points are close, merge or
pan between them; avoid pulling out and pushing back in for nothing.

Frame by first computing the box of the key content, then subtracting the caption area and margins. Whether type
is big enough is checked on the final target screen, not by the font size in code or a fixed ratio.

Use only the weights and styles a font actually has. The engine turns off the browser's synthetic bold and italic,
so `font-weight: 700` on a family with no bold (Instrument Serif has a regular and an italic, nothing heavier) draws
the regular weight, not a smeared fake. For a heavier headline, pick a family that has the weight.

Teaching an operation needs the location and the result to be seen clearly; fast-paced pieces can use quick
push-ins, whip pans or fast scale changes. There is no universal shot length, zoom limit or "slower is safer" rule;
those numbers depend on the material's resolution, the amount of information, the film type and the user's notes.

Emphasis can be a quick start and a firm landing; give springiness only to things that need weight or rebound.
Linear motion is legitimate for constant-speed objects and scrolling backgrounds. No easing curve guarantees a
premium feel.

## Sound and picture

With narration, confirm the track and its word timing first, then design the reveals that must sync. Write a cue
as "when this word is said, the viewer sees the result", not as the start of the motion: if something flies in for
half a second, start it early; the landing is the accent.

Holds are for reading and thinking. When the voice has no breath, slowing the picture cannot create an audible
pause; changing the audio needs the user's permission this time, and the user's own words are never cut or added to
automatically.

## Layers of the build

Concept and timing plan → material and drawing → object animation → camera → captions → mix. Find the layer the
problem is in and change that layer. Weak picture craft does not call for a new timeline; narration that is too
dense does not call for endless camera tweaks.

For a canvas style, first understand how the material is made: stroke layout, colour regions, the layer order of
paper and ink. Cache what is static and let stroke direction evolve continuously; reshuffling randomness every frame
becomes flicker. When a character is placed in, match its light or material, and keep the original image.
