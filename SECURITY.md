# Security Policy

This security policy applies to **all open source repositories** in the [SantanderAI](https://github.com/SantanderAI) organization, unless an individual repository documents its own (more specific) policy.

## Reporting a vulnerability

If you discover a security vulnerability in any of our open source repositories, please report it responsibly. **Do not open a public GitHub issue for security vulnerabilities.**

### How to report

Please use **GitHub's private vulnerability reporting** as the primary channel:

1. **GitHub Private Vulnerability Reporting** (preferred): open the affected repository's **Security** tab → *Advisories* → *Report a vulnerability*. This opens a private advisory visible only to you and the maintainers.
2. **Email** (alternative): if you cannot use GitHub, email **opensource@gruposantander.com**.

### What to include

- Description of the vulnerability
- Affected repository and version (commit SHA, tag or release)
- Steps to reproduce
- Potential impact
- Suggested fix (if any)

### Response SLA

| Stage | SLA |
|:---|:---|
| Acknowledgment of report | < 48 hours |
| Initial assessment and severity classification | < 7 days |
| Fix for Critical / High severity | < 30 days |
| Fix for Medium / Low severity | < 90 days |

### What happens next

1. We acknowledge your report within 48 hours.
2. We investigate and assign a severity.
3. We develop and test a fix.
4. We release the fix and publish a security advisory in the affected repository.
5. We credit you publicly in the advisory and changelog (unless you prefer to remain anonymous).

## Scope

This policy covers **code published in the SantanderAI organization**. It does **not** cover:

- Santander's internal infrastructure, products or customer-facing services
- Third-party dependencies (report those to the respective upstream maintainers)
- Forks or derivative works not maintained by Santander

For vulnerabilities affecting Santander commercial products or infrastructure, follow the disclosure process at <https://www.santander.com/en/responsible-disclosure>.

## Supported versions

Each repository declares its own supported versions in its release notes or `SECURITY.md`. As a baseline across the org:

- **Latest release** — fully supported
- **Previous minor release** — security fixes only
- **Older versions** — not supported

## Security best practices for contributors

- Never commit secrets, API keys, tokens or credentials.
- Never commit internal URLs, IP addresses or corporate email addresses.
- Never commit personally identifiable information (PII) or customer data.
- Use environment variables for any configuration that could be sensitive.
- Keep dependencies up to date — Dependabot is enabled on our repositories.

## Disclosure policy

We follow a **coordinated disclosure** process. We ask that you:

- Give us reasonable time to fix the vulnerability before public disclosure.
- Do not exploit the vulnerability beyond what is necessary to demonstrate it.
- Do not access or modify data that does not belong to you.
