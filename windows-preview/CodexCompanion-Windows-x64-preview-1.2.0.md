# CodexCompanion Windows x64 preview 1.2.0

Download:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.0/CodexCompanion-Windows-x64-preview-1.2.0.zip

SHA-256:

`350795412d2d749059518c7ad9839ec626b18a302fbefc03d6b9a4d5d6536420`

This is a Windows preview build. It is not code-signed yet. This build seeds a visible sample asset on first app launch and writes diagnostics to `%APPDATA%\CodexCompanion\logs\codex-companion.log`.

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

After launch, use the tray menu’s **Next Reaction** action to verify overlay rendering.
