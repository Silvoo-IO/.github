# Repository Safety Checklist

Use this checklist when adding repositories, inviting collaborators, or preparing for diligence.

## Required Controls

- Private repository unless intentionally public.
- `main` is the production branch.
- Pull requests required before merge.
- At least one maintainer review required.
- CI required before merge.
- Force pushes disabled.
- Branch deletion disabled.
- Squash merge preferred.
- Merge commits disabled.
- Delete source branches after merge.
- CODEOWNERS present.
- SECURITY.md present.
- Dependabot enabled.
- Secret scanning and push protection enabled when the GitHub plan supports it.

## Branch Protection Status

GitHub Team supports private repository branch protection. Product repositories now have `main` protected.

Use one approval while there is only one trusted maintainer. Move backend, payment-control, infrastructure, auth, payment, matching, risk, migration, and CI changes to two approvals once a second trusted reviewer is active.

## Manual Safeguards Until Upgrade

- Restrict write access to maintainers only.
- Do not grant admin access to contractors.
- Use pull requests by policy even if GitHub cannot enforce them.
- Review `main` after every collaborator session.
- Keep local clones fresh after any history rewrite.
- Keep production credentials outside GitHub repository contents.

## Hard Red Flags

- `members_can_delete_repositories=true`
- `members_can_change_repo_visibility=true`
- `members_can_invite_outside_collaborators=true`
- `members_can_create_teams=true`
- `two_factor_requirement_enabled=false`

These must be reviewed in organization settings and closed as soon as the GitHub plan allows enforcement.
