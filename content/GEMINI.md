# Gemini Configuration Log - Obsidian Vault

This file tracks architectural changes and specific configuration overrides made by Gemini CLI.

## 🚀 Quartz 4 Deployment & Hosting (Final Working Setup)

### Architecture
- **Unified Vault**: The Obsidian Vault and the Quartz Content folder are now the same directory.
- **Active Path**: `/home/yash/Documents/my-vault-site/content`
- **Why?**: Symlinks are not natively supported by GitHub Actions/Pages. Moving the actual files directly into the repository ensures they are visible to the build engine.

### Configuration Details
- **GitHub Repository**: [Yashas2801/My_vault](https://github.com/Yashas2801/My_vault)
- **Live URL**: [https://Yashas2801.github.io/My_vault](https://Yashas2801.github.io/My_vault)
- **Base URL (Config)**: `Yashas2801.github.io/My_vault`
- **Hosting Method**: GitHub Pages (via GitHub Actions)
- **Deployment Branch**: `v4`

### Synchronization Workflow
1.  **Open Obsidian**: Open the folder `/home/yash/Documents/my-vault-site/content` as your vault.
2.  **Edit**: Write notes as usual.
3.  **Publish**:
    ```bash
    cd ~/Documents/my-vault-site
    git add .
    git commit -m "Update notes: [brief description]"
    git push origin v4
    ```

### Troubleshooting & Fixes
- **Frontmatter Syntax**: Quartz requires valid YAML between `---` separators. Avoid raw dates or `#tags` at the start of a note if they are inside `---`.
- **XML/RSS Redirect Issue**: Fixed by ensuring physical files are present (removing symlinks) and correcting the `baseUrl` in `quartz.config.ts`.
- **2026-03-06 Fixes**: 
    - Moved notes from original vault to site repository.
    - Updated `quartz.config.ts` ignore patterns (ignoring `.obsidian`, `.trash`, etc.).
    - Created `WELCOME - HOW TO USE THIS SITE.md` and `index.md`.

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

---

## Vault Architecture & Observations

### Directory Purpose
- **`Atomix/`**: The core of the vault. Contains **Permanent/Atomic Notes** (VLSI, DDR, UVM, SystemVerilog).
- **`Literature notes/`**: Synthesized knowledge from specific sources.
- **`Indexes/`**: Domain entry points.
- **`Rough Notes/`**: Transient data and logs.
- **`Unsorted/`**: Repository for attachments and unclassified notes.

### Note Conventions (Atomix)
- **Standard Header**: 
  ```markdown
  YYYY-MM-DD HH:MM
  Status: #done / #todo
  Tags: #topic1 #topic2
  ```
- **Linking**: Wikis (`[[Note Name]]`) are used heavily to connect concepts.

---
*Last updated: 2026-03-06*
---
