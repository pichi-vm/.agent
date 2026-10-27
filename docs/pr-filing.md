# Pull request filing

A pull request presents a **finished proposal** for human reviewers: a series of
logical commits rebased on `main`, described with Summary / Approach /
Verification — not a stream of consciousness or a diary of how the work was done.

## Commit series

- Rebase onto current `main` before opening or updating the PR.
- Every commit is a **logical** change with a clear Conventional Commit message.
- **Tests (and the repo’s CI checks) must pass for every commit** in the series,
  not only at the tip.
- **Fixup / “fix” commits are not permitted** in the published series. Fold
  corrections into the logical commits (interactive rebase / amend) before the
  PR is ready for review.
- No stream-of-consciousness commits (scratch, WIP, “try again”, tool narrative).

## Body shape

Required headings, in order:

1. **Summary** — What the change is, in plain words (a few sentences). State
   the finished proposal, not a diary of attempts.
2. **Approach** — Only non-obvious decisions that explain the shape of the
   result. Omit chronology, false starts, and tooling narrative.
3. **Verification** — How reviewers can tell it works: which checks, commands,
   or review steps. Prefer the repo’s CI workflow as the source of truth when
   one exists. Every commit in the series must be green. Include this checked
   checkbox (required assertion by the filer):

   - [x] Tests (and the repo’s CI checks) were run and passed for every
     commit in this series independently

## Title

Short, Conventional Commits style when practical (`type(scope): summary`).
Describe the finished change. Do not narrate how the work was produced.

## What not to put in titles or bodies

- Development history (iterations, “tried X then Y”, agent or tool play-by-play)
- Internal process notes, bot roles, workstation names, or hosted coding-agent
  product names
- Merge holds, personal approval gates, or other process notes that belong in
  assistant chat only

Those belong in private notes or separate house-rule docs, not in PR chrome.