# Changelog

All notable changes to NullFit are tracked here. Each release on the [Releases page](../../releases) corresponds to one entry below.

## [Unreleased]

## [0.8.0] — 2026-05-26

The biggest performance pass since launch. Pro refits that used to take minutes on heavy outfits now finish in seconds, with bit-identical output to v0.7.0.

### Changed

- **Massive Pro performance pass.** Pro algorithms (Better, Surface, Snap) got a deep optimization to the part of the pipeline that was eating most of the runtime. Bigger outfits and denser meshes feel the difference the most. Output is byte-for-byte identical to v0.7.0 — same results, dramatically less waiting.
- **Free tier got better too.** The Free single-mode refit benefited from the same plumbing improvements as Pro — faster, cleaner, more reliable.
- Quiet refinements under the Pro hood to how Pro post-processes its results. Nothing you'll have to think about, but the Pro experience gets a little sharper.
- Various small reliability improvements and UI polish in the panel.
- Updated update-check banner behavior.
- **Pro price raised from $10 to $15** for new purchases, reflecting the consistent maintenance, performance work, and ongoing improvements that have rolled into the v0.x line. Existing license keys carry through unchanged — if you've already bought Pro at $7 or $10, you keep your key, you keep your lifetime updates, and you're already on v0.8.0 quality.

### Notes for existing customers

- Your Companion will show an **Update available** banner on next launch. Grab the latest from Gumroad — your existing Pro license keys carry over unchanged.

## [0.6.0] — 2026-05-24

Speed-focused release for Pro users. Pro features now skip redundant work after your first refit in a session, so each subsequent Pro refit feels noticeably snappier. Foundation release for a bigger performance pass landing in v0.7.0.

### Changed

- Pro features reuse the result of the first license check during an active session — subsequent Pro refits no longer pay that overhead each time. Same Pro algorithms, same quality, same final result on your avatar.
- Various internal cleanup rolled in.
- Activated license keys carry through unchanged from earlier versions.

### Coming next

- **v0.7.0** is a real performance pass on the Pro algorithms themselves (Better, Adaptive, Snap, MatchAll, MultiBody). Same algorithms, same quality, same final result — just much faster getting there.

## [0.5.5] — 2026-05-22

Small quality-of-life release — no new features, just a few rough edges polished.

### Changed

- Companion now politely exits if you accidentally launch it twice (e.g., once from Windows auto-start and once manually). The first instance keeps running; the second one shows a brief "already running" notice and goes away. Fixes the tray-icon duplication some people saw on busy boots.
- Various internal cleanup. Customers who saw heuristic antivirus false-positive flags on earlier versions should be less likely to see them now.
- Activated license keys carry through unchanged from earlier versions.

## [0.5.0] — 2026-05-18

Adds **Layered Body Refit** — a Pro feature built for avatars with a separate scales / fur / spike mesh on top of the base body. Refitting cloth against just one of the two meshes always produced a wrong result; this feature fits cloth against whichever layer is on top in each region and produces two shape keys you wire together in Unity.

### Added

- **Layer Mesh dropdown (Pro)** — new optional selector in Section 1 (Setup) right next to Body Mesh. Pick your scales / fur / spikes mesh and the refit fits cloth against whichever layer is on top per region.
- **Two shape keys on the cloth (Pro, automatic when Layer Mesh is set):**
  - **Body Match** — cloth fitted to the base body alone
  - **Body+Layer Match** — additive offset that accounts for the scale-mesh contribution on top
  - Wire both to the same Unity animator toggle for the combined fit; or wire only Body Match for animations where scales are hidden.
- All three Pro algorithms (**Better / Adaptive / Snap**) support Layered Body Refit. Adaptive and Snap are recommended for the typical static-scales case; Better is most useful when you want clipping repair to also push cloth out of the scales mesh.

### Changed

- **Companion app updated to v0.5.0** — bundles the layered-refit support.
- **Plugin updated to v0.5.0** — adds the Layer Mesh dropdown, two-key apply path, and updated Help & Workflow text.
- Help & Workflow section updated with troubleshooting notes for anthro / dragon avatars.
- Pro CTA bullet list updated to mention Layered Body Refit.

