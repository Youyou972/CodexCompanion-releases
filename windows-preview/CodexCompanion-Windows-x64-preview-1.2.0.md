# CodexCompanion Windows x64 preview 1.2.0

Download:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.0/CodexCompanion-Windows-x64-preview-1.2.0.zip

SHA-256:

`e0b0417f3f2ea76f1110f9fc81e53350caa81fe8f9f8dfa9da8cb780236234b0`

This is a Windows preview build. It is not code-signed yet.

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
