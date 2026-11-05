# Best practice: explaining product use with continuous framing

Read this for product demos, cross-device workflows and short interface films. The reference is ChatGPT's official
[demo of delegating a Codex task from dot](https://x.com/ChatGPT/status/2108636748217770180), published 2026-10-09
and broken down 2026-10-10. Its value is in rhythm, composition and the hand-off of attention; its light ground,
yellow bubbles and device frames are that film's choices.

## Evidence and scope

The original is 1920×1080 at 30 fps, 732 frames, a video track of about 24.40 s. The time windows below start at 0
and are approximate, not a frame-exact edit list. This breakdown checked frames across the whole film, 0.1 s
sequences around the key seams and full-resolution representative frames; it did not include a normal-speed viewing
or a listening review, and it does not judge exact easing, beats, sound or the software used. The source has sound.

"What the picture shows" is what can be seen in the original; "how to borrow it" is an implementation choice
derived from it and not yet proven on an unfamiliar subject. The original is a promo: its run times, test numbers and
packaging prove nothing about the product. What ships with the skill is the method and the source link.

## How the original organises viewing

- About 0.0–0.7 s: the whole phone, centred on white, then a fast zoom that reframes on the input box below. First
  recognise the device, then make the operation the subject; cropping the top of the device is deliberate.
- About 0.8–3.8 s: the request types in letter by letter, the input box grows with each line, the close-up mostly
  holds. The changing text already advances the event; the camera need not wander at the same time. A short hold
  after typing, then send.
- About 3.8–6.6 s: the input clears, the message enters the thread; framing pulls back to the whole phone and the
  reply appears. The close-up explains "how it starts", the whole view "what happens next".
- About 6.6–7.5 s: the phone moves right, a desktop window appears from the left and opens, ending with the desktop
  leading and the phone supporting. The phone and the yellow request stay recognisable; the cross-device relation is
  built by composition, not a new title card.
- About 7.5–10.9 s: the framing is mostly still, three tasks appear in turn, the cursor moves to one. The desktop
  carries the reading, the phone the reference to the source; the two never compete for the same attention.
- About 11.0–12.8 s: a task is clicked, details open on the right; the picture pushes into them as the desktop frame
  and other threads fade. First see where it came from, then remove what is around it.
- About 13.8–16.4 s: a summary and a list of changes appear, the picture is left for reading; about 16.4–17.1 s the
  content moves up and the next "open a PR" request comes in. After about 18.3 s the completed result appears and
  holds. Scrolling content carries the advance; the framing stops changing scale.
- About 20.4–20.8 s: the content clears, a short white frame; about 20.9–21.3 s a notification card enters and
  settles, holding to the end. It reuses the same avatar and sums up the three tasks, closing the opening request
  with one result.

The viewing structure is "whole → close-up of the operation → whole → side by side → close-up of details → result
notification". Borrow the order of cause and effect and re-time it for your own information; do not take 24 s,
three tasks or these seconds as a template.

## Rhythm: short moves, long explanations, each event brings the next shot

First write the story events: typing starts, typing ends, send, reply, tasks appear, click, result, notification.
Then give each framing change a trigger event and a landing point. Split each viewing into "move to the focus →
land → read or the state changes", and time the move and the reading separately. Slowing everything down drags the
joins; speeding everything up swallows the reading.

In the reference, the opening and the cross-device rearrangement are brief; typing, tasks opening and reading the
result take longer. Try a simple framing move of about 0.3–0.8 s as a start and adjust for the target screen and the
distance travelled; this is a starting point for borrowing, not a measured easing or a range for every shot. While
the frame is still, text can type, a list can open or a state can update: the picture holds, the information grows.

A sequential demo links the cursor, the click feedback and the new state. The wait before a result can be compressed,
but never cut to suggest "click and it is done"; keep a working state or show that time passed when needed. Run
times in the reference are picture content, not measurements of this product.

## Composition: one main reading area at a time

The whole view lets the viewer recognise the device and the relations; the close-up lets them read the key text.
In a side-by-side shot, decide what leads: the main window is big enough to read, the supporting device only needs to
be recognised as carrying the same request or source. Change the focus only when the supporting device must be read;
never treat two small interfaces as body text.

Keep a few identity anchors: the same request, an avatar, a bubble colour, a task title. A white ground with sparse
accents makes the subject easy to find; with another brand, use that brand's real identity, not the yellow or the
character. Frames, corner radii, letter spacing and light shadows separate interface layers; strong reflections and
heavy shadows never replace legible text.

Device frames or unrelated sidebars may be cropped to explain. It counts as focusing only when the same focal point
can be found before and after the crop and the key text stays whole; cropping the most important information is a
defect. Check type size and line breaks at the real output resolution and viewing size; an English line length does
not carry over to another language.

## Camera: decide the landing, then how to get there

Write one sentence per seam: `what the previous shot's focus is → where it goes in the next shot → what new
information that makes visible`. The phone moving right to make room for the desktop is a rearrangement of objects;
zooming into the input box is flat framing; details lifting out of the desktop is extracting a layer of information.
They need not all be one 3D camera.

Build four layers apart: interface content and scrolling, device or window frames, a framing wrapper, and fixed
captions. A simple front-on interface needs only DOM/SVG and 2D transforms; adjust object position and framing zoom
separately, so a line break in the input box does not distort the device. Synchronise several layers only for a
clear hand-off, not to make every layer move for the sake of motion.

For flat framing, with the wrapper's local focus `(fx, fy)`, the landing point on screen `(vx, vy)`, the wrapper's
untransformed top-left position in the frame `(bx, by)` and the zoom `s`, the wrapper's translation is
`x = vx - bx - s * fx`, `y = vy - by - s * fy`. This assumes the wrapper's transform origin is top-left, the local
point already includes content scrolling, and no parent adds an unaccounted transform; `bx/by` must not be taken from
an already scaled or moved box. They are 0 only when the wrapper sits at the frame's origin. Animate from the current
pose to this landing, never from a default centred pose each time; a nearby target often needs only a pan.

When details must be lifted out, start them matching their position, size and text in the original interface; once
the viewer recognises them, fade the surrounding frame or push in. The packaging stays a film layer and never poses
as the product's own animation. Screenshot material uses a matching crop or mask; never erase text and write feedback
that does not exist.

A notification can close the film as its own card, reusing the avatar or name to bring the result back to whoever
asked. The original uses a white frame as a separator here and does not require every shot to morph seamlessly; a
white frame is a deliberate full stop, never a cover for a failed load or a dropped frame.

Every pose is decided by one timeline or by absolute time. Set the GSAP wrapper's starting state explicitly; later
`fromTo` calls use `immediateRender: false` where needed, so a future close-up does not appear on the first frame.
Seeking backwards restores the same content, crop and camera.

## In real production and review

When a product demo starts, write a short shot record with the real material:

`event | current reading area | identity anchor kept | start and end framing | content move / framing move | landing time | reading window | new information in the next shot`

Build first the stretch most likely to lose the viewer's bearings, such as "whole device → cross-device side by side →
task details". Check motion and reading with the final material and fonts, then build the rest. The `keynote-ui`
grammar provides titles, cards and screenshot highlights; it does not guarantee continuous cross-device
rearrangement, scrolling content or lifting out details, so use `blank` and write those shots freely when needed.

When reviewing, look separately at:

- Three representative frames: is the whole view recognisable, does the side-by-side have a lead, are the details big
  enough to read. Compare visual weight, white space and the purpose of each framing with the reference; matching
  colours and fonts is not learning the composition.
- A short sequence at each seam: how the old focus hands over to the new, whether position, zoom and content change
  all at once so the viewer has to search again, whether a fast move lands exactly.
- The film at normal speed: are the reading windows long enough, does each still stretch advance the content, does a
  camera move get ahead of the user's action, does the notification answer the opening request. Sampled frames do not
  replace this.
- Sound: follow the main skill's score and effects workflow and design to your own landings; the reference was not
  listened to, so it sets no tempo or sound recipe.

A successful transfer means an unfamiliar subject can also be followed from the request to the result. A first
transfer is a "trial"; after independent review and real user feedback, the changes that worked, the time windows
that failed and the scope go back into `experience.md`. When counter-evidence appears, fix the conclusion; never
raise this film's recipe into a hard rule for all animation.
