# Silvoo GitHub Access Control Model

Company: Djalo Ventures OU  
Product: Silvoo  
Owner: Jonathan / Djalo Ventures core ownership

## Executive Summary

Silvoo repositories contain sensitive product IP, financial logic, contract-invoice matching logic, risk evaluation logic, integration code, architecture, deployment configuration, and customer-adjacent workflows.

Access must be granted by least privilege. External collaborators must receive repository-scoped access only, never broad organization access by default. Production secrets must remain outside GitHub repository contents and unavailable to external collaborators.

## Access Principles

- Use least-privilege access by default.
- Grant repository-level access unless organization membership is clearly required.
- Do not grant admin access except to owners.
- Block direct pushes to `main`, `production`, and `release/*`.
- Require pull requests for all changes.
- Require signed NDA and IP assignment before access.
- Keep production secrets restricted to owners and approved operators.
- Separate frontend-only work from backend and infrastructure work where possible.
- Time-bound access for external collaborators.

## Recommended Team Structure

| Team | Purpose | Default Org Role | Repository Access |
| --- | --- | --- | --- |
| Owners | Company ownership, billing, security, secrets, repo creation | Organization owner | Admin only where required |
| Core Backend | Backend APIs, matching, integrations, database logic | Member | Maintain on backend |
| Core Frontend | Frontend UI and product workflows | Member | Write on frontend/payment UI repos |
| Payment Control Maintainers | End-to-end Payment Control ownership | Member | Maintain on payment-control |
| Security Reviewers | Auth, secrets, CI, deployment, governance review | Member | Maintain on sensitive repos |
| External Frontend | Scoped UI contributors | External collaborator preferred | Write on assigned frontend repo only |
| External Backend | Scoped backend contributors | External collaborator preferred | Write on assigned backend repo only |
| Advisors | Non-coding stakeholders | No code access by default | Sanitized docs only |

## Repository Access Matrix

| Role | Frontend | Backend | Payment Control | Infrastructure | Docs |
| --- | --- | --- | --- | --- | --- |
| Owner | Admin | Admin | Admin | Admin | Admin |
| Core Developer | Maintain or Write | Maintain or Write | Write if needed | Read or None | Write |
| External Frontend | Write | None | None unless approved | None | None or Read |
| External Backend | None or Read | Write to scoped repo only | None unless approved | None | None or Read |
| Advisor / Investor | None | None | None | None | Sanitized read-only docs only |

## Current Silvoo Repository Classification

| Repository | Sensitivity | Default Access |
| --- | --- | --- |
| `silvoo-Backend` | High | Core Backend and Security Reviewers only |
| `silvoo-payment-control` | High | Payment Control Maintainers, Core Frontend, Security Reviewers |
| `.github` | Medium/Public | Owners and maintainers for governance docs |
| Future `silvoo-infrastructure` | Critical | Owners only |
| Future `silvoo-public-demo` | Low | External-safe work only |

## External Collaborator Policy

External collaborators must:

- sign NDA and IP assignment before access
- receive access only to the assigned repository
- receive no organization-wide access unless explicitly approved
- receive no admin access
- receive no production secrets
- work only through branches and pull requests
- be removed immediately when work ends

External collaborators must not:

- access production systems
- access billing or organization settings
- invite other collaborators
- approve their own pull requests
- fork sensitive private repositories without written approval
- copy customer data, contracts, invoices, logs, or datasets into local files or issues

## Forking Policy

Default position: forks are restricted for private sensitive repositories.

Allowed:

- low-sensitivity public demo repositories
- temporary private forks only when explicitly approved and controlled
- branch-based collaboration inside private repos for trusted developers

Not allowed:

- public forks of private Silvoo repositories
- forks containing secrets, customer data, contracts, invoices, private datasets, or `.env` files
- forks of infrastructure repositories unless explicitly approved

## Branch Protection Rules

Protect:

- `main`
- `production`
- `release/*`

Required:

- pull request before merge
- status checks must pass
- conversation resolution required
- CODEOWNERS review required
- stale approvals dismissed on new commits
- linear history where practical
- force pushes disabled
- branch deletion disabled

Review count:

- frontend-only changes: at least 1 approval
- backend, payment-control, infrastructure, auth, payments, matching, risk, integrations, migrations, CI, or security-sensitive changes: target 2 approvals
- current operational minimum while only one trusted maintainer exists: 1 approval plus CODEOWNERS

## Pull Request Review Rules

Every contribution must go through a pull request.

Security-sensitive areas require trusted review:

- authentication and authorization
- payment-control logic
- invoice-contract matching
- risk engines and scoring logic
- provider integrations
- database migrations
- CI/CD and GitHub Actions
- environment and secret handling
- logging and PII handling

External collaborators cannot approve their own PRs. AI-generated code must be reviewed like human-written code.

## Secret and Environment Access Policy

- Never commit `.env` files.
- Never commit tokens, private keys, certificates, OAuth secrets, API keys, customer data, logs, contracts, invoices, or dumps.
- Use separate development, staging, and production environments.
- Production secrets are owner-only unless explicitly approved.
- External collaborators receive no production secrets.
- GitHub Actions secrets must be repository-scoped and environment-scoped where possible.
- Rotate secrets when a collaborator leaves or exposure is possible.
- Enable secret scanning and push protection when the GitHub plan supports it.

## Onboarding Checklist

Before access:

- signed NDA
- signed IP assignment agreement
- role and scope confirmed
- repository access confirmed
- access duration confirmed
- no production secrets needed

Grant access:

- prefer repository-level external collaborator access
- assign least-privilege role
- add to team only when organization membership is needed
- confirm branch and PR workflow
- confirm security rules

After access:

- assign first task with limited scope
- require pull request for all changes
- inspect first PR for architecture, security, and credential handling

## Offboarding Checklist

Immediate actions:

- remove GitHub access
- remove from teams
- revoke repository permissions
- revoke Vercel, Supabase, Slack, Linear, Notion, email, and related access
- rotate shared secrets if exposure is possible
- review recent commits and PRs
- archive or transfer unfinished branches
- confirm deletion or return of local materials under signed agreement

## Emergency Access Revocation

Use this process for suspected credential exposure, contract termination, malicious behavior, or compromised accounts:

1. Remove the user from the organization and all repositories.
2. Remove team memberships.
3. Revoke linked SaaS access.
4. Disable or rotate any shared credentials.
5. Review commits, branches, PRs, Actions logs, and deployments from the prior 30 days.
6. If secrets were exposed, rotate immediately and open a private incident record.
7. Require fresh clone after any history rewrite.

## Current Red Flags To Monitor

- Organization-wide 2FA must be enabled.
- Repository deletion and visibility-change permissions must remain owner-only.
- Outside collaborator invitations must remain owner-controlled.
- Two-review enforcement should be activated once there are at least two trusted reviewers.
