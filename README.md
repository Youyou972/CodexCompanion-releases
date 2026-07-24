# CodexCompanion release feed

Public, static update hosting for CodexCompanion. The application source remains in a separate private repository.

## Public layout

- `stable/appcast.xml` — stable-channel Sparkle feed, created only when a verified release exists
- `beta/appcast.xml` — beta-channel Sparkle feed, created only when a verified beta exists
- `downloads/<version>/` — notarized, stapled release archives and optional DMGs
- `release-notes/<version>.html` — public release notes

Placeholder files keep the empty channel directories visible. They are not appcasts and contain no release items.

## Publication policy

Nothing may be published until all of these gates pass:

1. Build the release from the private source repository at a recorded commit.
2. Sign the app and distribution artifacts with the intended Developer ID identity.
3. Verify the app signature and designated requirement with `codesign`.
4. Submit the distribution artifact to Apple and receive an accepted notarization result.
5. Staple and validate the notarization ticket on the distributed app or DMG.
6. Verify the final artifact with `spctl` and re-check its cryptographic checksum.
7. Sign the Sparkle archive with the configured EdDSA key and verify the generated signature.
8. Generate the channel appcast using only the final public HTTPS artifact and release-note URLs.
9. Stage the versioned artifact, release notes, and appcast together in a review branch.
10. Confirm there are no credentials, private paths, source files, internal logs, or private metadata in the staged tree.
11. Merge to `main`, wait for GitHub Pages deployment, and verify every public URL over HTTPS.
12. Run the manual in-app update test from an older signed build and retain rollback instructions.

If any signing, notarization, stapling, Gatekeeper, Sparkle-signature, or HTTPS check fails, publication stops. An older valid appcast remains untouched.

See [PUBLISHING.md](PUBLISHING.md) for the repeatable release procedure.