### Known limitation

- Shape Key Filter (Breasts Only / Exclude Breasts) is disabled when a Layer Mesh is set in this release — use one or the other for any given refit. Polish item for the next v0.5.x update.

### Notes for existing customers

- If you're on **NullFit 0.2.x or 0.4.x**, your Companion will show an **Update available** banner on next launch. Grab the latest from Gumroad — your existing Pro license keys carry over unchanged. **Pro price stays at $10**; lifetime updates on the v0.x line covers v0.5.

## [0.4.4] — 2026-05-18

Major Pro tier expansion — two new algorithms and four new refinement tools built specifically for the cases v0.2.x couldn't handle: anthro avatars, stylized proportions, dragons, and any irregular body where the standard refit produced distortion.

### Added — New Pro Algorithms

- **Adaptive (Pro)** — a refit option for complex avatars (anthro, stylized) where the Better algorithm isn't enough. Handles unusual shape key authoring that simpler refitters can't follow.
- **Snap (Pro)** — last-resort fit for irregular avatars (dragons, custom proportions). Snaps the cloth directly to the body's current shape, even when other refit options can't track the body correctly.

The algorithm row in the panel is now: **Standard | Better (Pro) | Adaptive (Pro) | Snap (Pro)**. The plugin's Help section explains when to use which.

### Added — New Pro Refinement Tools

- **Shape Key Filter** — restrict the refit to specific body regions. **Breasts Only** refits just the cup, leaves straps/band alone. **Exclude Breasts** refits everything except the chest. Custom name field for non-standard shape key names.
- **Strength Slider** — a single 0.5–2.0 dial that scales how aggressively the algorithm pushes cloth away from the body. Replaces the old millimeter-scale settings with one user-friendly number.
- **Preserved Faces** — Edit Mode, select faces you don't want touched, click Mark. Those vertices stay locked no matter what refit you run. Pairs with any algorithm tier.
- **Smoothing Workshop** — standalone smoothing tool with wide-range knobs (up to 100 passes, full 0–1 blend). Run it on any cloth shape key, click multiple times to layer the effect. Pair with Preserved Faces to protect detail while smoothing everything else.

### Added — Quality of Life

- Smarter handling of non-uniform body shape keys (silently helps every refit, not just Pro tiers).
- Help & Workflow section in the panel fully rewritten — covers all four algorithm tiers, troubleshooting paths for irregular avatars, and the full Pro feature list.
- Updated discoverability hints under the algorithm row — if a refit looks off, the panel tells you which stronger algorithm to try next.

### Changed

- **Pro price raised from $7 to $10** for new purchases. Existing license keys keep working — no action needed if you've already bought Pro.
- **Companion app updated to v0.4.4** — bundles the new Pro features.
- **Plugin updated to v0.4.8** — adds the new UI sections and operators.

### Notes for existing customers

If you're on **NullFit 0.2.x**, your Companion will show an **Update available** banner on next launch and your old plugin will get flagged as outdated once you update. Grab the latest from Gumroad — your existing Pro license keys carry over unchanged.

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
  - Align to Body — one-click positioning helper for outfits imported as FBX that land at the world origin.
  - Bake Cloth Pose — apply armature modifiers, for outfits with their own rig.
- **Pro tier** (requires Nullcore Companion + license):
  - Refit All Selected — apply to every selected cloth in one click.
  - Match-All Shape Keys — for every body shape key, create a matching cloth-side key.
  - Weight Transfer — copy the body's rigging weights onto store-bought outfits.
- **Nullcore Companion** — themed window with system-tray support, optional Windows-startup launch, in-app license activation.
- **Auto-launch from the plugin** — the companion starts itself when you click Refit if it isn't already running.
- **Auto-detect companion location** across common spots (Downloads, Desktop, Documents, Program Files, AppData) plus a **Scan** button for non-standard installs.
- **Built-in update checker** — the companion notifies you on startup when a new release is out.
