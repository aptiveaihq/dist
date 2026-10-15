# AptiveAI `dist`

Public distribution host for **AptiveAI** release binaries, served by GitHub's CDN.

> **This repo holds release assets only — there is no source code here.**
> Everything is published automatically by CI from the private AptiveAI
> repositories. Do not open PRs against this repo.

## aptive-worker (Aptive AI Worker)

The app that connects a customer's own computer to AptiveAI Agents, published
from `aptiveaihq/worker-app`.

- **`aptive-worker-v<X.Y.Z>`** — an immutable per-version release holding the
  packages (`aptive-worker-<v>-<os>-<arch>.tar.gz`,
  `aptive-worker-<v>-windows-amd64.zip`), the one-file Windows installer
  (`aptive-worker-installer-windows-amd64.exe`), `SHA256SUMS`, and a
  `latest.json` manifest (version + per-platform URL + SHA-256).
- **`aptive-worker-latest`** — a mutable pointer release. It always carries the
  newest version's Windows installer, `SHA256SUMS` and `latest.json`, so these
  links never change:

  ```
  https://github.com/aptiveaihq/dist/releases/download/aptive-worker-latest/aptive-worker-installer-windows-amd64.exe
  https://github.com/aptiveaihq/dist/releases/download/aptive-worker-latest/latest.json
  ```

Each publish uploads the versioned release first and only then advances the
`aptive-worker-latest` pointer, with `latest.json` last, so the manifest never
references files that are not live yet. Check a download against the SHA-256
shown on the Computers page in AptiveAI Agents (a second source), not only
against `SHA256SUMS` beside it.
