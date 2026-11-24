# CLAUDE.md

Guidance for Claude Code in this repo.

## What this is

A public repo with **no source code**. Its GitHub Releases hold the finished
installers for Dylan's desktop tools, and the homepage
(`mylandurray.github.io`, source in the `github-pages-home` repo) reads them
through the unauthenticated releases API to draw its Download buttons.
README.md has the publishing steps for people.

## How releases get here

- **KongCut** and **Prepress Check** publish themselves. In the tool's private
  repo, a pushed `v<version>` tag runs `.github/workflows/release.yml`: it
  creates a **draft** release here, each build job (Windows, Mac Apple silicon,
  Mac Intel) uploads its file straight into it, and a final job publishes the
  draft. A **Run workflow** test build leaves a draft named
  `<tool-id>-v<version>-test-<run>`; delete it when done. Those repos need the
  `DOWNLOADS_TOKEN` secret (fine-grained, Contents read/write on this repo only).
- Anything else is published by hand with `gh release create` (README.md).
- **ProofHub/Printlogic Bridge must not be published here**: its installers
  contain a Zoho client secret. `proofhub-bridge-v2.5.0` was pulled on
  2026-11-24 and kept as a hidden draft so its files survive; don't republish it.

## Conventions the homepage relies on

- Tag `<tool-id>-v<version>`; `<tool-id>` matches an `id` in the homepage's
  `DOWNLOADS` array (`index.html`). The newest non-draft, non-prerelease per
  tool is shown.
- Mac files contain `-mac-apple-silicon` or `-mac-intel` (or `arm64`/`x64`);
  any `.exe`/`.msi`/`.zip` without "mac" is the Windows download.
- Release assets in a public repo don't count toward Actions storage. Don't
  route builds through Actions artifacts — the account's 500 MB artifact quota
  ran out once (2026-11) from 90-day-retained builds.
