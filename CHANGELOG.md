# Changelog

All notable changes to this project will be documented in this file. This project follows a simple, tag-based changelog where each entry is associated with a Git tag (format: vMAJOR.MINOR.PATCH). Use the tag name as the release header and list the changes under it.

Format:
- YYYY-MM-DD — Tag: vX.Y.Z — Short title
  - Category: Description (files changed or important notes)

---

## [Unreleased]

- Pending: Add release notes here before creating the release/tag.

---

## v0.1.0 — 2025-09-29 — Initial site import and CI

- Site: Added core `index.html` with header, Bandcamp embeds renderer, and assets (images, fonts, favicons).
- Bandcamp: Replaced static iframe with `bandcampTracks` array and dynamic renderer; iframes include `loading="lazy"`.
- Header: Email icon positioned at the right and vertically centered; original logo styling preserved.
- GitHub: Created repository `dionisrom/dj-jovan` and pushed initial files and assets.
- CI/CD: Added GitHub Actions workflow `.github/workflows/ftp-sync.yml` to mirror repo to FTP on new tags and manual dispatch. The workflow excludes `.git`, `.github`, and `.gitignore` from upload.
- Docs: Added `README.md`, `.gitignore`, and this `CHANGELOG.md`.

---

## Release template

When creating a new release (tag), copy the `Unreleased` section and fill in the changes. Example:

## v0.1.1 — 2025-10-01 — Minor fixes

- Fix: Corrected footer spacing (files: `index.html`, `styles.css`).
- CI: Added dry-run option to FTP workflow (file: `.github/workflows/ftp-sync.yml`).

Notes:
- Use semantic versioning for tags where practical (MAJOR.MINOR.PATCH).
- Keep entries short and list files changed where helpful.
