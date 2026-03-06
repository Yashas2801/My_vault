# Gemini Configuration Log - Obsidian Vault

This file tracks architectural changes and specific configuration overrides made by Gemini CLI.

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
