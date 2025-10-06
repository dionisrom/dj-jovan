# Changelog

All notable changes to this project will be documented in this file. This project follows a simple, tag-based changelog where each entry is associated with a Git tag (format: vMAJOR.MINOR.PATCH). Use the tag name as the release header and list the changes under it. 
Always the latest changes are on top, so the version history is in reverse chronological order.

Format:
## vX.Y.Z — YYYY-MM-DD — Short title
  - Category: Description (files changed or important notes)

---

## v0.1.3 — 2025-10-05 — Fixed mobile layout issues and made the header sticky

- UI: Wrapped the logo in a dedicated sticky header, tweaked the footer social icons, and tightened container widths to remove accidental horizontal scrolling on mobile without altering layout visuals. (file: `index.html`)

---

## v0.1.2 — 2025-09-30 — Recovered the logo and the banner images

- Site: Recovered the (file: `assets/dj-yovan-logo.jpg`) and (file: `assets/dj-yovan-logo.jpg`) image files. they got corrupted at one point.

---

## v0.1.1 — 2025-09-29 — Use SFTP for deployment and add diagnostics

- CI: Reworked deployment workflow to use SFTP on port 22. Added a pre-sync connectivity check, timeouts, retries and verbose tracing to the lftp command so deployment fails fast and provides useful diagnostics when auth/TLS/network issues occur. (file: `.github/workflows/ftp-sync.yml`)
- Fix: Corrected footer spacing (files: `index.html`, `styles.css`).
- CI: Added dry-run option to FTP workflow (file: `.github/workflows/ftp-sync.yml`).

Notes:
- Use semantic versioning for tags where practical (MAJOR.MINOR.PATCH).
- Keep entries short and list files changed where helpful.

---

## v0.1.0 — 2025-09-29 — Initial site import and CI

- Site: Added core `index.html` with header, Bandcamp embeds renderer, and assets (images, fonts, favicons).
- Bandcamp: Replaced static iframe with `bandcampTracks` array and dynamic renderer; iframes include `loading="lazy"`.
- Header: Email icon positioned at the right and vertically centered; original logo styling preserved.
- GitHub: Created repository `dionisrom/dj-jovan` and pushed initial files and assets.
- CI/CD: Added GitHub Actions workflow `.github/workflows/ftp-sync.yml` to mirror repo to FTP on new tags and manual dispatch. The workflow excludes `.git`, `.github`, and `.gitignore` from upload.
- Docs: Added `README.md`, `.gitignore`, and this `CHANGELOG.md`.
