# Boolean Studio Pro (BoolPro)

[![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero%20(Vanilla%20JS)-success.svg)](#architecture--engineering-principles)
[![Single File App](https://img.shields.io/badge/Delivery-Single%20.html%20File-blue.svg)](#quick-start)
[![Engines](https://img.shields.io/badge/Engines-6%20Precision%20Platforms-purple.svg)](#supported-sourcing-engines)
[![License: MIT](https://img.shields.io/badge/License-MIT-emerald.svg)](#license)

> **Deterministic, platform-specific Boolean string compiler tailored for Staff, Principal, and Executive Technical Talent Sourcing.**

BoolPro is a standalone, client-side web application designed to solve common search failures in technical recruitment—such as Google's 32-word ceiling, syntax collation mismatches, and over-constrained X-Ray zero-result traps. It translates complex requisition parameters into syntax-accurate search queries across 6 major technical sourcing channels in real time.

---

## Table of Contents

- [Core Capabilities](#core-capabilities)
- [Supported Sourcing Engines](#supported-sourcing-engines)
- [The Google X-Ray 2-Keyword Clamp](#the-google-x-ray-2-keyword-clamp)
- [Recruiter Operations Manual](#recruiter-operations-manual)
  - [1. Mode A: Structured Input Grid](#1-mode-a-structured-input-grid)
  - [2. Mode B: Heuristic Job Description Parser](#2-mode-b-heuristic-job-description-parser)
  - [3. Inline Syntax Rule Chips](#3-inline-syntax-rule-chips)
  - [4. Algorithmic Complexity Slider (1–5)](#4-algorithmic-complexity-slider-15)
  - [5. Advanced Query / Pro Mode Drawer](#5-advanced-query--pro-mode-drawer)
  - [6. Local Storage Template Management](#6-local-storage-template-management)
  - [7. Bulk Export System (CSV & TXT)](#7-bulk-export-system-csv--txt)
- [Architecture & Engineering Principles](#architecture--engineering-principles)
- [Quick Start](#quick-start)
- [License](#license)

---

## Core Capabilities

- **Zero-Dependency Single-File Utility:** Delivered entirely inside an offline-first, self-contained `index.html` file using Tailwind CSS CDN and vanilla ES6+.
- **Automated Anti-Dropout Clamp:** Clamps Google LinkedIn X-Ray queries to the top 2 mandatory keywords while allowing LinkedIn Native to run full multi-skill conjunctions.
- **Dynamic Platform Usage Callouts:** In-card muted usage guides showing recruiters exactly where to paste each string (e.g., search bars, Recruiter keyword fields, or user directory filters).
- **Hard Limit Safeguards:** Real-time character/word counting that warns when queries approach or breach platform-specific limits (Google's 32-word cap, LinkedIn's 1,200-character ceiling, and GitHub's 256-character qualifier limit).
- **Local Storage Requisition Templates:** Save, rename, load, and purge custom search profiles locally without external database overhead.
- **Linear-Inspired Zinc Theme:** Minimalist UI with accessible typography and a segmented `[ ☀ Light | ☾ Dark ]` toggle persisted in `localStorage`.

---

## Supported Sourcing Engines

| Engine | Core Target Scope | Syntax Dialect | Primary Use Case |
|---|---|---|---|
| **Google X-Ray (LinkedIn)** | `site:linkedin.com/in/` | Google Web Search | Discovering public member profiles without commercial search limit barriers. |
| **LinkedIn Native / Recruiter** | Full Profile Index | Standard Boolean (`AND`, `OR`, `NOT`) | Full-text candidate pipeline search in LinkedIn Recruiter or Recruiter Lite. |
| **GitHub Talent Search** | `type:user` | GitHub Qualifiers (`language:`, `location:`) | Sourcing open-source contributors, systems engineers, and active coders. |
| **Hugging Face Creators** | `site:huggingface.co` | Domain-Specific Google X-Ray | Pinpointing creators with published open-source models, spaces, or safetensors. |
| **Kaggle Profile X-Ray** | `site:kaggle.com` | Directory-Filtered Google X-Ray | Sourcing competitive ML specialists (Grandmasters, Masters, Competitions tier). |
| **Stack Overflow Users** | `site:stackoverflow.com/users/` | Directory-Filtered Google X-Ray | Surfacing high-reputation practitioners by language and domain expertise. |

---

## The Google X-Ray 2-Keyword Clamp

### The Problem
Google strictly interprets space-separated search tokens as rigid `AND` conjunctions. Because LinkedIn restricts how much profile body content crawlers can index without authentication, requiring 3 or more mandatory skills on Google X-Ray (`"Go" "Kubernetes" "Kafka" "gRPC"`) almost always causes searches to return **zero results**, even when thousands of qualified candidates exist.

### The BoolPro Solution
BoolPro decouples Google X-Ray from LinkedIn Native:
1. **Google X-Ray (Clamped):** Automatically clamps mandatory skills to the **first 2 primary keywords**, focusing on terms most likely to appear in public headlines and page titles.
2. **LinkedIn Native (Unclamped):** Preserves every mandatory skill (`AND "Go" AND "Kubernetes" AND "Kafka" AND "gRPC"`), leveraging LinkedIn's internal indexing of complete resumes, skill tags, and experience entries.
3. **Visual UI Badge:** Displays a visible `Clamped (Top 2)` indicator on the Google card whenever more than 2 mandatory keywords are configured.

---

## Recruiter Operations Manual

### 1. Mode A: Structured Input Grid

- **Seniority Checklist:** Quick toggles for `Staff`, `Principal`, `Lead`, and `Senior` that automatically prefix role titles.
- **Job Titles (OR):** Enter titles separated by commas or Enter (e.g., `Software Engineer`, `Backend Engineer`).
- **Mandatory Skills (AND):** Core technical competencies. The top 2 are passed to Google X-Ray; all are passed to LinkedIn Native.
- **Secondary / Variations (OR):** Tech stack alternates or nice-to-haves (e.g., `Distributed Systems`, `AWS`, `GCP`).
- **Locations / Affiliations:** Target geographic markets or remote hubs (e.g., `San Francisco`, `New York`, `Remote`).
- **Exclusions (NOT):** Negative keywords automatically formatted per platform (e.g., `Junior`, `Intern`, `Recruiter`).

### 2. Mode B: Heuristic Job Description Parser

Paste a raw Job Description or requisition draft into the expandable **Job Description Smart Parser** drawer and click **Extract Criteria**. The client-side parser uses regex heuristics against technical dictionaries to automatically populate:
- Seniority levels
- Target role titles
- Core and secondary technical skills
- Geographic locations
- Standard recruiter negative exclusions

### 3. Inline Syntax Rule Chips

Clickable syntax chips at the top of the workspace toggle compiler rules globally on the fly:
- **Force Exact Quotes:** Forces quotation marks around every token (`"Go"`), disabling stemming.
- **Parenthetical Nesting:** Toggles standard grouped nesting `(Title A OR Title B)`.
- **NOT / -negations:** Toggles whether negative exclusions are appended to generated strings.

### 4. Algorithmic Complexity Slider (1–5)

- **Level 1 (Broad Discovery):** Minimal quotes, single role titles, loose conjunctions.
- **Level 2/3 (Balanced Targeted - Default):** Quoting on multi-word phrases only, automated 2-keyword clamp for Google X-Ray, standard clustering.
- **Level 4 (Strict Precision):** Seniority permutations generated for every role title, strict quoting, full negative keywords enforced.
- **Level 5 (Max Exact Match):** Every keyword strictly quoted, full permutation expansion, strict conjunction enforcement.

### 5. Advanced Query / Pro Mode Drawer

Expand the **Advanced Query / Pro Mode** drawer for fine-grained engine tuning:
- **Hugging Face Scope:** Switch between Creator Profiles, Hybrid Authors (`models created`), or Open-Source Model Cards.
- **Kaggle Minimum Tier:** Filter specifically for `Grandmaster Only`, `Master Only`, or `Competitions Tier`.
- **Platform Overrides:** Configure LinkedIn Industry Codes (e.g., `4, 96` for Technology) or GitHub repository creation dates (`created:<2024-01-01`).
- **Engine Tuning:** Set GitHub primary languages (`language:go`) or minimum Stack Overflow reputation scores.

### 6. Local Storage Template Management

- **Save Current:** Click **Templates** > **+ Save Current** in the top bar to name and store the active search setup.
- **Instant Restore:** Select any saved template from the dropdown to restore all fields, slider levels, rule chips, and Pro Mode overrides.
- **Local Persistence:** Data is saved locally in the browser's `localStorage` (`sr_studio_custom_templates_6e`), requiring no accounts, tokens, or network requests.

### 7. Bulk Export System (CSV & TXT)

Click **Export** in the top navigation bar to generate downloads:
- **Download CSV (`.csv`):** Formatted tabular file including Platform Name, Target Endpoint, Word Count, Character Count, and the compiled search query.
- **Download Dossier (`.txt`):** Text summary formatted for engineering hiring briefs, requisition syncs, or team wikis.

---

## Architecture & Engineering Principles

```
┌────────────────────────────────────────────────────────┐
│                   BoolPro Core Runtime                 │
│                                                        │
│  ┌──────────────────────┐    ┌──────────────────────┐  │
│  │     UI View Layer    │    │   Templates Engine   │  │
│  │ Tailwind + Dark Mode │    │ localStorage Schema  │  │
│  └──────────▲───────────┘    └──────────▲───────────┘  │
│             │                           │              │
│  ┌──────────┴───────────────────────────┴───────────┐  │
│  │           State & Parsing Orchestrator           │  │
│  │                                                  │  │
│  │  - state: { titles, mandatory, optional... }     │  │
│  │  - Complexity Scaler (1 - 5)                     │  │
│  │  - Heuristic JD Tokenizer                        │  │
│  │  - Safe Token Formatter (Smart-Quote Normalizer) │  │
│  └──────────┬───────────────────────────┬───────────┘  │
│             │                           │              │
│  ┌──────────▼───────────┐    ┌──────────▼───────────┐  │
│  │   Google Clamping    │    │  Native Conjunction  │  │
│  │   2-Keyword Cap      │    │  Full Unclamped Set  │  │
│  └──────────┬───────────┘    └──────────┬───────────┘  │
│             │                           │              │
│  ┌──────────▼───────────────────────────▼───────────┐  │
│  │           6 Specialized Output Compilers         │  │
│  │   Google LinkedIn | LI Native | GitHub Search    │  │
│  │   Hugging Face    | Kaggle    | Stack Overflow   │  │
│  └──────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────┘
```

- **Smart Quote Neutralization:** Automated sanitizer replaces curly/smart quotes (`“...”`, `”...”`) with ASCII 34 straight double quotes (`"..."`) to prevent syntax errors in search engines.
- **Punctuation Collision Prevention:** Avoids quoting terms with symbols (like `C++` or `Node.js`) that break Google's token parser.
- **Zero Network Footprint:** Runs entirely inside the local browser context with no trackers, telemetry, or external API requirements.

---

## Quick Start

1. Clone or download the repository:
   ```bash
   git clone https://github.com/your-username/boolpro.git
   cd boolpro
   ```
2. Double-click `index.html` to open it in Chrome, Safari, Edge, or Firefox.
3. Add target roles, technical skills, and locations, or paste a Job Description into Mode B.
4. Click **Copy** on any of the 6 compiled cards and paste into the platform indicated in the card's usage tip.

---

## License

Distributed under the MIT License. See `LICENSE` for details.
