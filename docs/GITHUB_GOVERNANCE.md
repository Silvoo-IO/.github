# GitHub Governance

Silvoo uses GitHub as a controlled engineering system, not a file store.

## Organization Defaults

Configured:

- organization name and description
- default repository permission: read
- repository creation disabled for members
- team structure for backend, frontend, payment-control, and security review
- private repository for product code
- web commit signoff required
- repository projects disabled
- organization projects disabled
- private repository forking disabled
- secret scanning and push protection enabled on product repositories

Requires GitHub UI or plan upgrade review:

- require two-factor authentication for all members
- prevent repository deletion by members
- prevent repository visibility changes by members
- restrict outside collaborator invitations
- prevent team creation by members

## Repository Defaults

Configured:

- issues enabled
- wiki disabled
- projects disabled
- squash merge enabled
- merge commits disabled
- rebase merge disabled
- delete branch on merge enabled
- Dependabot vulnerability alerts enabled
- Dependabot automated security fixes enabled
- CODEOWNERS present in product repositories
- CI workflow present in product repositories
- Dependabot config present in product repositories
- `main` branch protection enabled on product repositories
- production and `release/*` repository rulesets enabled on product repositories

## Required Branch Protection Target

When available, protect `main` with:

- require pull request before merge
- require at least one approval
- dismiss stale approvals
- require CODEOWNERS review
- require status check: `verify`
- require branches to be up to date
- require conversation resolution
- require linear history
- block force pushes
- block branch deletion
- apply rules to administrators

Current enforcement uses one approval while Silvoo has only one trusted maintainer. Move to two approvals for high-risk repositories once a second trusted reviewer is active.

## Repository Deletion Risk

GitHub organization owners can always create severe blast radius. Keep owner count minimal and review audit logs after access changes.
