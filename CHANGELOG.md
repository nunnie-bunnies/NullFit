# Changelog

All notable changes to NullFit are tracked here.

## [0.9.10] — 2026-05-28

Maintenance release. Various small improvements and minor polish. Feature set unchanged from v0.8.0.

### Changed

- Clearer messages when activation hits a temporary rate limit.
- Various small reliability improvements throughout the app.
- UI polish in the panel.

### Notes for existing customers

- Your Companion will show an **Update available** banner on next launch. Grab the latest from Gumroad — your existing license keys carry over unchanged.

## [0.8.0] — 2026-05-26

The biggest performance pass since launch. Refits that used to take minutes on heavy outfits now finish in seconds, with byte-for-byte identical output to v0.7.0.

### Changed

- **Massive performance pass.** The refit algorithms (Better, Adaptive, Snap) got a deep optimization to the part of the pipeline that was eating most of the runtime. Bigger outfits and denser meshes feel the difference the most. Output is byte-for-byte identical to v0.7.0 — same results, dramatically less waiting.
- Various small reliability improvements and UI polish in the panel.
- Updated update-check banner behavior.

### Notes for existing customers

- Your Companion will show an **Update available** banner on next launch. Grab the latest from Gumroad — your existing license keys carry over unchanged.

## [0.6.0] — 2026-05-24

Speed-focused release — repeat refits within a session are noticeably snappier. Foundation release for a bigger performance pass landing in v0.7.0.

### Changed

- Repeat refits in an active session are faster — same algorithms, same quality, same final result on your avatar.
- Various internal cleanup rolled in.
- Activated license keys carry through unchanged from earlier versions.

### Coming next

- **v0.7.0** is a real performance pass on the algorithms themselves (Better, Adaptive, Snap, Match-All, Multi-Body). Same algorithms, same quality, same final result — just much faster getting there.

## [0.5.5] — 2026-05-22

Small quality-of-life release — no new features, just a few rough edges polished.

### Changed

- Companion now politely exits if you accidentally launch it twice (e.g., once from Windows auto-start and once manually). The first instance keeps running; the second shows a brief "already running" notice and goes away. Fixes the tray-icon duplication some people saw on busy boots.
- Various internal cleanup. Customers who saw heuristic antivirus false-positive flags on earlier versions should be less likely to see them now.
- Activated license keys carry through unchanged from earlier versions.

## [0.5.0] — 2026-05-18

Adds **Layered Body Refit** — built for avatars with a separate scales / fur / spike mesh on top of the base body. Refitting cloth against just one of the two meshes always produced a wrong result; this fits cloth against whichever layer is on top in each region and produces two shape keys you wire together in Unity.

### Added

- **Layer Mesh dropdown** — new optional selector in Section 1 (Setup) right next to Body Mesh. Pick your scales / fur / spikes mesh and the refit fits cloth against whichever layer is on top per region.
- **Two shape keys on the cloth (automatic when Layer Mesh is set):**
  - **Body Match** — cloth fitted to the base body alone
  - **Body+Layer Match** — additive offset that accounts for the scale-mesh contribution on top
  - Wire both to the same Unity animator toggle for the combined fit; or wire only Body Match for animations where scales are hidden.
- All three algorithms (**Better / Adaptive / Snap**) support Layered Body Refit. Adaptive and Snap are recommended for the typical static-scales case; Better is most useful when you want clipping repair to also push cloth out of the scales mesh.

### Changed

- **Companion + plugin updated to v0.5.0** — bundles the layered-refit support, adds the Layer Mesh dropdown and two-key apply path, and updated Help & Workflow text with troubleshooting notes for anthro / dragon avatars.

### Known limitation

- Shape Key Filter (Breasts Only / Exclude Breasts) is disabled when a Layer Mesh is set in this release — use one or the other for any given refit. Polish item for the next v0.5.x update.

### Notes for existing customers

- Your Companion will show an **Update available** banner on next launch. Grab the latest from Gumroad — your existing license keys carry over unchanged.

## [0.4.4] — 2026-05-18

Major expansion — two new algorithms and four new refinement tools built specifically for the cases v0.2.x couldn't handle: anthro avatars, stylized proportions, dragons, and any irregular body where the standard refit produced distortion.

### Added — New Algorithms

- **Adaptive** — a refit option for complex avatars (anthro, stylized) where the Better algorithm isn't enough. Handles unusual shape key authoring that simpler refitters can't follow.
- **Snap** — last-resort fit for irregular avatars (dragons, custom proportions). Snaps the cloth directly to the body's current shape, even when other refit options can't track the body correctly.

