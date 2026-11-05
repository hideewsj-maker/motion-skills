# Data stories

The data is the hero; the motion makes one number land.

- **Find the story first.** Read every row. Write the one sentence the numbers support (a turning point, a
  multiple, a comparison) and check it against the file. Compute derived numbers (ratios, totals, growth) and put
  the arithmetic in `sources.md`. If the data supports no story, say so to the user rather than invent one.
- **Exact and honest.** Plot every value from the file, to scale, axes from zero for bars (lines may start higher
  if the axis says so). Round only for reading, and only in a way that keeps the story true ("7.0M", not "7M+" for
  6,994,725). A dip in the data is shown, not smoothed away. Units and the period are on screen.
- **Order of reveal:** the frame (title, axes, period) → the data grows → one annotation lands on the point →
  the number that matters, big. A trial has one chart and one point; several charts are a full Data Video.
- **Source on screen** in the film: the dataset and the date it was retrieved, small but readable. For a file the
  user gave you, its name and the period or date written in it ("sales.csv, 2024–2026"); no retrieval date to invent.
- **Language:** [library/languages/data-story.md](library/languages/data-story.md); the `finance-chart` grammar
  is a fast start for bars, lines and K-lines from a JSON series.
- **Numbers count, they do not appear.** A key number counts up to its value (expo ease, with the `count` effect)
  and holds once it has landed. A counter that runs alongside a chart steps through the real values (one per
  data point), never through in-between figures that are not in the file. Keep the axis scale fixed while bars
  arrive, or early bars shrink on screen.
