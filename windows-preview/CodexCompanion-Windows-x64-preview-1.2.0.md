# CodexCompanion Windows x64 preview 1.2.0

Download:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.0/CodexCompanion-Windows-x64-preview-1.2.0.zip

SHA-256:

`47e6ecc48ca76e754dfa23d82536c3b80210710a5f610925aa56410e0d94b318`

This is a Windows preview build. It is not code-signed yet. This build seeds a visible sample asset on first app launch, writes diagnostics to `%APPDATA%\CodexCompanion\logs\codex-companion.log`, and includes the refreshed glass/anime management window plus improved overlay placeholder.

## Run

1. Extract the ZIP.
2. Open the extracted `publish` folder.
3. Run `CodexCompanion.exe`.

## Smoke test

From PowerShell in the extracted `publish` folder:

```powershell
powershell -ExecutionPolicy Bypass -File .\tools\SmokeTest-CodexCompanion.ps1 -PublishPath .
```

The helper verifies the executable, seeds a tiny sample AMII asset under `.\AMII\sample-smoke\`, starts the app, and prints PASS/WARN/FAIL evidence.

After launch, open the tray menu and choose **Open Companion**. Use the management window’s **Next Reaction** button to verify overlay rendering.
