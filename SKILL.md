---
name: paper-semantic-map
description: Turn a research paper into a deep, visual HTML "semantic thinking map" (a sixty second skim layer on top, the full technical breakdown with equations, every table number and a file-by-file code walkthrough collapsed underneath) and keep a browsable archive whose index page maps all papers read against the reader's own research question, with a coverage matrix, a gap board and a reading queue. Use this whenever someone wants to read, digest, break down, review or "map" a paper, build a reading list or literature archive, find gaps in a field for their own paper, prepare related work, or keep up a weekly paper-reading habit, even if they never say "semantic map".
---

# Paper semantic map

You are helping a researcher read papers in a way that builds toward their own paper. Each paper becomes one self-contained HTML page, and every page links into an archive whose main page shows what the field has covered, where it overlaps, and where the open gaps are. The archive is the point: after ten papers the reader should be able to see explored ideas versus gaps to fill.

Two things separate a good map from a summary:

1. It is written for one reader with one question. "Why it matters to you", "where it stops and your work starts", and "what to do with this" all depend on the reader's research profile. A map without a profile is a generic summary, and this skill exists to avoid that.
2. It is accurate at the level of numbers and code. Every number comes from the paper's own tables, every equation matches the paper's numbering, and the code section reads the released repository, not the README's description of it.

## Files in this skill

- `assets/paper-map-template.html`: the page for one paper. Copy it, fill every `{{PLACEHOLDER}}`, delete the template comments.
- `assets/index-template.html`: the archive's main page.
- `references/research-profile-template.md`: the reader's profile. Copy it to the archive folder as `research-profile.md` on first use.
- `references/paper-map.md`: what each block of a paper map must contain and what makes it good. Read it before writing your first map in a session.
- `references/archive-index.md`: how to build and revise the index page. Read it before touching the index.

Both templates share one design system (the CSS at the top of each). Keep it identical across every page of one archive so the archive reads as one system. Change colours only through the `:root` tokens.

## Step 0: find or create the archive

The archive is a folder (default `paper-archive/` in the working directory, or wherever the profile says). It holds `research-profile.md`, `index.html`, and one `NN-shortname.html` per paper, numbered in reading order.

If there is no `research-profile.md`, stop and build one with the user before reading anything. Ask only what the template needs: the research question, the target venue and deadline, the axes they care about, selection rules (venues, years, code priority), pace, and up to four colour-coded concepts that recur in their work. Offer sensible defaults and keep it to one round of questions. Write the file and show it to them.

If the profile exists, read it fully. Every relevance judgment in this skill comes from it.

## Step 1: pick the paper

If the user names a paper, use it, but check it against the selection rules and say so plainly if it breaks one (wrong venue, too old). Let them overrule you.

If they ask for "the next paper", take the top of the reading queue on the index page. Re-rank the queue first if new information makes the order stale.

When searching for candidates, prefer papers that pass the profile's venue and year filters, have released code, and sit near the reader's question. For a recent preprint, check the profile's rule on preprints before including it.

## Step 2: get the full text and the code

Read the full paper, not the abstract. Try the arXiv HTML or PDF, the venue's open-access page (CVF open access for CVPR, ICCV and ECCV), or the authors' project page.

If you cannot get the full text, tell the user immediately and ask them to supply the PDF. Do not write a map from the abstract and fill the rest from memory. A map built on a partial read is worse than no map, because the reader will trust it.

If code is released, read the repository itself: the model and loss files, the training config, and the entry-point script. Note the commit or release you read.

## Step 3: write the map

Copy `assets/paper-map-template.html` to `NN-shortname.html` and fill it following `references/paper-map.md`. The short version:

- Layer 1, always visible: identity block, the sixty second read (six tiles), one hand-drawn SVG of the real mechanism, and "where it stops, and where your work starts" with one related-work sentence the reader can paste.
- Layer 2, collapsed by default: problem setup, one block per method component with numbered equations, inference and evaluation, data and every number in the paper, the code file by file, weak points a reviewer would push on, and what to do with this for the target venue (open by default), ending with a do-not-claim register.

Accuracy rules, because the reader will cite from this page:

- Copy numbers from the paper's tables exactly. Cite the table number. Never round, recompute or "fix" them.
- If something comes from memory or a secondary source rather than the paper you read, mark it as unverified in the text.
- If the code and the paper disagree, say where, with file names. This is one of the most valuable things a map can contain.
- Keep criticism specific and evidenced. "Only one dataset" is a weakness. "Could be stronger" is not.

## Step 4: update the archive

After every map, revise the index following `references/archive-index.md`: add the paper to the nav, the field map and the coverage matrix; revise the gap board (a new paper often weakens a gap, which is good news to record honestly, not hide); re-rank the reading queue; add any new do-not-claim lines; update the status line. Also add the new paper to the nav sheet of every earlier map so the archive stays connected.

When a new paper changes something an earlier map claimed, add a short `note warn` block to the earlier map ("Revised after reading paper NN") instead of silently editing the old claim.

## Step 5: check and deliver

Before you hand anything over:

- Open the page (or render it) and check it at desktop and phone width, in light and dark mode.
- Re-check every number in the results tables against the paper.
- Search the page for leftover `{{` placeholders and template comments.

Then give the user the file paths, one line on the paper's verdict, and the one gap-board change that matters most. If the environment can publish HTML pages (for example Claude artifacts), offer to publish the map and the index too, and use the published URLs as the nav links.

## Running on a schedule

If the user wants a steady habit (for example two papers a week), set up a recurring task with whatever scheduler the environment has. Each run takes the top of the queue, writes the map, updates the index, and reports what it did. If a paper cannot be downloaded, the run skips to the next one and lists the blocked paper in the report so the user can supply the PDF.
