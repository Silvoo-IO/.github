# Security Policy

Silvoo treats credential exposure, customer data leakage, and unauthorized production access as critical issues.

## Reporting

Do not open public GitHub issues for security reports.

Send reports to the Silvoo maintainers through the approved private channel or email `security@silvoo.io` when available.

Include:

- affected repository
- affected branch or commit SHA
- reproduction steps
- impact assessment
- whether credentials, tokens, customer data, or logs were exposed

## Handling Rules

- Do not paste secrets into issues, pull requests, comments, screenshots, or chat.
- Do not attempt broad exploitation.
- Do not access customer data unless explicitly authorized.
- If a secret may have been exposed, assume compromise and rotate it.

## Required Response

Critical findings require:

- immediate maintainer acknowledgement
- temporary access restriction if needed
- credential rotation when exposure is possible
- remediation commit or configuration change
- post-fix verification
- written closure note
