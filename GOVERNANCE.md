<!--
  Copyright (c) 2026 Santander Group
  SPDX-License-Identifier: CC-BY-4.0
-->

# SantanderAI Open-Source Governance

> **Status: DRAFT v0.1 — pending review by Banco Santander OSPO Lead and Legal Counsel.**
>
> This document defines the organization-level operating model for the
> `SantanderAI` GitHub organization (https://github.com/SantanderAI). It is
> intentionally minimal — sufficient to launch the first public repositories
> while the formal OSPO operating model is being finalised. Once the OSPO
> Lead and Legal Counsel sign off, the DRAFT banner will be removed and this
> file will become v1.0.

---

## 1. Purpose and Scope

`SantanderAI` is the GitHub organization through which Banco Santander S.A.
(through its AI Lab) publishes open-source software related to artificial
intelligence research, fraud detection, financial-services data tooling,
and adjacent topics.

This document applies to **every public and internal repository** owned by
the `SantanderAI` organization. It complements (but does not replace)
Banco Santander's internal information-security, intellectual-property and
compliance policies.

## 2. Roles

| Role | Responsibilities | Scope |
|---|---|---|
| **OSPO Lead** | Org owner, policy enforcement, repo publication approvals, member onboarding/offboarding, quarterly access audits, escalation point for any governance question. | Organization-wide |
| **Security Champion** | Security review of every new public repository, secret-scanning alert triage, vulnerability response coordination, supply-chain risk monitoring. | Organization-wide |
| **Repo Maintainer** | PR review, releases, issue triage, community engagement, CHANGELOG and CODEOWNERS upkeep. Named in `CODEOWNERS`. | Per repository |
| **Legal Advisor** | License review, CLA/DCO interpretation, trademark approval, third-party-content clearance. | On-demand |

At least **two** org owners must exist at all times (no single point of
failure). Owners must each have 2FA enforced on their GitHub account.

## 3. Service-Level Agreements

| Process | Owner | SLA |
|---|---|---|
| New repository publication review | OSPO + Security | 5 business days from request |
| External PR — first response | Repo Maintainer | < 1 week |
| External PR — merge or close | Repo Maintainer | < 1 month (or document why longer) |
| Employee offboarding (remove from org, revoke tokens) | OSPO + HR | < 24 hours from termination |
| Security incident response | Security Champion | Per repository `SECURITY.md` SLA (typically < 48 h acknowledgment) |
| Quarterly access review | OSPO Lead | Every 90 days, results minuted |
| Quarterly token / GitHub App audit | OSPO Lead | Every 90 days, inventory updated |

## 4. Publication Decision Framework

Every new public repository must clear the following gates **before** being
flipped from private/internal to public. The OSPO Lead is responsible for
verifying all six gates.

| # | Gate | Question to answer | Sign-off |
|---|---|---|---|
| 1 | **Business value** | What problem does this solve for the community? What does Banco Santander gain by publishing it (reputation, talent attraction, ecosystem influence, regulatory positioning)? | OSPO + Sponsor |
| 2 | **Competitive risk** | Does this give away IP that constitutes competitive advantage? Has the trade-off been explicitly accepted by leadership? | OSPO + Sponsor |
| 3 | **Security risk** | Does the code or its history expose internal infrastructure, secrets, IP ranges, hostnames, or sensitive business logic? Has a history audit been performed? | Security Champion |
| 4 | **Legal clearance** | Is the license (default: Apache 2.0) compatible with all dependencies and contributors? Is a CLA or DCO mechanism in place? Are third-party assets correctly attributed (`NOTICE`)? | Legal Advisor |
| 5 | **Maintenance commitment** | Is there a named Repo Maintainer (in `CODEOWNERS`) with a written 12-month commitment to triage issues and accept contributions? | OSPO + Maintainer |
| 6 | **Quality bar** | Does the repository meet the technical baseline: green CI, ≥ 80% test coverage, all required workflows (lint, test, SAST, dep-scan, license-check, internal-pattern-scan, CLA, release), all `uses:` pinned to SHA, all community files (LICENSE, README, CHANGELOG, CONTRIBUTING, CODE_OF_CONDUCT, SECURITY, CODEOWNERS, issue + PR templates)? | Security Champion + OSPO |

A repository may only be made public **after all six gates are explicitly
signed off**. Sign-offs are recorded as a comment on the GitHub Issue
opened for the publication request, or in an equivalent tracker.

## 5. Branch, Tag, and Push Protection (mandatory in every repo)

These rules are enforced on every public and internal repository owned by
`SantanderAI`. Repository maintainers cannot disable them.

- `main` branch protection:
  - Require pull request before merge (no direct push, including for admins)
  - Require at least 1 approval from `CODEOWNERS`
  - Require all status checks (CI, lint, SAST, dep-scan, license-check, internal-pattern, CLA) to pass
  - Require conversation resolution before merge
  - Require linear history
  - Require signed commits (GPG or SSH)
  - Disallow force-push and branch deletion
- Tag protection on `v*` tags — only repo maintainers may create release tags.
- Push protection — GitHub native secret scanning push protection enabled.
- Dependabot security updates enabled.

## 6. Programmatic Access Controls

- **GitHub Apps preferred over Personal Access Tokens** for any automation
  that touches the org or its repositories.
- All Personal Access Tokens must be **fine-grained**, scoped to the minimum
  permissions required, and carry an expiration of **≤ 90 days**.
- Secrets used by GitHub Actions live exclusively in **encrypted GitHub
  Actions secrets** (repository, environment, or organization scope). No
  secret may be committed to a repository at any time, in any branch, in
  any history.
- A **quarterly token and GitHub App inventory audit** is performed by the
  OSPO Lead. Tokens that are unused, over-scoped, or past expiration are
  revoked.

## 7. Member Lifecycle

### Onboarding

1. Employee receives an invitation to join the `SantanderAI` org sent by
   the OSPO Lead to the employee's individual public GitHub account.
2. Employee accepts and enables 2FA (if not already enforced at org level).
3. OSPO Lead records the mapping `corporate_id → github_username` in the
   internal IAM system.
4. Employee is added to the relevant teams (e.g., `@SantanderAI/<repo>-maintainers`).

### Offboarding

Triggered within 24 h of employment termination by HR notification:

1. OSPO Lead removes the user from all teams and from the organization.
2. OSPO Lead revokes any Personal Access Tokens and SSH keys associated
   with the user that grant access to org resources.
3. If the departing user was a `CODEOWNER` or repo owner, ownership is
   transferred to another active maintainer before removal.
4. OSPO Lead reviews the audit log for the prior 30 days for any
   unexpected activity.

## 8. Decision-Making and Disputes

- **Routine technical decisions** (PR merges, release timing, feature
  prioritisation): the Repo Maintainer decides, in consultation with the
  team named in `CODEOWNERS`.
- **Cross-repo or policy changes** (new mandatory CI check, license policy
  change, new mandatory community file): the OSPO Lead decides after
  consulting the Security Champion and, where applicable, the Legal Advisor.
- **Unresolvable disagreements** are escalated to the AI Lab leadership and,
  if needed, to Banco Santander's Innovation steering committee.

## 9. This Document

- This document lives at https://github.com/SantanderAI/.github/blob/main/GOVERNANCE.md
- Changes follow the same PR-based flow as any other repository (PR + at
  least 1 CODEOWNERS approval).
- The OSPO Lead is the named owner of this document.
- Material changes (sections 2 through 8) require Legal Advisor review.
- Versioning follows SemVer; the current version is recorded in this
  document's header.

---

## Contacts

- General OSPO inquiries: `opensource@gruposantander.com`
- Security incidents and responsible disclosure: `security-opensource@gruposantander.com`
- Legal / IP / trademark questions: route through the OSPO Lead.

---

*This document is licensed under [Creative Commons Attribution 4.0 International (CC-BY-4.0)](https://creativecommons.org/licenses/by/4.0/) so that other organizations setting up an OSPO may reuse it.*
