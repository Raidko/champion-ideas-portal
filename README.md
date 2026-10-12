# CHAMPION Ideas Portal

Public static shell for the CHAMPION idea workbench. Idea contents are **not stored in plaintext** in this repository.

## Security model

- Idea cards are encrypted in the browser with AES-256-GCM.
- The vault key is never committed to GitHub and is not required by GitHub Actions.
- `data/index.json` exposes only idea IDs needed to discover encrypted cards.
- Saving creates a normal GitHub Issue containing only ciphertext. The workflow accepts sync requests only from the repository owner (`Raidko`), commits the encrypted payload, and closes the service issue.
- No GitHub personal access token is entered into the portal.

## GitHub Pages

Publish from `main` / `/ (root)`. The site URL is expected to be:

`https://raidko.github.io/champion-ideas-portal/`

## Local files

- `index.html` — application shell.
- `styles.css` — visual system.
- `app.js` — filtering, scoring, local encryption/decryption and sync flow.
- `data/index.json` — public list of encrypted-card IDs only.
- `data/ideas/*.enc.json` — AES-GCM encrypted idea cards.
- `.github/workflows/idea-sync.yml` — owner-only encrypted update ingestion.
