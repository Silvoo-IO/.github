# Collaborator Onboarding

This guide is for new Silvoo developers, contractors, and external collaborators.

## First Day

1. Confirm GitHub access is granted through the Silvoo organization.
2. Clone fresh from `Silvoo-IO`; do not reuse pre-transfer or pre-history-rewrite clones.
3. Read the repository `README.md`, `SECURITY.md`, and `CONTRIBUTING.md`.
4. Copy `.env.example` only. Never request or commit real `.env` files.
5. Run the repository CI command locally before opening a pull request.

## Access Rules

- Use the minimum GitHub role required.
- Do not share credentials or tokens.
- Do not add deploy keys without maintainer approval.
- Do not invite outside collaborators without business approval.
- Remove access when work ends.

## Engineering Rules

- Work through pull requests.
- Keep changes small enough to review.
- Treat auth, payment logic, invoice matching, customer data, and deployment paths as high-risk.
- Write clear commit messages.
- Document migrations and operational changes.

## Red Flags

Escalate immediately if you see:

- secrets in commits, logs, screenshots, or issue comments
- direct pushes to `main`
- force pushes to protected branches
- unreviewed dependency upgrades
- unexplained production configuration changes
- tests disabled without replacement
- customer data copied into local files
