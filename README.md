# PlayMaGame

Solo builder. I take ideas to shipped software — FastAPI, Electron, ffmpeg pipelines, OBS/Discord/Twitch integrations.

I don't have a CS degree. What I do have is a habit: if it doesn't work the way I want, I keep going until it does — or until I find the shorter route I missed the first time.

## The clip pipeline

Three parts, running daily. Kill → clip → phone → export.

**[killfeed-saver](https://github.com/PlayMaGame/killfeed-saver-for-clipdeck)** — watches the killfeed over OBS and saves one clip per fight, at the length the fight turns out to be. Extra kills reset the tail instead of stacking; if you're talking, the clip closes 2.5s after you stop; a follow-up kill re-saves longer and deletes the shorter. The killfeed is transparent text over a background that shifts bright to dark, so OCR has no stable contrast — white-gating, confidence gating and row dedupe get it close, and it can't reach 100% without reading game memory, which breaks TOS. So every miss is logged instead: unmatched rows, and a trace of exactly why each clip got its length.

**[clipdeck](https://github.com/PlayMaGame/clipdeck)** — the bottleneck in clipping isn't editing, it's deciding, and deciding is dead time. Pulls clips off the share, rips 1080x1920 with a minimap PiP, and serves a phone deck where you swipe to keep, delete or defer. Defer isn't a verdict — the clip comes back. Sources are only removed after a verified rip (`moov` atom, duration, size), and only when deletion is explicitly enabled.

**[clip-merger](https://github.com/PlayMaGame/clip-merger)** — Electron timeline editor. Lossless keyframe-aligned cuts when the cut lands on a keyframe, re-encode when it doesn't, encoders probed at runtime because the listed ones still fail. The real work here was fidelity: making the preview match the export.

## Gloria Victis guild platform

**[Quest-Board](https://github.com/PlayMaGame/Gloria-Victis-Quest-Board)** — quests, claims, loyalty, shop and live chat for my guild. Single-file HTML on GitHub Pages, Postgres with RLS and Realtime behind it, discord.js bot for claims. Real-time across everyone's screen, no build step, no framework. Built for one guild, not hardened for public use.

## Smaller things

- **[GV FOV unlock](https://github.com/PlayMaGame/Gloria-Victis-fov-unlock)** — works out that the FOV cap is per-aspect-ratio, then patches the paired 120/140 constants so a 16:9 monitor gets the ultrawide view.
- **[FireFox compact mode](https://github.com/PlayMaGame/FireFox-compact-mode)** — userChrome scripts via fx-autoconfig: tabs, bookmarks, extension buttons.
- **[Outer Empires 2 userscripts](https://github.com/PlayMaGame/Outer-Empires-2-userscripts)** — 22 scripts for a game that will never get official ones.

## How I work

AI handles the typing. I own the architecture, the edge cases, and the failure modes — and I don't trust anything I can't check myself.

📫 [Twitch](https://twitch.tv/WekizZ) · [YouTube](https://youtube.com/c/wekizz) · [Reddit](https://reddit.com/u/PlayMaGame)
