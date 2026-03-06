# 🌿 Your Digital Garden: A Beginner's Guide

Welcome! This file explains how your new personal website works and how you can manage it using Obsidian and GitHub.

---

## 🏗️ How the Setup Works

Your notes and the website code live together in one place: `~/Documents/my-vault-site`.
1.  **Editor:** Use Obsidian to open the `content` folder inside that directory.
2.  **Engine:** Quartz (in the root folder) turns those notes into a website.
3.  **Sync/Host:** GitHub stores your notes and hosts the site at:
    👉 **[https://Yashas2801.github.io/My_vault/](https://Yashas2801.github.io/My_vault/)**

---

## 🚀 How to Publish Your Changes

When you finish writing in Obsidian, follow these steps to update the web:

1.  **Open Terminal** and go to the site folder:
    ```bash
    cd ~/Documents/my-vault-site
    ```
2.  **Send to GitHub**:
    ```bash
    git add .
    git commit -m "Update my notes"
    git push origin v4
    ```

---

## 💻 Working on a Different Computer

Because your notes are on GitHub, you can easily work on them from any PC.

### 1. Initial Setup (First time on a new PC)
1.  **Clone the Repo**:
    ```bash
    cd ~/Documents
    git clone https://github.com/Yashas2801/My_vault.git my-vault-site
    ```
2.  **Open in Obsidian**: Open the folder `~/Documents/my-vault-site/content` as a new vault.

### 2. Daily Syncing (The "Pull/Push" Workflow)
Before you start writing on a different PC, always **Pull** the latest changes:
```bash
cd ~/Documents/my-vault-site
git pull origin v4
```

After you finish writing, **Push** your changes:
```bash
git add .
git commit -m "Work from my other PC"
git push origin v4
```

---

## ⚠️ Important Rules for Success

### 1. The "Top of the File" Rule
Avoid starting a file with `---` unless you are writing proper YAML (e.g., `title: My Note`). Plain text or `#tags` inside `---` will break the website build.

### 2. Private Notes
Folders named `private` or `Template` are ignored by the website and won't be published.

---

## 🛠️ Need Help?
*   **Track Progress:** Watch your site build in the **[Actions tab](https://github.com/Yashas2801/My_vault/actions)**.
*   **Technical Logs:** See `GEMINI.md` for a history of AI-made changes.

Happy Gardening! 🪴
