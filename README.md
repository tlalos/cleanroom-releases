# CleanRoom — Releases

Public update channel for the **CleanRoom** desktop app.

- **`version.json`** — the update manifest the app reads on startup:
  ```json
  { "version": "1.0.0", "url": "<zip download URL>", "notes": "..." }
  ```
  When `version` here is higher than the running app's version, the app downloads the zip, installs it
  over itself (preserving the local `appsettings.json`), and relaunches into the new version.

- **Release zips** are attached as assets to each [GitHub Release](../../releases) (`CleanRoom-<version>.zip`),
  framework-dependent win-x64 builds. They never contain credentials — `appsettings.json` is excluded and an
  `appsettings.example.json` template is shipped instead.

## Cutting a new release

From the app repo, run:

```powershell
.\publish-release.ps1 -Version 1.0.1 -Notes "What changed"
```

This builds, strips secrets, attaches the zip to a new GitHub Release here, and updates `version.json`.
