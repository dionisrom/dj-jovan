# DJ Yovan — Official website

Static site with Bandcamp embeds. This repository contains the site source (HTML/CSS/JS) and assets.

Preview

- Open `index.html` in a browser to preview locally.

Development notes

- Bandcamp embeds are defined in the `bandcampTracks` array inside `index.html` and are rendered dynamically by the included script.
- To add a new track, add an object with { iframeTitle, playerSource, songUrl, songName } to the array or call `addBandcampTrack(...)` in the browser console.

License

This repository contains assets and code provided by the project owner.

Deployment / GitHub Actions

This repository includes a GitHub Actions workflow at `.github/workflows/ftp-sync.yml` that will sync new, changed, and removed files to an FTP server when you push to `main` or trigger the workflow manually.

Secrets required (create these in the repository Settings → Secrets → Actions):
- `FTP_HOST` — your FTP server host (example: ftp.example.com)
- `FTP_PORT` — optional FTP port (leave blank for default 21)
- `FTP_USERNAME` — FTP username
- `FTP_PASSWORD` — FTP password
- `FTP_REMOTE_DIR` — remote directory on the FTP server where files should be mirrored (example: /public_html)

Add secrets using the GitHub UI or GitHub CLI. Example using GitHub CLI:

```powershell
gh secret set FTP_HOST --body "ftp.example.com"
gh secret set FTP_PORT --body "21"
gh secret set FTP_USERNAME --body "ftp-user"
gh secret set FTP_PASSWORD --body "super-secret-password"
gh secret set FTP_REMOTE_DIR --body "/public_html"
```

How it works

- The action uses `lftp` and the `mirror -R --delete` command to mirror the repository root to the configured remote directory.
- It uploads only new/changed files and deletes remote files that are absent locally.
- The workflow excludes `.git` and `.github` folders by pattern.

Notes and safety

- Keep your FTP credentials secret — do not store them in code.
- Test the action on a staging area or with a test remote directory before deploying to production.

