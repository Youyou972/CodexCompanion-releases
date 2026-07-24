# Publishing procedure

This repository is a public static host. Release construction and secret-bearing signing operations happen outside this repository.

## Required inputs

- a final Developer ID-signed and Apple-notarized archive
- a stapled and Gatekeeper-verified DMG when a DMG is distributed
- Sparkle EdDSA signature generated from the final archive
- SHA-256 checksums
- public release notes
- semantic version and monotonic build number

Never copy signing keys, notarization credentials, GitHub tokens, private source, chat data, local filesystem paths, or build logs into this repository.

## Stage a release

1. Create a branch named `release/<version>-<channel>`.
2. Add final artifacts beneath `downloads/<version>/`.
3. Add release notes at `release-notes/<version>.html`.
4. Update only the matching channel appcast:
   - stable: `stable/appcast.xml`
   - beta: `beta/appcast.xml`
5. Ensure all appcast URLs use the canonical GitHub Pages HTTPS origin.
6. Verify the appcast enclosure includes the expected version, build, length, and Sparkle EdDSA signature.
7. Record public SHA-256 checksums beside the artifact.

## Pre-merge verification

Run these checks against the exact staged artifact:

```sh
codesign --verify --deep --strict --verbose=2 CodexCompanion.app
spctl --assess --type execute --verbose=4 CodexCompanion.app
xcrun stapler validate CodexCompanion.app
shasum -a 256 CodexCompanion-<version>.zip
```

For a DMG, run the equivalent `spctl --assess --type open` and `xcrun stapler validate` checks against the DMG. Verify the Sparkle EdDSA signature using the public key embedded in the shipped app.

Review the staged file list and content before merge:

```sh
git diff --cached --name-only
git diff --cached --check
git grep -n -I '/Users/' -- ':!PUBLISHING.md'
git grep -n -I -E 'BEGIN .*PRIVATE KEY|github_pat_|gh[opsu]_' -- ':!PUBLISHING.md'
```

Treat every match as a stop-and-review condition.

## Publish and validate

1. Merge the reviewed release branch into `main`.
2. Wait for the GitHub Pages deployment to succeed.
3. Fetch the appcast, release notes, and artifacts from their public HTTPS URLs.
4. Compare downloaded byte counts and SHA-256 checksums with the staged files.
5. Test the in-app update from the prior signed version.
6. Confirm the updated app identity, version, build, signature, notarization, preferences, and rollback path.

## Rollback

If an update is defective, restore the prior known-good appcast as a new commit. Do not delete or silently replace versioned artifacts. Keep the prior signed installer available and document the manual fallback.
