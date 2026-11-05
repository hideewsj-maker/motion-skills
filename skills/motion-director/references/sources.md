# sources.md

Write it while you read, not at the end. One row per line, number or name that might appear on screen:

```markdown
| On screen | Source |
|---|---|
| 3.1× in two years | sales.csv: 41,200 (2024) → 128,900 (2026); 128,900 / 41,200 = 3.13, shown as "3.1×" |
| Ships Friday. | README.md line 3 |
| Untitled-3.mov | illustrative UI content (a sample file name) |
| a client | illustrative UI content (a generic recipient; no invented person or company) |
```

`mo audit` checks every line on screen against it and fails:

- a line that is not in it (invented, or not yet sourced);
- a number marked illustrative. Counts, amounts and metrics are claims. Two exceptions say so in the row: the
  interface's own state (a playhead time, a version number: "UI state") and a made-up product or file name that
  holds a digit.

**A sample or made-up product** (the shipped `examples/CHANGELOG.md`, or one the user says is made up): its numbers
come from the sample file, so the row cites the file and line and says `sample app detail` (or `sample event / shop /
invitation detail`), and the film says "Sample app" on screen. Never write "sample data" or "made up" in a row with a
number: `mo audit` reads those as illustrative and fails the line.

```markdown
| 1,200 teams in the beta | CHANGELOG.md line 17 (sample app detail; "Sample app" on screen) |
```

A derived number (a ratio, a total, a rounding) shows its arithmetic in the row. Material with no source (the
user's notes) is cited as the user's notes, quoted. Nothing private on screen: no keys, tokens, internal hosts,
real users or emails.
