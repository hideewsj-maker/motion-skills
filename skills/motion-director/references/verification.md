# Verification and rework

Machines answer what can be measured: does the file decode completely, is the frame count right, are the length
and frame size right, does seeking to the same time give the same frame, are fonts or files missing. Frame checks
cover the key text, the caption area and the landing points of motion; where no automatic detector exists, name the
time windows you checked by hand and do not claim everything was checked.

An independent reviewer gets only: the original request, the final MP4, the chosen direction, the rhythm sheet
(`treatment.md`), the sources table for on-screen text (`sources.md`: which screenshot or page each caption or
UI string came from) and the facts that must be verified. It does not read the maker's explanations first. Without
the sources table, a reviewer mistakes the official site's own sentences for "invented copy". The review must ask
"where does attention start to drift, where does it go flat?" — a review that only checks right and wrong misses
boredom, which is what users reject most often. The report names timecodes, the defect, its severity, how much was
watched and the limits, and is tied to the final file's SHA. Tell apart: not explained, logic error, unreadable
text, rough craft, rhythm flat or out of control, unmotivated camera, technical fault. Check still-frame craft and
continuous motion separately (visual-direction.md): which detail does not hold up close, which stretch does not
move the information forward.

Review is not about chasing one high score. Fix what blocks understanding and use, then verify the original defect
and the seams next to it. A trade-off the user accepted is not reopened without new evidence; when the user says
stop, finish as asked and state the limits of what was verified.

The chosen version keeps its code, timeline, asset references, sound and the identity of the render. Rework starts
from the version actually delivered last and accounts for the patches of earlier rounds. After an export, check that
the target window changed as intended and that nothing else changed by accident; treat encoding differences and
content differences separately.

Checking only screenshots cannot claim the motion was reviewed; running only audio metrics cannot claim a listening
review; converting only a spec cannot claim a new subject's film passed. Confirm a test tool catches a deliberately
broken input, so "all green" does not come from a check that never ran.

Record engineering acceptance and creative acceptance separately. Frame-exact matches prove only the edit's
boundary or determinism, and the number of tests only says which counter-examples are covered; neither proves it
looks good. A sample the user explicitly rejected becomes a technical regression case, with the rejected dimension
noted. After changing a skill, only an independent agent making a real film on an unfamiliar subject counts as a
transfer test; the author simulating two answers in the same context does not.

## Working economically

A film costs the user minutes and tokens; spend them where they change the film. Measured on six example films,
most of both went to full renders after every small fix and to looking at many full-size frames.

- **Between fixes, look without rendering.** `mo check`, then `mo still film --sheet` (the whole film as one small
  image, a frame a second, in seconds) or `mo still film --at <the times the fix touched>`. A full `mo render` is for
  a review round and for delivery, not for each fix. A narration change is heard with `mo voice --check`; the cues
  come from the voice, so its timing needs no render either.
- **Look small first.** Judge layout, rhythm and continuity on the sheet. Open a full-size frame only where you must
  read text or a number or check an edge, and each such frame once.
- **Read each file once.** Do not reread a reference, a source or a script already read in this session; note what
  you need from it the first time.

## Before delivery: a review by someone who did not make it

The agent that made a film is the worst judge of it: it sees what it meant, not the frames. So before delivering:

1. `mo render film`, then `mo review film`. It writes `film/review/`: the film as delivered (and its sha256), contact
   sheets two frames a second, a frame after each scene starts and the last, what whisper hears with times, the
   loudness every second, `mo qa`'s measurements, the request, plan and `sources.md`, and `brief.md` — the reviewer's
   instructions: the six criteria (clear to a stranger, only about this subject, rhythm, craft up close, sound with
   picture, truth), findings as JSON with severity (blocking, major, minor) and timecodes. What lives outside the
   film's folder goes in with `--add <file>` (repeatable): always the user's request in their words, and the material
   the film quotes or shows (a spec, reviews, a data file, a session); `mo review` warns when the kit has no request.
2. Give that folder, and nothing else, to a fresh agent: "Read brief.md in <folder> and do what it says." In Claude
   Code, the Agent tool with a new general-purpose agent — never a fork, which inherits this session and its bias; in
   Codex, `codex exec --sandbox read-only` from that folder. A reviewer of another model family than the maker sees
   other things; say which model reviewed. With no way to start a fresh agent, say so and hand the folder to the user.
3. Fix every blocking and major finding (do not argue one away; when a finding is wrong, say why in the delivery
   note). **One review round.** Check the fixes yourself with `mo still --sheet` and `--at` the times they touched,
   then render once for delivery. A second round, with `mo review` again and a new reviewer, only when the first
   found a blocking problem (a false claim, something unreadable, a broken frame), to see that its fix worked; or
   when the user asks for more. Three at most. (Measured on a launch film: the first round found most of what three
   rounds found, and the second and third roughly doubled the film's tokens.)
4. **The delivery note is part of the film's truth.** It is written for the user, in their words: what was made,
   what was changed from the request and why (first, when it matters; of several changes, the one that changes what
   the viewer sees or believes comes first, in its own sentence), what they must check or decide. Every figure
   in it — length, words, words a minute, loudness — is one you measured on the delivered file (a count of words or
   pages is counted by a script, never estimated; every file you name — `review.md`, a caption file — is delivered),
   and a check you did not make is not claimed ("whisper heard every line" only if the transcript of this render matches the script word for word, names and
   any stray syllable included; otherwise say which words it heard differently). A claim about a whole source ("the book never names Newton",
   "nowhere in the report") is made only of what you read: "not on the pages I had". A claim that a source does not say something ("does not
   mention any rules", "gives no cause") is searched for in the whole text first (its notes and footnotes too) and
   worded as narrowly as the search: "gives no cause for the rise" when it names the directive elsewhere. No tool names or skill
   rules: say what is true of the film, not how it was made; one line says it was reviewed (item 6).
5. **The floor:** never deliver with a blocking finding open — a wrong number, name, date or quotation, a claim the
   sources do not support, something unreadable. If it cannot be fixed, it goes to the user as the first line of the
   delivery note.
6. Beside the film, `review.md`: who reviewed (the model), the scores, what was found and what changed, and anything
   left as it was and why. The delivery note says it in one line, in these words, filled in truly: "Reviewed by N
   fresh agent(s) (<model>); the final render was / was not reviewed again; what was left as it was is in
   review.md." Nothing stronger ("every finding fixed", "independent") unless it is exactly so.
7. A word about quality in the note — "loops cleanly", "seamless", "slow", "readable on a phone" — is a claim like a
   number: make it only when you measured it on the delivered file (the level either side of a loop seam, the pace
   page by page, the type size), and say what you measured.

After latent-variable/shipshow's critic loop (MIT: a fresh critic per round, never the builder; findings by severity;
a floor no cap lowers) and Vincentwei1021/mg-styles-15's review prompt (MIT: frames and measurements first, fixes in
order of impact).
