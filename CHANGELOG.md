# Changelog

All notable changes to NullFit are tracked here. Each release on the [Releases page](../../releases) corresponds to one entry below.

## [Unreleased]

## [0.2.0] — 2026-05-15

### Added
- **Algorithm: Better (Pro)** — new face-aware refit with auto clipping repair baked into a single click. The Single Refit + Refit All Selected buttons now use this algorithm when Pro is activated. Catches polygon-level clipping that vertex-only refit misses — chest-side and underside body curves where cloth was sitting *too close* to the body or bridging across concavities.
- **Algorithm toggle in the panel** — Pro users can switch back to Standard (Free-equivalent algorithm) at any time. Free users see the toggle but it stays locked.
- **Auto Clipping Repair (Pro, standalone)** — manual fine-tuning tool. Three detection methods (Naive / Raycast / Winding Number), strength up to 2.0, optional smoothing, optional enforce-minimum-clearance mode, debug vertex group output showing exactly what was flagged.
- **Multi-Body Wardrobe Batch (Pro)** — select N outfits and M saved body presets, one click generates one shape key per outfit per silhouette. Toggle a preset's shape key to switch the whole wardrobe to that body type.
- **Plugin / companion version handshake** — plugin sends its version on every `/status` poll; companion surfaces a yellow banner when an outdated plugin is detected, with a one-click link to grab the latest from GitHub.

### Changed
- **Companion v0.1.1 → v0.2.0**. New Pro endpoints: `/refit/single-better`, `/refit/multi-body`, `/refit/clipping-repair`. Each runs four to five distinct validators across the route + algorithm boundaries, in addition to the obfuscation pass.
- Default clipping repair strength bumped from 1.0 to 1.5 — validated on test bodysuits as the value that clears typical body curvature without over-puffing tight outfits.

### Security
- **Server-side version sunset / kill switch**. The companion polls the license server's `/check-version` endpoint on startup and hourly. If the server flags a build as sunset (soft) or killed (hard), the companion surfaces a banner and — in the hard-kill case — refuses to run Pro features regardless of any locally-cached license token. Lets the operator force-update old or compromised versions without waiting for token expiry. Fail-open: if the server is unreachable, normal operation continues.

### Fixed
- Plugin operators that write to vertex groups now restore Edit-mode state if you launched them mid-edit.

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
