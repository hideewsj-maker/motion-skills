# Picture craft and shot direction

Read this when making a new animation, when the user asks for a higher finish, or when a film is called rough or
boring. It guides creative judgement; code that runs, frame diffs that pass and a pile of material are not a
certificate of taste. A prototype made to test technology is labelled a prototype and is not promoted to a creative
example.

## First decide what is worth seeing

Translate the brief's goal into visible evidence. Write down the subject, the change, one detail worth getting
close to, and what the viewer understands at the end. "A station runs out of bikes" has the city-wide flow and the
empty dock after the last bike leaves; the number reaching zero and the real empty space should prove each other.

With a reference, look at its real frames and motion, not just the name of its style: note representative frames,
how much of the screen the subject takes, material and light, how shots begin and land, visible speed changes, how
long it holds for reading, and how it joins shots. Keep observation apart from guesswork. A video-understanding model
can add meaning but never replaces checking the frames; a promo's packaging does not prove what the product can do.

For product demos and cross-device interface flows, read [product-demo-continuity.md](product-demo-continuity.md)
when needed: the timing of the reference, the reading area's hierarchy, short framing moves and stable reading,
separating the interface layer from the framing layer, and checking stretch by stretch. When you borrow its
viewing structure, re-time it for this film's amount of information.

Keep the direction that was chosen. Without one, follow the main workflow's selection steps. Do not hand creative
judgement back to the user because "not every parameter was specified".

## Make the picture hold up when the camera gets close

Work back from the real shot size to the precision needed, and spend effort where it is seen:

- Wide shots first: silhouette, depth, light-and-dark groups and the focal point. A city needs block scale, a
  riverbank or main road, varied heights and density, not an even carpet of identical boxes.
- Medium shots add the structure that explains the setting: plinths, windows, eaves, roads and kerbs, bridge
  supports, how a station meets the street. Repeated elements come as a family with variants that follow a logic,
  not random detail everywhere.
- Close shots must deliver material and construction. A bicycle needs a recognisable frame, tyres, handlebar and
  saddle; a dock needs structure and a contact shadow. For another subject, check that object's own structure,
  edges and contact points; do not copy the city list.

Check that silhouette, edge highlights, roughness, translucency or reflection, contact shadows and key and fill
light all describe the same material. Pretty grading cannot fix paper-thin objects, floating contact or wrong
structure. Add fine detail only where it is visible in the final output on the target screen.

2D carries the same responsibility: letterforms, spacing and line breaks; curves and joins; proportion, white space
and visual weight; the crop, resolution and edges of real images. Flat colour, minimalism or a whiteboard can be
very refined; detail does not mean texture on everything.

Pick the representative states that expose this film's main craft risk and render them at final resolution. A
spatial film with scale changes is checked close for construction and wide for composition; a fixed-frame chart or
loop is checked at its densest, sparsest or key-change state, with no shot sizes forced on it for the sake of
checking. Put them beside the chosen direction or reference, note concrete gaps and fix them before building the
whole timeline. A low-detail grey model never stands in for the final style, unless that is what the user chose.

## Write the rhythm as a way of watching

For each shot write "why we look here", then choose the shot size and motion. Keep each shot's note short:

`shot id | what the viewer gets | subject / focus | start and end framing | object action | camera path and speed intent | landing and hold | how it joins the next`

A shot's speed intent should read as a sentence ("drop fast to street level, follow the bike close, slow to a stop
at the empty dock"), not one smoothstep repeated through the film. Contrast between neighbouring stretches can come
from fast and slow, wide and close, direction, density, which motion leads, or motion and stillness; choose by
content, with no quota of devices.

- Push in: pull evidence out of a relationship; the subject's position and the landing frame are clear.
- Pull out: show which system a detail belongs to; new information must really appear.
- Track or follow: let the viewer follow one event; foreground parallax helps speed and space.
- Rise, drop or orbit: show structure, occlusion or spatial relations a flat view cannot.
- Hard cut or match on action: change the question being watched, the story moment or the scale of telling. There
  is no need to invent a fancy transition for every change.
- Stillness: let an event finish, information be read or a feeling land. A held frame still needs a composition
  worth looking at and a change that has happened.

