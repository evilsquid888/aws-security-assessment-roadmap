# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- **Phase 6 — AI-Driven AppSec & AWS Security Agent** subsection covering AWS's AI-driven design review, code review, and on-demand pen testing service (GA March 2026). Frames the assessor's role around safe scoping and documenting the compliance gap (AWS's own statement that it is "not a professional penetration testing service" and does not satisfy PCI-DSS or SOC 2 manual pen test requirements). Includes links to the AWS Security Agent User Guide, Security Considerations, GA announcement, and the multi-agent architecture deep dive.

## [1.0.0] - 2026-03-05

### Added
- Initial release of the AWS Security Assessment Roadmap
- **README.md** — Full markdown roadmap covering 6 phases (Foundations through Advanced & Specialization)
- **index.html** — Interactive single-page HTML app (serves as GitHub Pages site) with:
  - Expandable phase sections with per-topic checkboxes
  - Overall and per-phase progress tracking via localStorage
  - Tabbed navigation: Roadmap, Weekly Habits, Labs, Certifications
  - Weekly habit tracker with auto-reset each week
  - Responsive dark-themed UI (JetBrains Mono / IBM Plex Sans)
- 6 learning phases spanning 30+ weeks:
  - Phase 1: Foundations (Weeks 1-4) — AWS core services, shared responsibility, CLI/SDK, networking
  - Phase 2: IAM & Access Control (Weeks 5-8) — policy language, privilege escalation, cross-account access
  - Phase 3: Assessment Tooling (Weeks 9-13) — Prowler, Pacu, ScoutSuite, CloudFox, OSINT tools
  - Phase 4: Attack Techniques (Weeks 14-19) — initial access, lateral movement, persistence, exfiltration
  - Phase 5: Compliance & Frameworks (Weeks 20-23) — CIS benchmarks, SOC 2, PCI-DSS, report writing
  - Phase 6: Advanced & Specialization (Weeks 24-30+) — container/serverless, IaC review, IR, multi-account
- Curated links to 60+ tools, documentation pages, and learning resources
- Hands-on lab recommendations (CloudGoat, Flaws.cloud, TryHackMe, etc.)
- Certification path (Cloud Practitioner through OSCP/OSWE)
- Suggested weekly study habit schedule (Monday-Sunday)
