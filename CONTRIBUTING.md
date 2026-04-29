# Contributing

Silvoo repositories are private operational systems. Treat every change as production-adjacent.

## Required Workflow

1. Create a branch from `main`.
2. Use a clear branch name: `feature/*`, `fix/*`, `chore/*`, or `docs/*`.
3. Keep the change scoped.
4. Run the repository CI command before requesting review.
5. Open a pull request with the default template completed.
6. Wait for review before merge.

## Commit Style

Use conventional commits:

- `feat: add payment review state`
- `fix: prevent duplicate invoice evaluation`
- `docs: update onboarding guide`
- `chore: refresh dependency baseline`

## Forbidden

Do not commit:

- `.env` files
- tokens, API keys, OAuth secrets, private keys, certificates
- production logs
- customer data
- local database dumps
- debug-only code paths
- generated AI transcripts or prompt artifacts

## Review Expectations

Every pull request should answer:

- What changed?
- Why is it safe?
- How was it tested?
- What could break?
- Does it touch credentials, auth, payments, customer data, or deployments?