The algorithm row in the panel is now: **Standard | Better | Adaptive | Snap**. The plugin's Help section explains when to use which.

### Added — New Refinement Tools

- **Shape Key Filter** — restrict the refit to specific body regions. **Breasts Only** refits just the cup, leaves straps/band alone. **Exclude Breasts** refits everything except the chest. Custom name field for non-standard shape key names.
- **Strength Slider** — a single 0.5–2.0 dial that scales how aggressively the algorithm pushes cloth away from the body. Replaces the old millimeter-scale settings with one user-friendly number.
- **Preserved Faces** — Edit Mode, select faces you don't want touched, click Mark. Those vertices stay locked no matter what refit you run.
- **Smoothing Workshop** — standalone smoothing tool with wide-range knobs (up to 100 passes, full 0–1 blend). Run it on any cloth shape key, click multiple times to layer the effect. Pair with Preserved Faces to protect detail while smoothing everything else.

### Added — Quality of Life

- Smarter handling of non-uniform body shape keys.
- Help & Workflow section in the panel fully rewritten — covers all four algorithms, troubleshooting paths for irregular avatars, and the full feature list.
- Updated discoverability hints under the algorithm row — if a refit looks off, the panel tells you which stronger algorithm to try next.

### Changed

- **Companion updated to v0.4.4 / plugin to v0.4.8** — bundles the new features and UI sections.

### Notes for existing customers

- Your Companion will show an **Update available** banner on next launch, and your old plugin will get flagged as outdated once you update. Grab the latest from Gumroad — your existing license keys carry over unchanged.

## [0.2.2] — 2026-05-16

### Changed
- Another sweep through the plugin's comments and docstrings — same polish as v0.2.1, just deeper. No user-visible behavior changes.

## [0.2.1] — 2026-05-16

### Changed
- Polish + clarity pass on the plugin's panel copy, comments, and labels. No user-visible behavior changes.

## [0.2.0] — 2026-05-15

### Added
- **Better algorithm** — a stronger refit that also cleans up body-poking-through-cloth as it goes, in a single click. Catches problem spots the standard refit can miss — sides of the chest, hip seams, where straps meet skin.
- **Algorithm toggle in the panel** — flip between **Standard** and **Better** at any time.
- **Auto Clipping Repair (standalone tool)** — fine-tune trouble spots after a refit. Pick how aggressive it should be (Fast / Balanced / Thorough), dial the strength, optionally smooth the result, and get a debug vertex group showing exactly what got flagged.
- **Multi-Body Wardrobe** — save body shapes as presets and run any number of outfits against any number of presets in one click. Each outfit gets one shape key per body preset.
- **Plugin / companion version check** — the companion shows a banner if your Blender plugin is out of date, with a one-click link to the latest release.

### Changed
- **Companion updated to v0.2.0.**
- **Auto Clipping Repair strength default raised from 1.0 to 1.5** — better starting value across a range of test bodysuits.

### Fixed
- Plugin actions that touch vertex groups now leave you in the same mode they found you in, even if you triggered them mid-edit.

## [0.1.1] — 2026-05-14

### Added
- **Watch Tutorial** button in the About panel — opens the full workflow walkthrough on YouTube.
- README: embedded tutorial video + quick demo.

### Changed
- The companion's update checker now watches this GitHub repo for new releases — every running install will surface a banner when a new tag goes up.

## [0.1.0] — 2026-05-14

### Added
- Initial release. Refit your avatar's clothing to a sculpted body shape:
  - **Single Refit** — combines all active body shape keys into one "Body Match" key on the selected cloth.
  - **Refit All Selected** — apply to every selected cloth in one click.
  - **Match-All Shape Keys** — for every body shape key, create a matching cloth-side key.
  - **Weight Transfer** — copy the body's rigging weights onto store-bought outfits.
  - **Align to Body** — one-click positioning helper for outfits imported as FBX that land at the world origin.
  - **Bake Cloth Pose** — apply armature modifiers, for outfits with their own rig.
- **Nullcore Companion** — themed window with system-tray support, optional Windows-startup launch, in-app license activation.
- **Auto-launch from the plugin** — the companion starts itself when you click Refit if it isn't already running.
- **Auto-detect companion location** across common spots (Downloads, Desktop, Documents, Program Files, AppData) plus a **Scan** button for non-standard installs.
- **Built-in update checker** — the companion notifies you on startup when a new release is out.
