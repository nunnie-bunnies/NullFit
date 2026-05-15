# NullFit

**Avatar Clothing Refitter for Blender** — by [Nunnie Bunnies (Mao Mao)](https://mixxy.gumroad.com)

Refit any VRChat / character avatar's clothing to a sculpted body shape — without redoing the rig or re-weighting every garment by hand. Cut a 5+ hour clothing refit job down to 30 minutes.

> **Note:** For ~95% of outfits the refit is complete after one click. For tight-fitting outfits over large body changes (e.g., big chest/hip changes with a skin-tight bodysuit), you may want 30 seconds to a minute of touch-up sculpting on the resulting shape key. Blender's sculpt tools are built for exactly this — the algorithm gets you 95% there, your hand finishes the last 5%.

## Watch the workflow

**Full tutorial (2 minutes)** — shows the entire pipeline including the micro-cleanup on outfits that need it:

[![NullFit full workflow tutorial](https://img.youtube.com/vi/XlkG0XqYmdU/maxresdefault.jpg)](https://www.youtube.com/watch?v=XlkG0XqYmdU)

**Quick demo (7 seconds)** — just the magic moment:
https://www.youtube.com/watch?v=jdGFQduW3MQ

## How it works

NullFit is a Blender plugin + **Nullcore Companion** (a small helper app). The plugin reads your avatar's body + selected clothing, sends the data to the companion, and the companion runs the refit algorithm and sends the result back. The companion auto-launches when needed — you only install it once and forget about it.

The companion is the same app that ships with future Nullcore products (Sculptor, etc.) — install once, use everywhere.

## Tiers

| Feature | Free | Pro |
|---|---|---|
| Single refit (active cloth → "Body Match" shape key) | ✓ | ✓ |
| Combines all active body shape keys in one pass | ✓ | ✓ |
| Align cloth to body (one-click positioning helper) | ✓ | ✓ |
| Bake cloth pose to mesh (for outfits with their own armature) | ✓ | ✓ |
| **Batch refit** — apply to every selected cloth in one click | — | ✓ |
| **Match-All Shape Keys** — body's shape keys drive cloth's | — | ✓ |
| **Weight Transfer** — copy body's vertex groups to clothing | — | ✓ |

## Install

1. **Download the latest release** from the [Releases page](../../releases/latest) — you'll need:
   - `nullfit.py` (the Blender add-on)
   - `Nullcore.exe` (the companion app — free download)
2. **Install the plugin**: in Blender, **Edit → Preferences → Add-ons → Install...** → pick `nullfit.py` → check the box to enable it.
3. **Place `Nullcore.exe`** anywhere — the plugin auto-finds it in common locations (Downloads, Desktop, Documents, Program Files, %LOCALAPPDATA%) or you can set the path manually in the add-on preferences.
4. Open the **NullFit** tab in the 3D viewport sidebar (press **N** if it's hidden).

That's it for the Free tier. For Pro: buy a license at the [Gumroad page](https://mixxy.gumroad.com/l/NullFit-Pro), open `Nullcore.exe`, paste your key, click Activate.

## Quickstart

1. Sculpt your avatar's body using shape keys (boobs, butt, hips, whatever).
2. Set those shape keys to the values you want — the cloth will fit *that* silhouette.
3. In Blender's NullFit panel: pick the **Body Mesh** from the dropdown.
4. Select a clothing mesh in the viewport (right-click or click in the outliner).
5. Click **Refit Active Cloth**. New "Body Match" shape key appears on the cloth at value 1.0.

Toggle the new shape key on/off to compare. That's the entire free flow.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Refit button does nothing | Companion not running → enable Auto-launch in add-on preferences, or click Nullcore.exe manually |
| "Companion not found" | Set the path in Edit → Preferences → Add-ons → NullFit, or click the **Scan** button to auto-locate |
| Result looks jagged | Enable **Post-smooth** in the panel (2. Refit Parameters) |
| Cloth doesn't move | Check Max Body Distance — raise it for loose clothing (default 0.05m is for skin-tight) |
| Pro buttons greyed out after activating | Click the refresh ↻ icon next to "Nullcore Companion" in the panel, or just wait 5s for auto-refresh |
| "Cloth is X meters from body's center" error | Click the **Align to Body** button in section 3 (Tools), or position the cloth manually |
| Cloth has its own armature and looks wrong | Pose the armature to match the avatar, then click **Bake Cloth Pose** before refitting |

## Support

- **Discord:** [join the server](https://discord.gg/DRXRnPDmbJ) for help, feature requests, and demos
- **Issues:** [report a bug](../../issues)
- **Storefront:** [Gumroad](https://mixxy.gumroad.com)

## What's NOT in this repo

This is a closed-source product. The repository only hosts:
- This README
- Tagged release downloads (plugin + companion exe)
- Changelog
- Issue tracker

The source code for `Nullcore.exe` and the algorithms it runs are **not public**. The Blender plugin `nullfit.py` is a thin HTTP client — there's no algorithm code in it to fork.

## License

© 2026 Nunnie Bunnies (Mao Mao). All rights reserved. Redistribution, reverse-engineering, and sharing of license keys are prohibited. The Pro tier is licensed per machine via Gumroad.
