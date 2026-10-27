# Pull request filing

A pull request presents a **finished proposal** for human reviewers: a series of
logical commits rebased on `main`, described with Summary / Approach /
Verification — not a stream of consciousness or a diary of how the work was done.

After this file is on `.agent` `main`, Pull Request stamps each PR body with:

`Policy: docs/pr-filing.md@<full-sha-of-this-file-on-main>`

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
   one exists. Note that every commit in the series is expected to be green.
4. **Policy** — Final line only:
   `Policy: docs/pr-filing.md@<sha>`

## Title

Short, Conventional Commits style when practical (`type(scope): summary`).
Describe the finished change. Do not narrate how the work was produced.

## What not to put in titles or bodies

- Development history (iterations, “tried X then Y”, agent or tool play-by-play)
- Internal process notes, bot roles, workstation names, or hosted coding-agent
  product names

Those belong in private notes or separate house-rule docs, not in PR chrome.

## Bootstrap

While this file is not yet on `main`, the bootstrap PR may stamp
`Policy: docs/pr-filing.md@bootstrap` (or the blob SHA of the file on the PR
head). After merge, use the `main` tip SHA.