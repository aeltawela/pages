# Pages

The primary GitHub Pages repository used by the [Upload to Pages skill](https://github.com/aeltawela/upload-to-pages). Shared files are published under site/shares/<UUID>/; the root page does not list share links.

## Important

- This repository and its GitHub Pages site are public. Do not upload sensitive, confidential, or identifying information.
- A random URL is unlisted, not private. Anyone who receives or discovers the URL can open it.
- StatiCrypt encrypts HTML only. Linked CSV, PDF, image, and other assets stay public.
- Password-protected pages need a working HTTPS URL and certificate for browser decryption.
- Expiry is delayed cleanup by a daily GitHub Actions job. It is not immediate revocation and cannot remove downloads, caches, or Git history.

## Pages setup

The repository is configured to publish through GitHub Actions. The workflow in .github/workflows/pages.yml runs on pushes to the default branch, on a daily schedule, and manually. It removes folders whose expiry.json date has passed, commits those deletions, and deploys the site.

The expiry helper is scripts/expire_pages.py. Each expiring share stores metadata beside its page:

    {"expires_on":"YYYY-MM-DD","timezone":"Area/Location"}

The expiry date lasts through the end of that local date. Add a visible “Available until YYYY-MM-DD (TIMEZONE)” notice to pages that expire.

## Layout

- site/index.html — neutral landing page; does not enumerate shares.
- site/shares/<UUID>/ — one share per random UUID directory.
- scripts/expire_pages.py — standard-library cleanup helper.
- .github/workflows/pages.yml — scheduled cleanup and GitHub Pages deployment.

The source skill, install commands, and safety instructions live in [aeltawela/upload-to-pages](https://github.com/aeltawela/upload-to-pages).
