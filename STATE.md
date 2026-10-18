# Magic Island spec site — STATE (read first)

**What:** a spec homepage for Magic Island, 2215 Southwest Fwy, Houston (magicislandhtx.com), so the pitch shows the fix, not just the audit. Built 2026-10-17/18. The audit is in the vault: `Circle-Vault/Station/2026-10-17 Magic Island HTX - site dissection.md`. Memory: `magic-island-houston-prospect`.

**Current = v2, the scroll-film ("Under the Head").** Circle asked for "animated and immersive" mid-build; v1 (static, `work/static-v1.html`) is parked and superseded. v2 follows the `scroll-film-studio` skill, **Lane C** (the client's own footage, $0 generated).

**Where:** `C:\Users\Circl\magic-island\site\` — `index.html` (one file), `assets/` (stills, logo, textures), `frames/` (332 desktop WebP at 1600w, 17 MB) + `frames/phone/` (332 at 960w, 8.5 MB), `frames/cuts.json`, `frames/luma.json`. Preview config `magic-island` (:8864) in `~/.claude/.claude/launch.json`. **NOT deployed. NOT sent. No repo yet.** Live would be the usual `stationonemain-source.github.io/magic-island` (noindex) on Circle's call; push `site/` only (25 MB with frames).

**The film (one scroll, 620vh desktop / 560vh phone, seven hard-cut shots from their three June-2026 Vimeo promos):**
1. Aerial over the freeway and the building, dusk (hero beat, gold-dust ambient layer fades out over the first 7%)
2. The gold pharaoh bust in the green room — "Inside · The pharaohs kept watch."
3. The back-bar glassware — "Drinks · A new bar, polished and waiting."
4. Dining room focus-pull — "Dinner · Green walls, velvet chairs."
5. Levitation on the mural stage — "Disappearing acts · The intimate theatre upstairs."
6. Doves and applause — "Every night ends in applause."
7. The ballroom in service — finale "The ballroom · Taking bookings before the doors open." with both CTAs, then a fade to ink that hands off to the content.
Cuts dip to 55% black for ±3 frames so they read as cuts. Chapter readout bottom-left (I–VII), scroll cue bottom-right, header flips to dark text on bright frames via luma.json. Continuity gesture: every shot pushes forward/down.

**Cut sheet (seconds in the source files, all text-free):** c1 v…785 4.5–7.75 · c2 v…785 12.0–13.4 · c3 v…785 13.5–15.0 · c4 v…786 8.0–8.9 · c5 v…786 0–2.7 · c6 v…785 0–1.0 · c7 v…787 7.0–10.0 cropped to 1920×842 (the film's "EVENTS" caption sits in the bottom 22%). Clips in `work/clips/`, 24 fps. Rebuild: `CUTS=1 EVERY=1 WIDTH=1600 PHONE_WIDTH=960 Q=70 bash ~/.claude/skills/scroll-film-studio/scripts/assemble.sh work/clips site/frames c1-aerial c2-statue c3-glass c4-dining c5-levitate c6-doves c7-ballroom`.

**Source material (all theirs):** footage pulled through the public Vimeo player config (`work/src/vimeo_*.mp4`, 1080p); the agency's sparkle VFX remain in shots 2–4. Logo = their round badge, trimmed, never redrawn. Textures = their own licensed stock at 7%. Commons CC0 2021 exteriors in `work/src/` unused. Their media library also holds "VAGHA Night Club" and "COFFEEINE" logos (Elementor demo leftovers) — a pitch line.

**Type and colour:** Cinzel (the Trajan-style caps their logo ring and films use) + EB Garamond. Navy `#0d1e2b/#132b3c`, gold `#cfa64e`, cream `#efe4c6` from the logo; wine `#5f2626` from their current site.

**Facts and sources:** 1984 opening, private club, Vegas-style magic, psychics/palm readers, dress code, prime rib (Houstonia 2024, Texas Standard 2024); 2008 Hurricane Ike then a fire (ABC13 2024); Dr Mohammad Athari bought it in 2018 (Chronicle/Bisnow); theatre upstairs, large bar, covered patio, ballroom, murals kept (ABC13 + Texas Standard 2024); phone (713) 526-2442 from Facebook/Yelp; hiring from their Sept 2026 flyer. "Opening date to be announced" is deliberate: no date exists anywhere.

**⚠ Owner must confirm before anything goes live:** the rooms and their names; "magician at the table"; "every night ends in applause" (a line, not a promise); the 2018 purchase year; the phone still rings; the events contact; use of their promo footage on the site; a privacy policy (footer link is `#`); the sign-up form is NOT wired (shows a preview message on submit and says so).

**Verified 2026-10-18 (scripts/verify.js, isolated Playwright Chromium 1228 via `CHROME_PATH`, never the everyday Chrome):** `__ready` fires; `?jump` shots at every beat at 1905×1000 and 390×844 (`work/shots2/`); `?flat` 1440 capture; no console errors; Cinzel + EB Garamond loaded; no horizontal overflow; jank p95 ≈ 14 ms, one ~160 ms spike per run on the software GPU (startup decode burst, not the scrub). **Not yet scrubbed in a real desktop Chrome on Windows** (the ImageBitmap crash class is avoided by design: plain `<img>` + `decode()`).

**Footer credit:** "Designed by Station.Solutions" (not "hosted"). Spec disclaimer strip at the bottom. Run `link-preflight` on every outside link before it goes to anyone.
