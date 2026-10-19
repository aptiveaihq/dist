# AptiveAI `dist`

Public distribution host for **AptiveAI** release binaries, served by GitHub's CDN.

> **This repo holds release assets only. There is no source code here.**
> Everything is published automatically by CI from the private AptiveAI
> repositories. Do not open PRs against this repo.

## aptiveai-worker (AptiveAI Worker)

The app that connects a customer's own computer to AptiveAI Agents, published
from `aptiveaihq/worker-app`.

- **`aptiveai-worker-v<X.Y.Z>`**: an immutable per-version release with:
  - the packages (`aptiveai-worker-<v>-<os>-<arch>.tar.gz` and
    `aptiveai-worker-<v>-windows-amd64.zip`);
  - the one-file Windows installer (`aptiveai-worker-installer-windows-amd64.exe`);
  - `SHA256SUMS`;
  - a `latest.json` manifest (the version, plus each platform's URL and SHA-256).
- **`aptiveai-worker-latest`**: a mutable pointer to the newest **stable**
  version. It always carries that version's Windows installer, `SHA256SUMS` and
  `latest.json`, so these links never change:

  ```
  https://github.com/aptiveaihq/dist/releases/download/aptiveai-worker-latest/aptiveai-worker-installer-windows-amd64.exe
  https://github.com/aptiveaihq/dist/releases/download/aptiveai-worker-latest/latest.json
  ```

- **`aptiveai-worker-next`**: the same, for the newest prerelease (a release
  candidate). Use it only when asked to test one.

Each publish uploads the versioned release first and only then advances the
pointer, writing `latest.json` last, so the manifest never references files
that are not live yet.

To check a download, compare its SHA-256 with the `.sha256` file published
beside it (or its line in `SHA256SUMS`):

```powershell
Get-FileHash .\aptiveai-worker-installer-windows-amd64.exe -Algorithm SHA256
```

```sh
shasum -a 256 aptiveai-worker-*.tar.gz
```

The older `aptive-worker-*` releases (0.2.x) were removed when the app was
renamed to AptiveAI Worker in 0.3.0. An installer from them can no longer
connect to AptiveAI.
