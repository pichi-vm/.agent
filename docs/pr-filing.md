# Pull request filing

A pull request presents a **finished proposal** for human reviewers: a series of
logical commits rebased on `main`, described with Summary / Approach /
Verification — not a stream of consciousness or a diary of how the work was done.

Write the pull request **title**, **body**, and every **commit message** in
simple, straightforward, humble English. A normal human reviewer should
understand what changed and why without specialized shorthand. Prefer ordinary
words. If you must use a specialized term or acronym, define it in the same
title, body, or commit message the first time it appears.

**The audience rule.** The important thing is getting both the context and
English correct for the audience. This rule applies to pull request titles,
pull request descriptions, and every commit message:

PR messages must be written for a reader who has no context. You must ensure
that full context is given in plain English. This doesn't mean no technical
details. But it does mean avoiding jargon. Do not assume the reader has any
exposure to the development history.

## Commit series

Every pull request you review must always follow the principle of minimal,
self-contained, logical changes. Here minimal means the smallest possible
change to achieve the outcome set out in the commit. Likewise: the smallest
number of commits necessary to achieve the stated PR outcome. Never mix two
unrelated changes in a commit or PR.

- Rebase onto current `main` before opening or updating the PR.
- Every commit is a **logical** change with a clear Conventional Commit message
  in simple, straightforward, humble English (same rule as titles and bodies).
- **The developer bot (the bot that wrote the code) must run the repo’s
  required short local checks on every commit** in the series, not only at
  the tip, and they must pass. These include build, unit tests, clippy,
  actionlint, and gitlint. No bot may run long local VM test suites that take
  hours (for example, 1 to 2 hours), such as full VM lifecycle runs or distro
  boot matrices. These run in PR CI; never delay a push or PR to run them
  locally. Lodown's root-only (sudo/loop-device) tests, tests that need
  hardware the developer's machine lacks (macOS, Windows, arm64), and
  pichi's registry write test (bots have no package-write token) may run
  only in CI. The bot still runs every other test its machine can run.
  See [Definition of done](../pichi.md#definition-of-done).
  The repo’s continuous integration checks run on the PR after it opens.
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
   exists. Include this checkbox, unticked when the PR is filed. It means the
   developer bot ran the required short local checks on every commit, with
   the exceptions above, and they passed; it does not cover the continuous
   integration checks, which run separately on the PR:

   - [ ] All local tests were run and passed for every commit in this series
     independently

   Only the developer bot ticks this box. It ticks it after it has run all
   required short local checks on every commit, and after the Pull Request
   bot has questioned it about those runs and is satisfied with the answers.
   A person does not tick it, the Pull Request bot never ticks or unticks it,
   and a passing continuous integration run is never a reason to tick it.

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