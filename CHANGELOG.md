# Changelog

All notable changes to NullFit are tracked here. Each release on the [Releases page](../../releases) corresponds to one entry below.

## [Unreleased]

## [0.2.2] — 2026-05-16

### Changed
- Another sweep through the plugin's comments and docstrings — same kind of polish as v0.2.1, just deeper. No user-visible behavior changes; existing scenes and presets all carry over.

## [0.2.1] — 2026-05-16

### Changed
- Polish + clarity pass on the plugin's panel copy, comments, and method labels. No user-visible behavior changes; existing scenes and presets all work as before.

## [0.2.0] — 2026-05-15

### Added
- **Algorithm: Better (Pro)** — a stronger refit that also cleans up body-poking-through-cloth as it goes, in a single click. Catches problem spots the Free refit can miss — sides of the chest, hip seams, where straps meet skin. The Single Refit and Refit All Selected buttons use Better automatically when Pro is activated.
- **Algorithm toggle in the panel** — Pro users can flip between **Standard** (the Free-equivalent algorithm) and **Better** at any time. Free users see the toggle, but Better stays locked until you activate Pro.
- **Auto Clipping Repair (Pro, standalone tool)** — fine-tune trouble spots after a refit. Pick how aggressive it should be (Fast / Balanced / Thorough), dial the strength, optionally smooth the result, and get a debug vertex group showing exactly what got flagged.
- **Multi-Body Wardrobe (Pro)** — save body shapes as presets and run any number of outfits against any number of presets in one click. Each outfit gets one shape key per body preset, so you can toggle a preset on and watch the whole wardrobe snap to that silhouette.
- **Plugin / companion version check** — the companion shows a yellow banner if your Blender plugin is out of date, with a one-click link to the latest release.

### Changed
- **Companion app updated to v0.2.0** — bundles the new Pro features.
- **Auto Clipping Repair strength default raised from 1.0 to 1.5** — better starting value across a range of test bodysuits.

### Fixed
- Plugin actions that touch vertex groups now leave you in the same mode they found you in, even if you triggered them mid-edit.

## [0.1.1] — 2026-05-14

### Added
- **Watch Tutorial** button in the About panel — opens the full workflow walkthrough on YouTube.
- README: embedded tutorial video + 7-second quick demo.

### Changed
- The companion's update checker now watches this GitHub repo for new releases — every running install will surface a banner when a new tag goes up.

## [0.1.0] — 2026-05-14

### Added
- Initial release.
- **Free tier:**
  - Single Refit — combines all active body shape keys into one "Body Match" key on the selected cloth.
  - Align to Body — one-click cloth positioning for FBX imports.
  - Bake Cloth Pose — apply armature modifiers, for outfits with their own rig.
- **Pro tier** (requires Nullcore Companion + license):
  - Refit All Selected — apply to every selected cloth in one click.
  - Match-All Shape Keys — for every body shape key, create a matching cloth-side key.
  - Weight Transfer — copy the body's rigging weights onto store-bought outfits.
- **Nullcore Companion** — themed window with system-tray support, optional Windows-startup launch, in-app license activation.
- **Auto-launch from the plugin** — the companion starts itself when you click Refit if it isn't already running.
- **Auto-detect companion location** across common spots (Downloads, Desktop, Documents, Program Files, AppData) plus a **Scan** button for non-standard installs.
- **Built-in update checker** — the companion notifies you on startup when a new release is out.
