# Contributing to SantanderAI projects

Thank you for your interest in contributing to a **SantanderAI** open source project. This document covers the contribution guidelines that apply across **all repositories in the organization**. Individual repositories may add a project-specific `CONTRIBUTING.md` with additional requirements (build commands, test layout, etc.).

## Code of Conduct

All participants in our community are expected to follow the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). Report unacceptable behavior to **opensource@gruposantander.com**.

## Governance

All SantanderAI repositories operate under the [open source governance model](GOVERNANCE.md) maintained by the **Open Source Programme Office (OSPO)** — roles, SLAs, publication gates and member-lifecycle policies.

## How to contribute

### Reporting bugs

1. Search the repository's issue tracker first to avoid duplicates.
2. Open a new issue using the **Bug Report** template (when available). Include:
   - Clear, descriptive title
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment details (OS, language/runtime version, dependency versions)
   - Logs or screenshots if relevant

### Proposing features

Open an issue using the **Feature Request** template. Describe the problem, the proposed solution, and discuss with maintainers **before** implementing significant changes.

## Pull request process

### External contributors

1. **Fork** the repository to your GitHub account.
2. **Create a branch** from `main` with a descriptive name (`feature/...`, `fix/...`, `docs/...`).
3. **Make your changes** following the project's code style.
4. **Add or update tests** for any new behavior.
5. **Update documentation** when changes affect public APIs or user-facing behavior.
6. **Use [Conventional Commits](https://www.conventionalcommits.org/)** for commit messages (`feat:`, `fix:`, `docs:`, `test:`, `refactor:`, `ci:`, `chore:`).
7. **Open a Pull Request** against `main`.
8. **Sign the CLA** when prompted by the CLA Assistant bot (see below).
9. **Wait for review** — a maintainer will respond within the project's SLA (default: **2 weeks**).

### Internal contributors (Santander)

Create a branch directly in the repository (no fork required if you are an org member) and follow steps 3-7 above. Request review from the maintainer team listed in `CODEOWNERS`.

### PR requirements (default org-wide checks)

Every PR must pass the following before merge:

- [ ] **CI lint and tests** — formatting, linting, unit tests
- [ ] **Security scan** — secret scanning, SAST, dependency audit
- [ ] **License check** — dependency license compatibility
- [ ] **Pattern check** — no internal URLs, IPs or corporate email addresses
- [ ] **CLA signed** (for external contributors)
- [ ] **At least 1 maintainer approval**
- [ ] **All review conversations resolved**

Individual repositories may add or tighten these requirements.

## Acceptable content policy

Every contribution (code, documentation, data, issues, discussions) must comply with this policy. PRs that do not are rejected regardless of technical quality.

**We accept only:**

- **Original work or compatibly-licensed material** — you hold the rights (per the CLA) or the content carries a license compatible with the project's (attribution included).
- **Synthetic or properly anonymised data** — datasets must document their origin and redistribution rights.

**We never accept:**

- **Secrets** — credentials, tokens, API keys, certificates (push protection and CI scanning will block them; if one slips through, report it via [SECURITY.md](SECURITY.md)).
- **Personal data (PII)** — names, emails, employee IDs or customer data of any kind, beyond voluntary public attribution of the contributor.
- **Real customer, transaction or production data** — including "anonymised" extracts of production datasets.
- **Internal Santander references** — internal URLs, hostnames, IPs, mailboxes or project codenames.
- **License-incompatible or unattributed third-party material** — code or data without redistribution rights.
- **Malicious or offensive-security content** — malware, exploits, backdoors; vulnerability PoCs belong in private reports ([SECURITY.md](SECURITY.md)), not in PRs.
- **Unverifiable binaries** — compiled blobs, pre-trained model weights or datasets without documented provenance and license.
- Content that violates the [Code of Conduct](CODE_OF_CONDUCT.md).

**Enforcement**: automated gates (secret scanning, pattern check, license check, CodeQL) plus maintainer review. Violations already merged are handled per [SECURITY.md](SECURITY.md), including history rewrite when secrets are involved.

## Contributor License Agreement (CLA)

By submitting a pull request you agree to the terms of the SantanderAI Contributor License Agreement: <https://github.com/SantanderAI/cla/blob/main/CLA.md>

The [CLA Assistant](https://cla-assistant.io/) bot will check your PR automatically and ask you to sign on your first contribution. The CLA ensures that contributions can be distributed under the project's open source license (typically Apache-2.0).

## Code style

Each repository documents its own style requirements (linters, formatters, type checkers). As a general expectation across the org:

- Follow the dominant style of the existing codebase.
- Public functions, classes and modules should be documented.
- Source files should include the appropriate copyright header and `SPDX-License-Identifier`.

## Releases

SantanderAI projects follow [Semantic Versioning (SemVer)](https://semver.org/):

- **MAJOR** — incompatible API changes
- **MINOR** — new features (backward-compatible)
- **PATCH** — bug fixes (backward-compatible)

Releases are managed by repository maintainers.

## Questions

- General questions: open a **GitHub Discussion** in the relevant repository (if enabled) or contact **opensource@gruposantander.com**.
- Security vulnerabilities: see [SECURITY.md](SECURITY.md) — never open a public issue.

---

Thank you for contributing to **SantanderAI**.
