# CodexCompanion Windows x64 preview 1.2.0

Download:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.0/CodexCompanion-Windows-x64-preview-1.2.0.zip

SHA-256:

`9d138d95c0bf92155889b5e74bbe73b58c21eb3c29d45a25e90e3c57040f3eda`

This is a Windows preview build. It is not code-signed yet. This build writes diagnostics to `%APPDATA%\CodexCompanion\logs\codex-companion.log`, includes the refreshed glass/anime management window, uses the bundled anime fallback when no AMII library is installed, ignores the legacy `sample-smoke` test asset, and avoids watching its own management window.

## Run

1. Extract the ZIP.
2. Open the extracted `publish` folder.
3. Run `CodexCompanion.exe`.

## Smoke test

From PowerShell in the extracted `publish` folder:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\SmokeTest-CodexCompanion.ps1 -PublishPath .
```

The helper verifies the executable, starts the app, and prints PASS/WARN/FAIL evidence. It no longer seeds fake content by default.

After launch, open the tray menu and choose **Open Companion**. Use the management window’s **Next Reaction** button to verify the bundled anime fallback overlay or any installed AMII assets.
