# Changelog

All notable changes to NullFit are tracked here. Each release on the [Releases page](../../releases) corresponds to one entry below.

## [Unreleased]

## [0.1.1] — 2026-05-14

### Added
- About panel: **Watch Tutorial** button — opens the full workflow walkthrough on YouTube.
- README: embedded tutorial video + 7-second quick demo.

### Changed
- Update checker now points at this GitHub repo for release detection — every running companion will surface a banner when a newer tag is published.

## [0.1.0] — 2026-05-14

### Added
- Initial release.
- **Free tier** — Single-mode refit: combines all active body shape keys into one "Body Match" key on the selected cloth.
- **Pro tier** (requires Nullcore Companion + license):
  - Batch refit — apply to every selected cloth in one click.
  - Match-All Shape Keys — for every body shape key, create a matching cloth-side key (drivers-ready).
  - Weight Transfer — copy the body's vertex groups onto store-bought outfits.
- **Tools** (free):
  - Align to Body — one-click cloth positioning for FBX imports.
  - Bake Cloth Pose — apply armature modifiers, for outfits with their own armature.
- **Nullcore Companion** — fancy WPF window with system tray support, optional Windows startup, in-app license activation.
- Auto-launch from the plugin — companion starts itself when the user clicks Refit and it isn't already running.
- Auto-detect companion location across drives (`%LOCALAPPDATA%`, `%PROGRAMFILES%`, Downloads, Desktop, Documents) plus a "Scan" button for non-standard installs.
- Built-in update checker — companion notifies on startup when a new release is available.
- Honeypot endpoints for cracked-client detection.
