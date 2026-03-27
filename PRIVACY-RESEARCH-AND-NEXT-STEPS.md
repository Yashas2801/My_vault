# Vault Site Privacy Research and Next Steps

## Current Setup (What I found)
- This is a Quartz-based Obsidian vault site.
- It is currently deployed via GitHub Actions from branch `v4` to GitHub Pages.
- The site is public at `https://Yashas2801.github.io/My_vault/`.
- Relevant files:
  - `.github/workflows/deploy.yml`
  - `quartz.config.ts`
  - `content/WELCOME - HOW TO USE THIS SITE.md`

## Goal
Make the site private so only you can access it.

## Options Evaluated

### 1) Private hosting over Tailscale (Recommended)
Host the generated `public/` site on your own machine and expose it only through your Tailscale network.

Why this is best for your use case:
- Only devices/accounts in your tailnet can reach it.
- No public internet endpoint needed.
- Strong privacy and simple mental model: "if not on my tailnet, no access."

Tradeoffs:
- Your host machine must be online for access.
- Slightly more ops than GitHub Pages.

### 2) Cloudflare Access in front of hosted site
Put identity login (OTP/Google/GitHub) in front of the site.

Pros:
- Always-online hosting.
- Fine-grained access policies.

Tradeoffs:
- More setup complexity.
- Must avoid auth bypass via direct origin/public URL.

### 3) GitHub Pages + repository privacy changes
Helps source privacy but does not reliably satisfy strict "only I can see the website" for personal/project Pages.

Verdict:
- Not ideal for your strict privacy goal.

## Security Issue to Fix Immediately
- Your local git remote currently includes a GitHub token in the URL.
- Action items:
  1. Revoke that token in GitHub settings.
  2. Replace remote with SSH URL:
     ```bash
     git remote set-url origin git@github.com:Yashas2801/My_vault.git
     ```
  3. Use SSH key or GitHub credential manager instead of embedding token in URL.

## Recommended Path (Action Plan)

### Phase 1: Stop public exposure
1. Disable GitHub Pages for this repository (or remove deploy workflow trigger).
2. Optionally unpublish old site so `Yashas2801.github.io/My_vault` is not live.

### Phase 2: Set up private access with Tailscale
1. Install Tailscale on your host machine and your personal devices.
2. Build site:
   ```bash
   npx quartz build
   ```
3. Serve static files locally (example):
   ```bash
   npx serve public -l 8080
   ```
4. Restrict access via Tailscale:
   - Keep service bound to localhost if using Tailscale Funnel alternatives, or
   - Bind to Tailscale interface/IP only.
5. Access from your devices using the tailnet IP/hostname.

### Phase 3: Improve publishing safety
1. Keep `ignorePatterns` tight in `quartz.config.ts`.
2. Add `publish: true` workflow for notes you want visible (opt-in publishing model).
3. Create a pre-push checklist:
   - no secrets
   - no private folders exposed
   - test build before push

## Optional Hardening
- Use full-disk encryption on host.
- Keep firewall default deny except tailnet.
- Enable Tailscale ACLs for only your user.
- Disable analytics if you want minimum data exhaust.

## What to do next (short version)
1. Rotate leaked GitHub token now.
2. Unpublish/disable GitHub Pages.
3. I can then help you implement a private Tailscale-hosted workflow in this repo.