Fast shots can be short and decisive; slow shots must add information or be worth watching. When a film needs a rich
rhythm, smooth drifting throughout should be questioned; even motion is still right for constant-speed processes or
a deliberately calm character. Do not raise any past film's "slower is better", shot length, zoom limit or cut quota
into a general rule of taste. The user's explicit rhythm notes this time come first.

In continuous tasks such as web operations or reading an article, keep the cursor, button, document or text the
viewer is tracking. Decide each seam first: where the previous state's focus lands in the next state and how it gets
there; when the state changes, avoid resetting framing, zoom and viewing direction all at once. Waiting can be
compressed, but changing speed is not the same as suddenly changing the picture. Use a hard cut only when the film
needs to change the question being watched and the viewer can still find their place; when the user has pointed out
a break, fix the spatial and action continuity first instead of adding more cuts for rhythm.

Design the landing first; the speed curve serves the landing. Quick acceleration, following, a sudden stop and a long
settle are different choices; never apply one easing to every object and the camera. Key text is stable and sharp
while it must be read; fast motion need not keep every frame readable, but a key fact should never only flash past
in motion blur. When grouping or ordering is itself the explanation, group names, numbers and content stay
trackable; a fixed caption layer is independent of the scene camera and never leaves the frame by accident.

## Build the hardest stretch first, then expand

Make the most important change in viewing a playable short stretch with real picture detail. A film with camera
moves proves the shift of viewpoint and the landing; a fixed-camera piece proves the object's states, the density
of information or the loop seam, without inventing viewpoint changes and pauses. Use the final render path, not a
slide storyboard or a written description in place of motion.

After playing it through, ask: where is the eye led? At which moment does new information appear? Where is only the
camera gliding while the content does not advance? Put the diagnosis on timecodes. If the reference has clear
contrast in speed and shot size and the draft is still one slow drift, re-plan the shots instead of speeding
everything up.

While building, treat three layers separately so the wrong patch is not applied:

1. Looks cheap: check construction, material, light, letterforms and compositing; not more camera moves first.
2. Looks boring: check how the explanation advances and the variation in shot size, speed and landing; not more
   decorative particles first.
3. Hard to understand: check focus, object identity, data and reading time; not more narration first.

In a product promo, real material constrains the facts and the product's identity, but the film need not pan across
whole screenshots. To show a change, lift one sentence, number or card out of the real page as its own layer, let it
come into focus, separate, take the change and return to its place. Source text and data stay exact; the film's
packaging stays distinct from real controls; an effect is never passed off as a native feature. Keeping the
reference to the page and the return to place is what gives depth and speed changes their meaning.

## Implementation must keep creative freedom

Keep camera and object motion in separate layers; keep the shot list, scene assets and story events apart. Sample
the camera by absolute time, record cuts explicitly, seed all randomness. Playing through, seeking backwards and
re-rendering a single frame must give the same state.

Choose tools by the picture: SVG or canvas for exact graphics; Three.js or offline 3D for real perspective,
occlusion, material and light; licensed images, footage and generated material each for their own content. Do not
lower the picture to fit a ready-made text/shape/image/chart format. Advanced drawing can go the free-source route,
stating what editing it still guarantees, with an adapter built later.

Let the user work in their own words ("this bike", "this tracking shot", "hold the close-up a beat longer"); object
ids, camera parameters and time mapping are kept by the agent and the tools. What is parameterised is creative
decisions, not only colours and titles. After changing material, construction, camera path or rhythm, look at the
real render again.

## Creative acceptance and transfer

An independent reviewer gets the user's request, the chosen direction, the reference and the real film, and not the
maker's notes or test scores first. It names concrete defects and time windows: is structure or material rough, is
the focus clear, is the rhythm uniformly calm or uniformly frantic, which camera move added no understanding. Stills
check craft and continuous viewing checks rhythm; neither replaces the other.

Aiming for "top quality" means iterating until the concrete problems are solved, not awarding yourself a high score.
A film the user explicitly rejected is never again called a quality benchmark; its engineering tests keep only what
they prove.

Transfer a change to an unfamiliar subject by having an agent that did not write the skill make and render a real
film, then review it independently. Redoing only the city proves only the city improved; writing only a storyboard
is only a planning trial. A comparison uses the same subject, tools, material, time budget and delivery spec, with
the films watched anonymously and in random order; the author never plays the baseline or the judge. One success is
case evidence, not proof that every user will reliably make top work.
