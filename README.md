# ReadSwift to PaceRead Redirect

This repository redirects `readswift.techscript.ca` to `paceread.techscript.ca`
using GitHub Pages. Do not add any other content here.

## One-time manual setup

### 1. Push this folder to a new GitHub repo
- Go to github.com, create a new public repository named `readswift-redirect`
- Push the contents of this folder to the repo root on the `main` branch

### 2. Enable GitHub Pages
- Repo Settings > Pages
- Source: Deploy from branch > main > / (root) > Save
- Custom domain: enter `readswift.techscript.ca` and save

### 3. Add a DNS CNAME record
In your DNS provider for `techscript.ca`, add:

| Type  | Host       | Value                              | TTL  |
|-------|------------|------------------------------------|------|
| CNAME | readswift  | YOUR-GITHUB-USERNAME.github.io     | 3600 |

Replace YOUR-GITHUB-USERNAME with your actual GitHub username.

This is safe alongside the existing `paceread` CNAME pointing to the same
server. GitHub uses the CNAME file inside each repo to route correctly.

### 4. Enable HTTPS
Once the DNS checkmark turns green in Pages settings (up to 24 hours),
tick "Enforce HTTPS" and save.

## How it works
- readswift.techscript.ca hits this repo, instantly redirects to paceread.techscript.ca
- All old shared links continue to work
- The `link rel="canonical"` tag signals to search engines that the new URL is the
  authoritative version, helping transfer ranking credit (note: meta-refresh is not a
  server-side 301; canonical is the mechanism for SEO credit transfer here)
- Cost: zero