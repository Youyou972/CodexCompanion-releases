<!-- sparkle-sign-warning:
IMPORTANT: This file was signed by Sparkle. Any modifications to this file requires updating signatures in appcasts that reference this file! This will involve re-running generate_appcast or sign_update.
-->
# CodexCompanion 1.2.0

Build `2026072409` · macOS 14 or newer

Status: unreleased production candidate.

## Management window

- Adds a native SwiftUI management window opened from **Open Companion…** in the menu-bar menu.
- Uses a preserved, quality-checked 3840×2160 version of the approved hand-drawn anime-fantasy workspace as a static, full-window background.
- Uses system materials and restrained high-contrast glass cards. The wallpaper has no animation, drift, parallax, or motion state.
- Embeds the searchable character library, local import, favorites, live artwork
  preview, reaction/audio controls, and placement controls directly in the
  management window. Core character and reaction workflows no longer redirect
  to legacy Settings.
- Reduces the menu-bar menu to a single **Open Companion…** action.
- Replaces the generic star status item with a bundled character image, with a system-symbol fallback if the resource is unavailable.

## Claude Desktop compatibility

- Recognizes the installed Claude Desktop bundle identifier `com.anthropic.claudefordesktop`.
- Marks Claude overlay support experimental and deferred. Live Preview QA
  recognized Claude as the frontmost process but received no focused standard
  macOS window frame, so no sticker or GIF could be placed reliably.
- Switching Claude chats is not a reaction trigger because Claude exposes no supported privacy-safe chat-switch lifecycle event.
- Does not read Claude chat contents, scrape private APIs, or claim Claude cloud-task lifecycle support.
- Keeps Codex task and goal database observation disabled while Claude is frontmost because Anthropic does not expose a supported outbound prompt/task lifecycle stream for companion apps.

## Preview behavior

- Preview builds install at `/Applications/CodexCompanion Preview.app` and may register that installed bundle itself as a login item. They no longer require the production app’s exact bundle path.
- Preview network update checks are intentionally disabled. The configured private production host currently does not resolve publicly, so invoking Sparkle from a Preview produced a generic retrieval error. Preview updates use manual replacement until a signed private appcast is available.
- Preview and production have separate macOS Accessibility identities. An ad-hoc Preview must be authorized separately before it can draw overlays over Codex or Claude; this cannot be granted programmatically.

## Updates and distribution

- The private source remains at `Youyou972/CodexCompanion`.
- Signed updates use the separate public HTTPS origin
  `https://youyou972.github.io/CodexCompanion-releases/`.
- Stable and beta appcasts are isolated by channel. No appcast item or binary is
  published until Developer ID signing, Apple notarization, stapling,
  Gatekeeper assessment, and Sparkle EdDSA signing all pass.
- Private GitHub Releases remain the authenticated manual fallback. The app
  never embeds a GitHub token.

## Verification

- Focused regression suite: 17 tests passed for branding resources, installed
  Preview login-item eligibility, private-Preview update configuration, and
  Claude capability boundaries.
- Fresh production-candidate macOS suite: 280 tests passed with zero failures;
  the optimized 1.2.0 (`2026072409`) Release configuration also built
  successfully.
- An isolated 1.2.0 build `2026072408` was built, ad-hoc signed, installed as
  `/Applications/CodexCompanion Preview.app`, and passed the single-item
  menu check, management-window opening, static-wallpaper comparison, inline
  placement rendering at 940×620 and 1280×792, and real login-item
  registration. macOS displayed **Login Item Added** for the installed Preview.
- The stable `/Applications/CodexCompanion.app` executable SHA-256 remained
  unchanged during Preview replacement.
- The production candidate archive and DMG were signed with
  `Developer ID Application: Yohann Blanchard (R7XQPWQTFV)`, Team ID
  `R7XQPWQTFV`, hardened runtime, and secure timestamps. Both signatures passed
  strict local verification.
- Apple accepted notarization submission
  `30f43285-0320-46ec-aae9-72480fb8c89f`. The final DMG ticket stapled and
  validated successfully, and Gatekeeper reported `accepted` with source
  `Notarized Developer ID`.
- Sparkle generated an EdDSA signature for the exact stapled DMG. Publication
  still fails closed unless the private tag/Release and public HTTPS appcast
  are derived from the same final commit and artifact.
