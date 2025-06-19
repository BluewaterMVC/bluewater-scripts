# 🌊 Bluewater Central Script Repository


**The canonical, versioned library of automation scripts and Git hooks for all Bluewater repositories.  
Ensures consistent standards, metadata management, and automated workflows across the entire Bluewater platform.**

---

![Framework](https://img.shields.io/badge/framework-Bluewater-lightblue?logo=dropbox&logoColor=white)
![Status](https://img.shields.io/badge/status-active-blue)
![Version](https://img.shields.io/badge/version-1.0-blue?logo=semantic-release&logoColor=white)

![Docs Available](https://img.shields.io/badge/docs-Available-brightgreen?logo=readthedocs&logoColor=white)
![License](https://img.shields.io/badge/license-CC--BY--4.0-blue?logo=open-source-initiative&logoColor=white)
![Multi-Lingual](https://img.shields.io/badge/i18n-multi--language-brightgreen?logo=googletranslate&logoColor=white)


<!-- Multi-language Translation Status with Images -->

**Translation Status:**

<img src="https://flagcdn.com/24x18/us.png" alt="US" width="24"/> <img src="https://img.shields.io/badge/lang-en--100%25-brightgreen" alt="English" />
<br>
<img src="https://flagcdn.com/24x18/fr.png" alt="FR" width="24"/> <img src="https://img.shields.io/badge/lang-fr--70%25-yellow" alt="Français" />
<br>
<img src="https://flagcdn.com/24x18/de.png" alt="DE" width="24"/> <img src="https://img.shields.io/badge/lang-de--30%25-orange" alt="Deutsch" />
<br>
<img src="https://flagcdn.com/24x18/es.png" alt="ES" width="24"/> <img src="https://img.shields.io/badge/lang-es--planned-lightgrey" alt="Español" />
<br>
<img src="https://flagcdn.com/24x18/ru.png" alt="RU" width="24"/> <img src="https://img.shields.io/badge/lang-ru--planned-lightgrey" alt="Русский" />

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](../../pulls)
[![Contributors](https://img.shields.io/github/contributors/bluewatermvc/bluewater-scripts?style=flat-square)](https://github.com/bluewatermvc/bluewater-scripts/graphs/contributors)
---

## Overview

`bluewater-scripts` is the central source of truth for all automation, enforcement, and quality assurance scripts used across the Bluewater ecosystem.  
This repository guarantees that every contributor and every repository—whether code or documentation—operates under the same rigorously defined standards for metadata, file formatting, linting, and compliance.

**By maintaining all critical automation logic here and integrating it as a submodule in other Bluewater projects, we enforce consistency, minimize technical debt, and accelerate onboarding for contributors worldwide.**

---

## Key Features

- **Canonical Git Hooks**
  - Pre-commit, commit-msg, and pre-push hooks for enforcing standards on every commit.
  - Automation for metadata updates (e.g., copyright, last updated).
  - Protection against common documentation and code quality issues.
- **Cross-Platform Support**
  - Scripts are written for both Unix (bash) and Windows (batch).
- **Strict Linting and Formatting**
  - Wrappers for `markdownlint`, `yamllint`, and other linters.
  - Configurable and extensible for project-specific requirements.
- **Docs Structure Enforcement**
  - Shared scripts for maintaining multi-language `/docs/{lang}/` directory trees and validating structure.
- **Centralized Maintenance**
  - One authoritative place for updates; propagate via submodules to all dependent repositories.
- **Transparency and Open Source**
  - All scripts are public, auditable, and designed to build trust in the Bluewater process.

---

## Repository Structure

```text
/
├── metadata-updater.sh      # Updates copyright, date, and legal headers.
├── markdown-lint.sh         # Runs markdownlint on staged/target files.
├── yaml-lint.sh             # Runs yamllint on staged/target files.
├── docs-structure-check.sh  # Enforces /docs/{lang}/ directory structure.
├── pre-commit               # Composite pre-commit hook; calls relevant scripts.
├── setup-hooks.sh           # Installs all supported hooks (Unix).
├── setup-hooks.bat          # Installs all supported hooks (Windows).
├── README.md                # This file.
└── ...                      # (Add more shared automation scripts here.)
````

*See inline comments and each script’s header for detailed usage.*

---

## Installation & Usage

### **As a Submodule (Recommended)**

In your target repository (`bluewater-framework`, `bluewater-docs`, etc.):

```bash
git submodule add https://github.com/bluewatermvc/bluewater-scripts.git .shared-scripts
git submodule update --init --recursive
```

Update your `.githooks/pre-commit` and other hooks to source or execute the shared scripts:

```bash
#!/bin/bash
set -e
$(git rev-parse --show-toplevel)/.shared-scripts/pre-commit
```

Or call specific utilities as needed.

**Always re-run `git submodule update --remote .shared-scripts` to fetch updates.**

### **Manual Usage**

All scripts are self-contained.
Refer to each script’s `--help` or top comment block for usage instructions.

---

## Integration with Bluewater Projects

* **bluewater-framework:**
  Enforces PHP, PHPDoc, Markdown, YAML, and docs structure standards.
  All metadata and lint logic sourced from this repository.
* **bluewater-docs:**
  Enforces documentation and metadata standards, multi-language doc structure, and contributor compliance.

*All Bluewater projects reference and update this repository as the single source of automation truth.*

---

## Contribution & Governance

We welcome contributions that improve cross-repository automation, reliability, or developer experience.

* **Read:**
  [CONTRIBUTING.md](../CONTRIBUTING.md) (in parent repo for process),
  [GOVERNANCE.md](../GOVERNANCE.md)
* **Fork and PR:**
  Please use descriptive commit messages and submit focused pull requests.
* **Testing:**
  All scripts must be cross-platform, robust, and well-documented.

---

## Security & Compliance

* Scripts are auditable and maintained under version control.
* Do **not** include secrets, credentials, or sensitive configuration.
* All logic is open to review and improvement by the Bluewater community.

---

## License

Distributed under the [Open Software License (OSL 3.0)](./LICENSE) or other OSI-approved license as specified.

---

## Acknowledgments

This repository is maintained by the Bluewater Core Team.
Inspired by leading open-source automation patterns and a commitment to project excellence.

---

*Last updated: {{DATE}}*
