# Contribution and Weekly Update Workflow

## Branch and pull request workflow
1. Start from the latest `main`.
2. Create a focused branch, for example `feat/evidence-retrieval`, `fix/api-validation`, or `docs/setup-guide`.
3. Make a small, coherent change and add/update tests where appropriate.
4. Run relevant checks and record the actual commands and outcomes in the pull request.
5. Open a pull request against `main`, describe the change, link the related issue, and request review.
6. Address review comments and merge only after approval and required checks.
7. Delete the merged branch when appropriate.

## Commit messages
Prefer descriptive messages such as:
- `feat: add transaction evidence filter`
- `fix: handle empty investigation context`
- `test: cover risk queue edge cases`
- `docs: clarify local installation`

## Weekly updates
Create one entry per week in `WEEKLY_UPDATES.md`. Record:
- Work completed (with links to commits, PRs, and issues)
- Tests or validation actually run
- Blockers and decisions
- Next week's plan

Do not backdate entries or claim work, tests, or reviews that did not happen.

## Contribution integrity
Document your own contributions accurately. Cite collaborative work and clearly distinguish personal work from team work. Never commit credentials, tokens, private data, or unlicensed datasets.
