# Gemini Configuration Log - Obsidian Vault

This file tracks architectural changes and specific configuration overrides made by Gemini CLI.

## 🚀 Quartz 4 Deployment & Hosting (New)

### Configuration Details
- **Quartz Directory**: `~/Documents/my-vault-site`
- **GitHub Repository**: [Yashas2801/My_vault](https://github.com/Yashas2801/My_vault)
- **Live URL**: [https://Yashas2801.github.io/My_vault](https://Yashas2801.github.io/My_vault)
- **Hosting Method**: GitHub Pages (via GitHub Actions)
- **Deployment Branch**: `v4`

### Synchronization Workflow
To reflect changes made in Obsidian on the live website:
1.  **Edit in Obsidian**: Files in `~/Documents/Obsidian Vault` are synced to `~/Documents/my-vault-site/content` (likely via Syncthing).
2.  **Navigate to Quartz directory**:
    ```bash
    cd ~/Documents/my-vault-site
    ```
3.  **Git Add & Commit**:
    ```bash
    git add .
    git commit -m "Update notes: [brief description]"
    ```
4.  **Push to GitHub**:
    ```bash
    git push origin v4
    ```
5.  **Wait for Deployment**: The GitHub Action will automatically build and deploy the site (takes ~1-2 minutes).

### Troubleshooting & Fixes
- **Frontmatter Syntax**: Quartz requires valid YAML between `---` separators. If a file starts with `---` but contains non-YAML text (like raw dates or `#tags` without keys), the build will fail.
- **2026-03-06 Fix**: Removed malformed `---` separators from `Zettelkasten.md` files to prevent Quartz build crashes.
- **Backup Policy**: Before Gemini CLI modifies any vault notes, a `.bak` copy is created in the same directory.

---

## Indentation Guides Configuration

### Core Settings (`.obsidian/app.json`)
- **Toggle**: `showIndentGuide`
- **Current State**: `false` (Disabled)
- **How to Change**: **Settings > Editor > Indentation guides**.

### CSS Overrides (`.obsidian/snippets/hide-indent-guides.css`)
To provide a "hard" disable (useful when plugins or themes ignore the core setting), a CSS snippet was created:
- **Snippet Name**: `hide-indent-guides`
- **Current State**: **Enabled** in `.obsidian/appearance.json`.
- **Targets**:
    - Core Obsidian (`.cm-indent-guide`, etc.)
    - **Outliner** plugin (`.outliner-plugin-list-line`)
    - **Unitade/Monaco** editor (`.monaco-editor`, etc.)
- **How to Disable**: **Settings > Appearance > CSS snippets** (Toggle off `hide-indent-guides`).
### Plugin Investigations
The following plugins were identified as potentially affecting indentation guides:
- `obsidian-outliner`: Uses custom list lines.
- `unitade`: Integrates Monaco editor components which have their own guide system.
- `obsidian-style-settings`: Manages theme-specific variables.

---

## Vault Architecture & Observations

### Directory Purpose
- **`Atomix/`**: The core of the vault. Contains **Permanent/Atomic Notes**—granular, self-contained concepts (primarily VLSI, DDR, UVM, and SystemVerilog). These notes are rewritten in the user's own words and serve as the building blocks for the entire system.
- **`Literature notes/`**: Structured notes containing synthesized knowledge consumed from specific sources (books, courses, videos). These notes (like `DDR fundamentals.md`) provide a comprehensive narrative or structured summary of a topic, linking to the relevant atomic notes in `Atomix/`.
- **`Indexes/`**: High-level entry points for broad domains (e.g., `systemverilog.md`). They provide a starting point for navigation, pointing to key Literature Notes or specific Permanent Notes.
- **`Template/`**: Standardized formats for new content.
    - `Main Note.md`: Basic structure with timestamp, status, and tags.
    - `VLSI Templete.md`: A robust, sectioned template for technical VLSI deep-dives (Summary, Key Concepts, Insights, Applications, etc.).
- **`Rough Notes/`**: Transient data, logs, and trackers (e.g., `Workout tracker.md`, `Idea Tracker.md`).
- **`Unsorted/`**: Repository for attachments (images) and notes awaiting classification.
- **`Source Matirial/`**: Placeholder for raw inputs and references before they are distilled into the vault.

### Note Conventions (Atomix)
- **Standard Header**: Most notes follow the `Main Note.md` pattern:
  ```markdown
  YYYY-MM-DD HH:MM
  Status: #done / #todo
  Tags: #topic1 #topic2
  ```
- **Structure**: Technical notes often use tables for comparisons (e.g., TLM Ports, Latency vs Bandwidth) and numbered lists for sequences of operation (e.g., DRAM ACTIVATE).
- **Linking**: Heavy use of internal wikilinks (`[[Note Name]]`) to connect concepts across directories, especially from `Literature notes/` back to `Atomix/`.

---
*Last updated: 2026-03-06*
---
