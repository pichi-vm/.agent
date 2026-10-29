# Pull request filing

A pull request presents a **finished proposal** for human reviewers: a series of
logical commits rebased on `main`, described with Summary / Approach /
Verification — not a stream of consciousness or a diary of how the work was done.

Write the pull request **title**, **body**, and every **commit message** in
simple, straightforward, humble English. A normal human reviewer should
understand what changed and why without specialized shorthand. Prefer ordinary
words. If you must use a specialized term or acronym, define it in the same
title, body, or commit message the first time it appears.

## Commit series

- Rebase onto current `main` before opening or updating the PR.
- Every commit is a **logical** change with a clear Conventional Commit message
  in simple, straightforward, humble English (same rule as titles and bodies).
- **The developer must run all of the repo’s local tests on every commit** in
  the series, not only at the tip, and they must pass. The repo’s continuous
  integration checks are separate: they run on the PR after it opens.
- **Fixup / “fix” commits are not permitted** in the published series. Fold
  corrections into the logical commits (interactive rebase / amend) before the
  PR is ready for review.
- No stream-of-consciousness commits (scratch, work in progress, “try again”,
  tool narrative).

## Body shape

Required headings, in order:

1. **Summary** — What the change is, in simple, straightforward, humble English
   (a few sentences). State the finished proposal, not a diary of attempts.
   Avoid unexplained jargon.
2. **Approach** — Only non-obvious decisions that explain the shape of the
   result, still in simple, straightforward, humble English. Omit chronology,
   false starts, and tooling narrative.
3. **Verification** — How reviewers can tell it works: which checks, commands,
   or review steps, described so a normal human can follow them. Prefer the
   repo’s continuous integration workflow as the source of truth when one
   exists. Include this checked checkbox. It means the developer ran all local
   tests on every commit and they passed; it does not cover the continuous
   integration checks, which run separately on the PR:

   - [x] All local tests were run and passed for every commit in this series
     independently

## Title

Short, Conventional Commits style when practical (`type(scope): summary`).
Describe the finished change in simple, straightforward, humble English. Do not
narrate how the work was produced.

## What not to put in titles or bodies

- Development history (iterations, “tried X then Y”, agent or tool play-by-play)
- Internal process notes, bot roles, workstation names, or hosted coding-agent
  product names
- Merge holds, personal approval gates, or other process notes that belong in
  assistant chat only
- Unexplained jargon, acronyms used as shorthand, or insider terms that a
  reviewer would need outside context to understand (commit messages follow the
  same ban under Commit series)

Those belong in private notes or separate house-rule docs, not in the pull
request title or body.