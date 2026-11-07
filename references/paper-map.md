# Writing a paper map

One page per paper. Two layers. The reader should get the paper in sixty seconds from layer 1, and should never need to open the PDF again for anything in layer 2.

Write in plain, direct sentences. No "moreover", no "in this paper the authors propose", no restating the abstract. Say what the paper does and what you think of it.

## Layer 1: always visible

### Identity block

Eyebrow line: paper number, venue and year (with Oral or Highlight if it was one), subfield. Then the full title, a one-sentence lede saying what the paper is in plain words, and a key-value list: authors and affiliations, venue, code (repo link or "not released"), and what you actually read ("arXiv v2 PDF plus the repo at commit 3f9a1c2"). The "read from" line matters: it tells the reader how far to trust the page.

Chips: code status, datasets, and one `chip hot` if the paper is central to the reader's question.

### The sixty second read

Six tiles, each a few sentences. This block alone should be enough for a reading-group discussion.

1. **The problem it names.** The problem as the paper frames it, in one breath. If the paper defines a new task, say so.
2. **The mechanism.** What it actually does, concrete enough to sketch. Name the components.
3. **Headline result.** One big number, then what it is, against what baseline, on which data. Pick the number that best supports the paper's own claim, and note if it is cherry-picked.
4. **What is actually new.** Often smaller than the paper says. Separate the genuinely new part from careful engineering of known parts.
5. **The honest verdict.** Your judgment: solid, oversold, important but flawed. One or two sentences.
6. **Why it matters to you** (`tile lift`). Relative to the reader's research question in the profile. This is the tile that makes the map worth more than an abstract.

### How it works, in one picture

One inline SVG you draw yourself that shows the real mechanism: the decision rule, the data flow, or the timeline the method operates on. Do not redraw the paper's architecture figure box for box; find the picture that explains why it works. Use only CSS variables for colour (`fill="var(--st1)"`, `stroke="var(--ink)"`) so dark mode works, label in the `svg-label` and `svg-tick` classes, and add an `aria-label`. A short paragraph above it says how to read it.

### Where it stops, and where your work starts

The boundary of the paper measured against the reader's question: what it cannot do, what it assumes, what it never evaluates. Then a `note` with **the one sentence to put in your related work**: a citable, fair sentence that positions this paper and sets up the reader's contribution. Write it so it could go into a paper unchanged.

## Layer 2: the full breakdown

Each block is a `<details>` with a two-digit index, a title, and a one-line teaser that says the block's conclusion, not its topic ("The rank loss is dead code" beats "Implementation notes"). Collapsed by default, except the last block.

### Problem setup

The formal setup: inputs, outputs, notation, what is labelled at train time versus test time. Say what makes the problem harder than its nearest neighbour.

### One block per method component

For each part of the method: what it does, why it is there, and its equations in `div.eq` blocks numbered exactly as in the paper (`<span class="eqno">(3)</span>`). Write equations in plain monospace (`E[p_i] = alpha_i / S_i`), not LaTeX. After the equations, explain the move that matters. Use a `note` for an observation the paper does not make itself, such as a connection to prior work or an inverted assumption.

### Inference and evaluation

How a prediction is produced at test time, every threshold, and the metric. If the paper invents a metric, explain why the old ones were not enough and what the new one rewards. Use `note warn` for evaluation choices that constrain how the reader can compare against it.

### Data, splits and every number

Datasets with sizes and splits, then the paper's results tables reproduced as HTML tables, numbers copied exactly, with the table number in the caption. Mark the paper's own row with `tr.best`. Add a `note` titled "Read this table sideways" when a table says something the text does not (an ablation where one component carries most of the gain, a baseline that is suspiciously weak).

### The code, file by file

Only when code exists. Otherwise one line saying it was not released, and drop the block.

- **Where things are:** a trimmed tree with one comment per file that matters, marking which files are this paper's contribution versus inherited from a base repo.
- **Key pieces as implemented:** short excerpts (a few lines each) of the core loss or module, with file and function names.
- **Where the code and the paper diverge** (`note warn`): dead code, a loss term that is computed but never added, a hyperparameter that differs from the paper. Say "none found" if you looked and found none.
- **Hyperparameters:** a table from the released config, with the config path.
- **Running it:** environment setup and the train and eval commands from the README.

### Weak points, and what a reviewer would push on

A numbered list of specific, evidenced weaknesses: missing baselines, single dataset, unfair comparisons, untested assumptions. Order by how much each one matters to the reader's work.

### What to do with this, for the target venue

Open by default. Concrete actions for the reader: a split or protocol to adopt, a baseline they now have to run, a framing sentence, an idea to borrow. End with a `note` **do-not-claim register**: claims the reader might be tempted to make that this paper already rules out. These lines also go on the index page.

## Footer

Paper number, archive name, read date, and a line on how numbers were sourced.

## Common mistakes

- Writing the six tiles from the abstract. Write them last, after the deep read.
- "Why it matters to you" that would fit any reader. If it does not mention something from the profile, rewrite it.
- Rounded or recalled numbers. Copy from the table.
- A code section that paraphrases the README. Read the source.
- Hiding a paper that weakens the reader's gap. Record it; it saves them from a rejected submission.
