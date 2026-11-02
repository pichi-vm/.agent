# Pull request filing

A pull request presents a **finished proposal** for human reviewers: a series of
logical commits rebased on `main`, described with Summary / Approach /
Verification — not a stream of consciousness or a diary of how the work was done.

**The audience rule.** Write pull request **titles**, **bodies**, and every
**commit message** in clear, humble English, without overclaiming or
salesmanship, for a reader with a solid general technical education who
knows the pichi-vm architecture at a high level. Do not define common terms
or project components. Give precise specifics: the exact failure, the
mechanism, and the trade-offs. Give the immediate context for the change;
do not assume familiarity with earlier pull requests or discussions.

## Commit series

Every pull request you review must always follow the principle of minimal,
self-contained, logical changes. Here minimal means the smallest possible
change to achieve the outcome set out in the commit. Likewise: the smallest
number of commits necessary to achieve the stated PR outcome. Never mix two
unrelated changes in a commit or PR.

- Rebase onto current `main` before opening or updating the PR.
- Every commit is a **logical** change with a clear Conventional Commit message
  that follows the audience rule (same rule as titles and bodies).
- **The developer bot (the bot that wrote the code) must run all of the
  repo’s local tests on every commit** in the series, not only at the tip,
  and they must pass. The repo’s continuous integration checks are separate:
  they run on the PR after it opens.
- **Fixup / “fix” commits are not permitted** in the published series. Fold
  corrections into the logical commits (interactive rebase / amend) before the
  PR is ready for review.
- No stream-of-consciousness commits (scratch, work in progress, “try again”,
  tool narrative).

## Body shape

Required headings, in order:

1. **Summary** — What the change is, following the audience rule (a few
   sentences). State the finished proposal, not a diary of attempts.
2. **Approach** — Only non-obvious decisions that explain the shape of the
   result, following the audience rule. Omit chronology, false starts, and
   tooling narrative.
3. **Verification** — How reviewers can tell it works: which checks, commands,
   or review steps, described for the same technical audience. Prefer the
   repo’s continuous integration workflow as the source of truth when one
   exists. Include this checkbox, unticked when the PR is filed. It means the
   developer bot ran all local tests on every commit and they passed; it does
   not cover the continuous integration checks, which run separately on the
   PR:

   - [ ] All local tests were run and passed for every commit in this series
     independently

   Only the developer bot ticks this box. It ticks it after it has run all
   local tests on every commit, and after the Pull Request bot has questioned
   it about those runs and is satisfied with the answers. A person does not
   tick it, the Pull Request bot never ticks or unticks it, and a passing
   continuous integration run is never a reason to tick it.

## Title

Short, Conventional Commits style when practical (`type(scope): summary`).
Describe the finished change following the audience rule. Do not narrate how
the work was produced.

## What not to put in titles or bodies

- Development history (iterations, “tried X then Y”, agent or tool play-by-play)
- Internal process notes, bot roles, workstation names, or hosted coding-agent
  product names
- Merge holds, personal approval gates, or other process notes that belong in
  assistant chat only
- References to earlier pull requests or discussions that substitute for the
  immediate context (commit messages follow the same rule)
- Unexplained shorthand outside general technical knowledge and high-level
  pichi-vm architecture, such as internal finding IDs (`F-PIC-002`), coined
  labels, or bot-internal names (commit messages follow the same ban)

Those belong in private notes or separate house-rule docs, not in the pull
request title or body.