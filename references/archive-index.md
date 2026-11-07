# Building and revising the archive index

The index is the archive's main page and the reason the archive exists. It is framed around the reader's own research question from `research-profile.md`, not a neutral taxonomy of the field. A newcomer should be able to read it and understand both the field and exactly where the reader intends to contribute.

Rewrite it after every paper. It is a living argument, not a log.

## Sections, in order

### Hero

The archive title (a short name for the reader's question), the question itself in one or two sentences, one definition tile per colour-coded concept from the profile (`d1` to `d4`, matching `--st1` to `--st4`), and a status line: papers read, gaps open, next paper.

### The field, on two axes

Pick the two axes from the profile that best separate papers which sound similar in their abstracts. Draw the four quadrants; put each paper read as a chip in its quadrant; mark the reader's target quadrant with `quad target`. One line per quadrant says what lives there. If a quadrant fills up, that is a finding: say it.

### The axes every paper gets placed on

All axes from the profile (usually four to six), each with a one-line question and the set of values a paper can take, as chips. Keep values stable across revisions so the matrix stays comparable. Add a value only when a new paper genuinely does not fit.

### Coverage matrix

One row per paper read: short name linked to its map, venue, its value on each axis, and code status. Mark cells that land on the reader's target with `chip hot`. Unread but important papers (closed access, for example) can get a row with "not read" in muted text, so the gap is visible.

### Gap board

Each gap is a card: an id (G1, G2...), the gap in one line, what is missing and why it matters to the reader's paper, and the evidence (which papers support it, which weakened it, date of last revision). Status classes: `open` (nobody has done it), `weak` (partly addressed), `closed` (someone did it).

Rules for the gap board:

- A gap is a claim and is only as strong as the reading behind it. Ten papers is not much reading. Say so in the intro.
- When a new paper weakens a gap, revise the card and move its status. Do not delete it: a closed gap with its evidence is useful history and stops the reader from rediscovering it.
- Rewrite a gap's sentence as it sharpens. The goal is that after enough reading, at least one gap reads like the first sentence of the reader's paper.

### Reading queue

The next papers in order, with venue, authors, code status, and one line on why each is there. Rank by relevance to the open gaps first, then recency, with code-bearing papers promoted. Show read papers as `done`, the next one as `next`, and papers you could not download as `blocked` with the reason. Re-rank after every read: a new paper often surfaces better candidates through its related work.

### Do-not-claim register

Every do-not-claim line from every map, collected, each linked to the paper that rules it out and where (section or table).

### How the archive runs

Selection rules, pace, and where the files live (local folder, published URLs).

## Linking

Every paper page's nav sheet lists every paper, so after adding paper NN, update the nav sheet in papers 01 to NN-1 as well. If pages are published somewhere with their own URLs, use those URLs in all nav links; otherwise use relative file names so the folder works offline.
