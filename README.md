# AION 2 Lag Reduction INI Generator

A browser-based tool that generates a tailored `Engine.ini` block for **AION 2**, tuned to your GPU's VRAM and your preferred quality preset. Designed to reduce stutter, micro-freezes, and combat hitches **without touching visual quality** or locking your in-game graphics options.

🔗 **Live site:** [https://waelisa.github.io/aion2ini/](https://waelisa.github.io/aion2ini/)

---

## Features

- **GPU-aware generation** — Select your graphics card or VRAM tier (24GB+ down to 2GB or less) and the generator sizes the texture streaming pool, temp memory, and GC interval to fit your hardware.
- **Quality presets** — Four presets (**Low / Medium / High / Ultra**) adjust view distance, shadows, effects, and post-processing independently of the VRAM settings.
- **Safe by design** — The generated block does not alter visuals or in-game options. Deleting the pasted block is a 100% clean revert.
- **No install** — Pure HTML/CSS/JS. Runs entirely in the browser.
- **One-click copy** — Generates a ready-to-paste block with a header comment showing your selected GPU tier and quality preset.

---

## Quick Start

1. Open the [live site](https://waelisa.github.io/aion2ini/).
2. Select your **graphics card** (or use the VRAM fallback panel if yours isn't listed).
3. Choose a **quality preset**.
4. Click **Copy everything**.
5. Close AION 2 completely.
6. Press `Win + R`, paste `%LOCALAPPDATA%\AION2\Saved\Config\Windows`, and hit Enter.
7. Open `Engine.ini` in Notepad.
8. Leave existing content untouched and paste the copied block at the **very bottom**.
9. Save and launch the game.

### Reverting

Delete the pasted block from `Engine.ini` and save. That's it — no other cleanup required.

> **Tip:** Right-click `Engine.ini` → Properties → check **Read-only** to prevent game patches from resetting your tweaks.

---

## How It Works

### VRAM Tiers

The generator sizes `r.Streaming.PoolSize`, `r.Streaming.MaxTempMemoryAllowed`, and `gc.TimeBetweenPurgingPendingKillObjects` based on the selected tier:

| Tier | VRAM        | Pool (MB) | Temp (MB) | GC Interval | HLOD |
|------|-------------|-----------|-----------|-------------|------|
| 1    | 24GB+       | 12288     | 2048      | 180s        | Yes  |
| 2    | 16GB        | 10240     | 2048      | 150s        | Yes  |
| 3    | 12GB        | 8192      | 1024      | 120s        | Yes  |
| 4    | 10GB        | 7168      | 1024      | 120s        | Yes  |
| 5    | 8GB         | 6144      | 512       | 90s         | No   |
| 6    | 6GB         | 4096      | 512       | 90s         | No   |
| 7    | 4GB         | 3072      | 256       | 60s         | No   |
| 8    | 2GB or less | 2048      | 256       | 60s         | No   |

### Quality Presets

Each preset adjusts `r.ViewDistanceScale`, shadow quality, SSR, particle light quality, and post-processing settings. Defaults are loosely based on the [Aion2Timers advanced guide](https://www.aion2timers.com/game-ini/#advanced).

- **Low** — Maximum FPS. Shadows and effects heavily reduced.
- **Medium** — Balanced. Good visuals with stable frame times.
- **High** — Sharper distant objects and characters. Higher GPU load.
- **Ultra** — Maximum visuals. Only for top-tier GPUs.

---

## Local Development

No build step required. Just open `index.html` in a browser.
