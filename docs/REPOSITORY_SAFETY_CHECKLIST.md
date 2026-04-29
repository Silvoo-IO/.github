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

## Current GitHub Plan Limitation

GitHub returned a plan-level block for branch protection on private repositories:

`Upgrade to GitHub Pro or make this repository public to enable this feature.`

GitHub returned the same plan-level block for repository rulesets.

Until branch protection or rulesets are available, the organization must treat direct push and force-push prevention as a manual governance gap.

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
- branch protection unavailable on private repos
- repository rulesets unavailable on private repos
- secret scanning unavailable or disabled
- CI checks not required for `main`

These must be reviewed in organization settings and closed as soon as the GitHub plan allows enforcement.
