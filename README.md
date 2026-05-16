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

NullFit is a Blender plugin plus a small companion app — they talk to each other in the background. The plugin reads your body + clothing, the companion runs the refit, the new shape key lands on your cloth a second or two later. The companion auto-launches when you click Refit, so you install it once and forget about it.

The companion is also the same app that ships with future Nullcore products (Sculptor, etc.) — one install, all the tools.

## Tiers

| Feature | Free | Pro |
|---|---|---|
| Single Refit — fit the selected cloth to your body's current shape | ✓ | ✓ |
| Align to Body — snap an FBX import to the right position | ✓ | ✓ |
| Bake Cloth Pose — flatten a posed outfit before refitting | ✓ | ✓ |
| **Algorithm: Better** — stronger refit that also cleans up cloth clipping, one click | — | ✓ |
| **Refit All Selected** — batch a whole wardrobe in one go | — | ✓ |
| **Match-All Shape Keys** — every body shape key gets a matching cloth-side key | — | ✓ |
| **Weight Transfer** — copy the body's rigging weights onto store-bought outfits | — | ✓ |
| **Multi-Body Wardrobe** — save body presets, generate one shape key per outfit per preset | — | ✓ |
| **Auto Clipping Repair** — standalone tool for fine-tuning trouble spots | — | ✓ |

### What's Algorithm: Better?

Pro's headline feature. A stronger refit that also cleans up body-poking-through-cloth as it goes — catches problem spots the Free refit can miss, like the sides of the chest, hip seams, and where straps meet skin. All in one click. You can flip between **Standard** (the Free algorithm) and **Better** from the panel at any time.

## Install

1. **[Download NullFit (Free)](https://mixxy.gumroad.com/l/NullFit)** — the Gumroad page gives you two files:
   - `nullfit.py` (the Blender add-on)
   - `NullcoreCompanion-vX.Y.Z.zip` (the companion app)
2. **Install the plugin**: in Blender, **Edit → Preferences → Add-ons → Install...** → pick `nullfit.py` → check the box to enable it.
3. **Unzip and place `Nullcore.exe`** anywhere — the plugin auto-finds it in common spots (Downloads, Desktop, Documents, Program Files). If yours lives somewhere unusual, just point at it in the add-on preferences or click **Scan**.
4. Open the **NullFit** tab in the 3D viewport sidebar (press **N** if it's hidden).

That's it for the Free tier. For Pro features (Better algorithm, wardrobe batch, auto clipping repair, multi-body presets): buy a license at the [Pro page](https://mixxy.gumroad.com/l/NullFit-Pro) ($7), open `Nullcore.exe`, paste your key, click Activate.

## Quickstart

1. Sculpt your avatar's body using shape keys (boobs, butt, hips, whatever).
2. Set those shape keys to the values you want — the cloth will fit *that* silhouette.
3. In Blender's NullFit panel: pick the **Body Mesh** from the dropdown.
4. Select a clothing mesh in the viewport (right-click or click in the outliner).
5. Click **Refit Active Cloth**. A new "Body Match" shape key appears on the cloth at value 1.0.

Toggle the new shape key on/off to compare. That's the entire free flow. Pro users get the same flow but with the Better algorithm doing the work and clipping cleanup folded in.

## Troubleshooting

| Symptom | Fix |
|---|---|
| Refit button does nothing | The companion isn't running. Turn on auto-launch in the add-on preferences, or open `Nullcore.exe` once and leave it. |
| "Companion not found" | Point at it in **Edit → Preferences → Add-ons → NullFit**, or click **Scan** to auto-locate. |
| Result looks jagged | Turn on **Post-smooth** under Refit Parameters. |
| Cloth doesn't move | Bump up **Max Body Distance** — the default is set for skin-tight outfits; raise it for looser clothing. |
| Pro buttons stay greyed out after activating | Hit the ↻ refresh icon next to "Nullcore Companion" in the panel, or wait a few seconds for auto-refresh. |
| "Cloth is X meters from body's center" | Click **Align to Body** in the Tools section, or drag the cloth into roughly the right spot manually. |
| Cloth has its own rig and looks wrong | Pose the rig to match the avatar, then click **Bake Cloth Pose** before refitting. |

## Support

- **Discord:** [join the server](https://discord.gg/DRXRnPDmbJ) for help, feature requests, and demos
- **Issues:** [report a bug](../../issues)
- **Storefront:** [Gumroad](https://mixxy.gumroad.com)

## What's NOT in this repo

NullFit is a closed-source product. This repository hosts:

- This README and the changelog
- Release downloads (plugin + companion exe)
- The issue tracker

The companion app and the algorithms it runs are not open-source — they're what you get when you buy Pro.

## License

© 2026 Nunnie Bunnies (Mao Mao). All rights reserved. Redistribution, reverse-engineering, and sharing of license keys are prohibited. The Pro tier is licensed per machine via Gumroad.
