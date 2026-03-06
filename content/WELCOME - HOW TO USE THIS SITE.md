# 🌿 Your Digital Garden: A Beginner's Guide

Welcome! This file explains how your new personal website works and how you can manage it using Obsidian and GitHub.

---

## 🏗️ How the Setup Works

Think of your setup in three parts:

1.  **The Editor (Obsidian):** This is where you write your notes. Everything you do here is private and lives on your computer in the `Obsidian Vault` folder.
2.  **The Engine (Quartz):** This is a tool located in `~/Documents/my-vault-site`. It takes your Obsidian notes and turns them into a beautiful, searchable website.
3.  **The Host (GitHub):** When you "Push" your code to GitHub, a "GitHub Action" automatically starts. It builds your site and hosts it for the world to see at:
    👉 **[https://Yashas2801.github.io/My_vault/](https://Yashas2801.github.io/My_vault/)**

---

## 🚀 How to Publish Your Changes

When you finish writing a new note or editing an old one in Obsidian, follow these **three simple steps** to see it on the web:

### 1. Open your Terminal
You can use any terminal (like `kitty` or `zsh`).

### 2. Navigate to your Site folder
Type this command and press Enter:
```bash
cd ~/Documents/my-vault-site
```

### 3. Send changes to GitHub
Run these three commands in order (you can copy-paste them):
```bash
git add .
git commit -m "Updated my notes"
git push origin v4
```

**That's it!** In about 2 minutes, your website will update automatically.

---

## ⚠️ Important Rules for Success

To keep the "Engine" (Quartz) running smoothly, keep these two tips in mind:

### 1. The "Top of the File" Rule
If you use `---` at the very top of a note, Quartz thinks you are writing "Technical Settings" (Frontmatter). 
*   **Safe:** Just start typing your note or a title like `# My Note`.
*   **Risky:** Starting a file with `---` without using proper "Key: Value" pairs (like `title: My Note`). 
*   *Note: If a build fails, it's usually because of a stray `---` at the top of a file.*

### 2. Private Notes
If you have a note you **don't** want the world to see, you can add `draft: true` to the top of the file, or simply don't push it to GitHub.

---

## 🛠️ Need Help?
*   **Track Progress:** You can watch your site building in the **[Actions tab of your GitHub Repo](https://github.com/Yashas2801/My_vault/actions)**.
*   **Gemini Log:** Check the `GEMINI.md` file in this vault to see technical logs of changes made by the AI.

Happy Gardening! 🪴
