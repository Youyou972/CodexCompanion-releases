# CodexCompanion Windows 1.2.2

Download installer:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.2/CodexCompanion-win-Setup.exe

Installer SHA-256:

`2b6a3bf5ed606a565f874871f5569c7d02cf8b4724f19fc1f99dc8c892814338`

Velopack feed:

https://github.com/Youyou972/CodexCompanion-releases/releases/download/v1.2.2/releases.win.json

Feed SHA-256:

`3708f2eb2edf967824e1cae3226ac55395f95e85f52334855830736609455a68`

This release fixes the empty Windows sticker/GIF library problem:

- Bundles 40 real AMII starter GIFs in the installer/update package.
- Adds **Choose assets** in the management window to select a full local AMII/export folder.
- Shows an explicit empty-library state instead of silently falling back to the placeholder.
- Logs exact GIF/sticker decode failures.

Notes:

- Windows artifacts are not code-signed yet.
- Portable ZIP runs cannot self-update.
- Existing installed 1.2.1 Setup builds should discover 1.2.2 through the public Velopack feed.
