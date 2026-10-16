# Downloads

Installers for my desktop print-production tools. Grab them from the
**[homepage](https://mylandurray.github.io/)** or from
**[Releases](https://github.com/mylandurray/downloads/releases)**.

This repo holds no source code: each tool is built in its own repo, and only
the finished installers are published here as GitHub Releases.

## Publishing a release

Tag each release `<tool-id>-v<version>` and attach the installer:

| Tool | Tool id | Example tag |
|---|---|---|
| KongCut | `kongcut` | `kongcut-v1.0.0` |
| Prepress Check | `prepress-check` | `prepress-check-v1.0.0` |
| ProofHub Bridge | `proofhub-bridge` | `proofhub-bridge-v1.0.0` |

```bash
gh release create prepress-check-v1.0.0 path/to/PrepressCheck-Setup.exe -R mylandurray/downloads --title "Prepress Check 1.0.0" --notes "What changed"
```

The homepage shows the newest release for each tool that isn't a draft or
pre-release, so publish as a pre-release to test a build without listing it.
The tool ids match the `DOWNLOADS` list in the homepage's `index.html`; add a
row here when you add a tool there.

On Windows, unsigned installers trigger a SmartScreen warning: click
**More info**, then **Run anyway**.
