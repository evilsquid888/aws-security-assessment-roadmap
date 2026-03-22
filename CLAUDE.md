# CLAUDE.md

## Project Overview

AWS Security Assessment Roadmap is an educational resource that provides a structured 30+ week learning path for becoming proficient in AWS security assessments. It targets pentesters, auditors, and security engineers. The project consists of a Markdown reference document (`README.md`) and a standalone interactive single-page HTML application (`index.html`) that can be hosted via GitHub Pages.

## Repository Structure

```
.
├── README.md        # Full roadmap in Markdown (6 phases, labs, certs)
├── index.html       # Interactive single-page app (dark-themed, localStorage progress tracking)
├── CHANGELOG.md     # Release history (Keep a Changelog format)
└── CLAUDE.md        # This file
```

There is no build step, backend, or package manager. The project is purely static content.

## Running Locally

Open `index.html` directly in a browser:

```sh
# macOS
open index.html

# Linux
xdg-open index.html

# or serve it
python3 -m http.server 8000
# then visit http://localhost:8000
```

No dependencies need to be installed. External fonts (JetBrains Mono, IBM Plex Sans) are loaded from Google Fonts CDN at runtime.

## Testing

There are no automated tests. Manual verification involves:

- Opening `index.html` and confirming all six phases expand/collapse correctly.
- Verifying checkbox state persists across page reloads (uses `localStorage`).
- Checking that all external links in both `README.md` and `index.html` resolve.
- Confirming the responsive layout renders properly on mobile viewports.

## Architecture & Key Details

- **index.html** is a fully self-contained single-page application: HTML + CSS + JavaScript in one file (~43 KB). No framework is used.
  - UI: Dark theme with CSS custom properties defined in `:root`.
  - Fonts: `JetBrains Mono` (headings/code) and `IBM Plex Sans` (body text).
  - State: Per-topic completion checkboxes and weekly habit tracker are persisted in `localStorage`.
  - Tabs: Roadmap, Weekly Habits, Labs, Certifications — controlled via vanilla JS.
  - Progress: Overall and per-phase progress bars update dynamically.

- **README.md** mirrors the same six-phase structure as the interactive app, with curated links to 60+ tools, documentation pages, and learning resources.

- **Content is organized into 6 phases:**
  1. Foundations (Weeks 1-4)
  2. IAM & Access Control (Weeks 5-8)
  3. Assessment Tooling (Weeks 9-13)
  4. Attack Techniques (Weeks 14-19)
  5. Compliance & Frameworks (Weeks 20-23)
  6. Advanced & Specialization (Weeks 24-30+)

## Coding Conventions

- The project uses no build tools, linters, or formatters.
- `index.html` follows a structure of: `<style>` block, then semantic HTML, then a `<script>` block at the end.
- CSS uses custom properties (variables) defined in `:root` for consistent theming.
- JavaScript is vanilla ES6+ with no external dependencies.
- Markdown follows standard GitHub-Flavored Markdown conventions with emoji usage for visual categorization of links (e.g., book emoji for docs, gear emoji for tools).
- Changelog follows the [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) format.

## Contributing

PRs are welcome for fixing broken links, adding resources, or improving lab recommendations. The project is MIT-licensed.
