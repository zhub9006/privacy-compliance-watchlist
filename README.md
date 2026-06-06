# 🛡️ Privacy Compliance Watchlist

A curated watchlist of open-source GDPR compliance and consent management tools for small businesses, with security findings and direct links for ongoing monitoring.

> **Last audited:** June 2026  
> **Purpose:** Help small businesses evaluate open-source privacy tools by surfacing maintenance health, known vulnerabilities, and compliance gaps found in each project's issue tracker.

---

## Table of Contents

1. [Klaro — Consent Management Platform](#1-klaro--consent-management-platform)
2. [Bearer — Security & Privacy SAST Scanner](#2-bearer--security--privacy-sast-scanner)
3. [IBM AI Privacy Toolkit](#3-ibm-ai-privacy-toolkit)
4. [FAZ Cookie Manager — WordPress Plugin](#4-faz-cookie-manager--wordpress-plugin)
5. [PII Guard — LLM-Powered PII Detection](#5-pii-guard--llm-powered-pii-detection)
6. [Summary & Recommendations](#summary--recommendations)

---

## 1. Klaro — Consent Management Platform

| Field | Details |
|---|---|
| **Repository** | [kiprotect/klaro](https://github.com/kiprotect/klaro) |
| **Stars** | ⭐ 1,467 |
| **Language** | JavaScript |
| **License** | BSD-3-Clause |
| **Last commit** | March 27, 2025 |
| **Open issues** | ~10 |

### Description

Klaro is a simple, open-source consent management platform (CMP) and privacy tool that helps websites be transparent about third-party applications. It is designed to be extremely lightweight (57 kB minified+gzipped), customizable, multilingual, and compliant with GDPR and ePrivacy. It works by replacing `src` attributes on third-party scripts with `data-src` so they only execute after user consent.

### Maintenance Activity

⚠️ **Moderate concern.** The last meaningful commits were a batch of PR merges on March 27, 2025. Before that, there were long gaps between updates. Community PRs are still being merged, but core maintainer engagement appears inconsistent. Issue #565 requests an npm release that includes an important fix but has received no response.

### Known Vulnerabilities & Security Concerns

| Issue | Severity | Description |
|---|---|---|
| [#564 — Race condition in GTM integration](https://github.com/kiprotect/klaro/issues/564) | ⚠️ Medium | The `onAccept` callback for the Google Tag Manager service may fire **before** consent updates (`ad_storage`, `analytics_storage`) are applied. This can cause Google Ads/Analytics tags to execute while consent is still in "denied" mode, resulting in non-compliant cookieless/denied-mode pings. This is a **consent integrity** issue that could lead to GDPR non-compliance. |
| [#565 — npm release not published with fix](https://github.com/kiprotect/klaro/issues/565) | ⚠️ Medium | A community fix (PR #508) has been merged but no new npm version has been published. Users installing from npm are running an outdated version that may contain unfixed bugs. |
| [#558 — Missing accessible name on dialog](https://github.com/kiprotect/klaro/issues/558) | 🔵 Low | The consent dialog lacks an accessible name, which is an accessibility (WCAG) issue rather than a direct security vulnerability. |

### Issue Tracker

🔗 [https://github.com/kiprotect/klaro/issues](https://github.com/kiprotect/klaro/issues)

---

## 2. Bearer — Security & Privacy SAST Scanner

| Field | Details |
|---|---|
| **Repository** | [Bearer/bearer](https://github.com/Bearer/bearer) |
| **Stars** | ⭐ 2,674 |
| **Language** | Go |
| **License** | Elastic License 2.0 (ELv2) |
| **Last commit** | June 2, 2026 |
| **Open issues** | ~11 |

### Description

Bearer is a static application security testing (SAST) tool that scans source code for security and privacy risks. It covers OWASP Top 10 and CWE Top 25 vulnerability patterns, and uniquely provides a **privacy scanner** that discovers and classifies sensitive data flows (PII, PHI) across 120+ data types. This makes it valuable for generating privacy reports, DPIAs, and RoPA inputs required for GDPR compliance.

### Maintenance Activity

✅ **Actively maintained.** Commits are frequent (multiple per week), with regular Dependabot dependency updates and active development. The project has a formal `SECURITY.md` policy for responsible disclosure and is part of the Cygives community.

### Known Vulnerabilities & Security Concerns

| Issue | Severity | Description |
|---|---|---|
| [#1922 — Dependency bump: gitleaks v8.18.1 → v8.30.1](https://github.com/Bearer/bearer/pull/1922) | ⚠️ Medium | An open Dependabot PR to bump gitleaks from v8.18.1 to v8.30.1 — this is a major version jump that likely includes CVE fixes. The PR has been open since March 2026 and is not yet merged, meaning Bearer's current release ships with an outdated gitleaks dependency. |
| [#1883 — False positives in hardcoded secret detection](https://github.com/Bearer/bearer/issues/1883) | 🔵 Low | The `java_lang_hardcoded_secret` rule triggers false positives by matching the substring "des" in common words like "Description." While not a direct vulnerability, false positives can lead to **alert fatigue**, causing real security findings to be overlooked. |

### Issue Tracker

🔗 [https://github.com/Bearer/bearer/issues](https://github.com/Bearer/bearer/issues)

---

## 3. IBM AI Privacy Toolkit

| Field | Details |
|---|---|
| **Repository** | [IBM/ai-privacy-toolkit](https://github.com/IBM/ai-privacy-toolkit) |
| **Stars** | ⭐ 114 |
| **Language** | Python |
| **License** | MIT |
| **Last commit** | July 3, 2024 |
| **Open issues** | ~12 |

### Description

IBM's AI Privacy Toolkit provides tools for anonymizing ML model training data (so retrained models can be considered anonymous under GDPR/CCPA), minimizing personal data used in predictions (adhering to the GDPR data minimization principle), and assessing the privacy risk of synthetic datasets. It is an academic/enterprise-grade toolkit with an OpenSSF Best Practices badge.

### Maintenance Activity

🔴 **Low activity.** The last commit was in July 2024 — nearly two years without updates. Most open issues are feature requests from 2021–2023 with no maintainer response. A Mend security scanning configuration PR (#98) has been open since September 2025 without being merged. This suggests the project may be in maintenance mode or de-prioritized.

### Known Vulnerabilities & Security Concerns

| Issue | Severity | Description |
|---|---|---|
| [#95 — Missing GDPR Article 9 compliance](https://github.com/IBM/ai-privacy-toolkit/issues/95) | 🔴 High | The anonymization module accepts **any feature names** as quasi-identifiers without screening for special categories of personal data (racial/ethnic origin, health data, biometric data, etc.) as required by GDPR Article 9. There are no validation checks, no sensitivity screening, and no detection of proxy variables that could reveal protected characteristics. This is a **compliance gap** that could expose organizations to legal risk. |
| [#98 — Mend security scanning PR unmerged](https://github.com/IBM/ai-privacy-toolkit/pull/98) | ⚠️ Medium | An automated PR to configure Mend (formerly WhiteSource) for continuous security scanning has been open since September 2025 without being merged. This means the project does not currently have automated dependency vulnerability detection in place. |

### Issue Tracker

🔗 [https://github.com/IBM/ai-privacy-toolkit/issues](https://github.com/IBM/ai-privacy-toolkit/issues)

---

## 4. FAZ Cookie Manager — WordPress Plugin

| Field | Details |
|---|---|
| **Repository** | [fabiodalez-dev/FAZ-Cookie-Manager](https://github.com/fabiodalez-dev/FAZ-Cookie-Manager) |
| **Stars** | ⭐ 111 |
| **Language** | PHP |
| **License** | GPL-3.0-or-later |
| **Last commit** | June 2, 2026 |
| **Open issues** | 1 |

### Description

FAZ Cookie Manager is a fully free, open-source WordPress cookie consent plugin with no cloud dependencies or premium paywalls. It supports GDPR, CCPA, LGPD, IAB TCF v2.3, Google Consent Mode v2, and includes a built-in browser-based cookie scanner, consent logging with CSV export, geo-targeting, 180+ languages, WCAG 2.1 AA accessibility, and a Cookie Policy generator. It is ideal for small businesses running WordPress who need a complete compliance solution without recurring fees.

### Maintenance Activity

✅ **Very actively maintained.** Multiple releases per month with detailed changelogs. The most recent release (v1.17.1) was on June 2, 2026. The project has comprehensive E2E test suites (Playwright), PHPStan static analysis, and CodeRabbit AI code review integration. Only 1 open issue.

### Known Vulnerabilities & Security Concerns

**No open security vulnerabilities found.** 🎉

The project has proactively addressed several security concerns in recent releases:

| Fix | Release | Description |
|---|---|---|
| TOCTOU window closed | v1.17.0 | Single-SELECT `scan_available` + id derivation closes a time-of-check-to-time-of-use race condition |
| SQL injection hardening | v1.17.0 | `$wpdb->esc_like()` added to `SHOW TABLES LIKE` probes |
| ReDoS prevention | v1.17.0 | ReDoS-free literal-glob cookie-name matcher replaces regex |
| Cross-origin consent forwarding | v1.17.0 | `event.origin` allow-list on cross-domain consent forwarding |
| Prototype pollution fix | v1.17.0 | Prototype-pollution-safe `deepGet`/`deepSet` dot-path helpers |
| Cache poisoning fixes | v1.14.3 | Transactional delete + update_item, cache-poisoning races closed |

The only open issue ([#125 — Cookie banner not saving](https://github.com/fabiodalez-dev/FAZ-Cookie-Manager/issues/125)) is a functional bug, not a security concern.

### Issue Tracker

🔗 [https://github.com/fabiodalez-dev/FAZ-Cookie-Manager/issues](https://github.com/fabiodalez-dev/FAZ-Cookie-Manager/issues)

---

## 5. PII Guard — LLM-Powered PII Detection

| Field | Details |
|---|---|
| **Repository** | [rpgeeganage/pii-guard](https://github.com/rpgeeganage/pii-guard) |
| **Stars** | ⭐ 105 |
| **Language** | TypeScript |
| **License** | Not specified |
| **Last commit** | November 1, 2025 |
| **Open issues** | 0 |

### Description

PII Guard is an LLM-powered tool that detects and manages Personally Identifiable Information in application logs. It uses the `gemma:3b` model running locally via Ollama to identify PII types including identity information, sensitive categories (GDPR Art. 9), government/financial identifiers, and network/device information. It includes a web dashboard, REST API, and integrations with PostgreSQL, Elasticsearch, and RabbitMQ.

### Maintenance Activity

⚠️ **Moderate.** Last commit was November 2025 (~7 months ago). The author notes this is a personal side project. No open issues exist, but this also means there has been no community security review or bug reporting.

### Known Vulnerabilities & Security Concerns

**No open issues reported.** However, there are **inherent security considerations** with this tool:

| Concern | Severity | Description |
|---|---|---|
| LLM data exposure | ⚠️ Medium | Log data containing PII is sent to a local LLM (Ollama/gemma:3b) for analysis. If the Ollama instance is misconfigured or exposed, sensitive data could leak. The project does not document hardening guidance for the Ollama runtime. |
| No license specified | ⚠️ Medium | The repository has a LICENSE file (0.5 KB) but GitHub does not recognize it. Without a clear open-source license, legal use in production is uncertain. |
| No security policy | 🔵 Low | No `SECURITY.md` or responsible disclosure process is documented. |

### Issue Tracker

🔗 [https://github.com/rpgeeganage/pii-guard/issues](https://github.com/rpgeeganage/pii-guard/issues)

---

## Summary & Recommendations

| Tool | Stars | Maintenance | Security Status | Best For |
|---|---|---|---|---|
| **Klaro** | 1,467 | ⚠️ Moderate | ⚠️ Race condition in GTM consent flow (#564) | Websites needing a lightweight, embeddable consent banner |
| **Bearer** | 2,674 | ✅ Active | ⚠️ Outdated gitleaks dependency (#1922) | Dev teams wanting SAST + privacy scanning in CI/CD |
| **IBM AI Privacy Toolkit** | 114 | 🔴 Low | 🔴 Missing Art. 9 compliance (#95) | ML/AI teams needing data anonymization (with caveats) |
| **FAZ Cookie Manager** | 111 | ✅ Very Active | ✅ Clean — proactive security hardening | WordPress small businesses needing full cookie consent |
| **PII Guard** | 105 | ⚠️ Moderate | ⚠️ Inherent LLM data exposure risk | Teams wanting AI-powered log PII detection |

### Key Takeaways for Small Businesses

1. **For WordPress sites:** FAZ Cookie Manager is the standout choice — fully free, actively maintained, no cloud dependencies, and has proactive security hardening.
2. **For custom websites:** Klaro is the most popular open-source consent manager, but monitor issue #564 (GTM race condition) before relying on it for Google Consent Mode v2 compliance.
3. **For developer teams:** Bearer provides excellent dual security + privacy scanning, but note the ELv2 license restricts providing it as a managed service.
4. **For ML/AI workloads:** IBM's toolkit has a critical compliance gap (Article 9) and low maintenance — evaluate carefully before relying on it.
5. **For log PII detection:** PII Guard is innovative but experimental — ensure your Ollama instance is properly secured and network-isolated.

---

## Monitoring This Watchlist

To stay updated on security developments for these tools, consider:

- **Starring the repositories** on GitHub to get notifications
- **Subscribing to issue labels** like `security`, `bug`, or `vulnerability` in each repo
- **Setting up GitHub Actions** that periodically query each repo's issues for security keywords
- **Watching Dependabot alerts** for repositories you depend on

---

*This watchlist was compiled from GitHub repository data, open issue analysis, and commit history review. It does not constitute legal advice. Consult a qualified legal professional for GDPR compliance guidance specific to your organization.*
