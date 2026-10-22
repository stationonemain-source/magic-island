# Magic Island spec site — STATE (read first)

**What:** a spec homepage for Magic Island, 2215 Southwest Fwy, Houston (magicislandhtx.com), so the pitch shows the fix, not just the audit. Built 2026-10-17/18. The audit is in the vault: `Circle-Vault/Station/2026-10-17 Magic Island HTX - site dissection.md`. Memory: `magic-island-houston-prospect`.

**Current = v3 (2026-10-21), the scroll-film cut down to three clean shots.** v2 (seven shots, 2026-10-18) is superseded; its frames are parked in `work/frames-v2-old/`. v1 static is `work/static-v1.html`.

**v3.1 (2026-10-21, same day): five shots, two of them AI-assisted from his real stills (Higgsfield Seedance 2.5, image-to-video, Circle approved).** Order: opening (AI push-in from the real drone frame at 785 7.30s toward the pharaoh head — head checked against the real 786 aerial: cobra, striped nemes, long beard match) → Dinner (AI dolly from the despeckled dining still, FIRST 2.5 s ONLY — after that it invents the back room) → Drinks (AI glide from the bar-glass still, 0.5–1.6 s ONLY — after that it sculpts a face onto the sphinx) → levitation (real) → doves (real). Generated sources in `work/gen/` (dining-v1, bar-v1, facade-v1); trimmed clips `work/clips2/a1-open, a2-dining, a3-bar`. 217 frames, cuts [49,87,114,192]; desktop 600vh / phone 540vh. Phone crop x: open 585 · dining 775 · bar 725 · levitation 969 · doves 700. ⚠ When re-extracting phone frames from the VFR master use `-fps_mode passthrough` or ffmpeg pads to 1,341 frames. Credits used: 3 × 64 of 381.

**Why v3:** Circle's review 10-21 — no sparkles (our gold-dust canvas layer is deleted; the agency's baked sparkle VFX ruled out the bar, dining and bust shots), and the phone crop of the old doves clip showed the agency's burned-in "Houston's Landmark Restaurant is Returning" title. The bar/couple/cocktail shots in their promos look like stock, not the venue — deliberately NOT used.

**Where:** `C:\Users\Circl\magic-island\site\` — `index.html` (one file), `assets/`, `frames/` (137 desktop WebP at 1600w, 6.4 MB) + `frames/phone/` (137 portrait WebP 680×980, 3.2 MB, pre-cropped from the 1080p master: crop x facade 585 · levitation 969 · doves 700 of 1920). Preview config `magic-island` (:8864) in `~/.claude/.claude/launch.json`. **LIVE (noindex) at https://stationonemain-source.github.io/magic-island/** — public repo `stationonemain-source/magic-island`, root = this `site/` folder, GitHub Pages from main `/`. **NOT sent to the client.** To update: edit here, commit, `git push`.

**The film (460vh desktop / 420vh phone, three hard-cut shots, all filmed at the real building, no text, no sparkles):**
1. Drone drift onto the front facade and the pharaoh head (785 6.70–7.82) — hero beat.
2. The levitation on the mural stage (786 0.00–2.58) — "Disappearing acts · The intimate theatre upstairs."
3. Doves released on the same stage (786 2.63–3.45) — finale "Opening soon · Dinner, drinks and disappearing acts." with both CTAs.
Frames play over scroll 0–0.84 (`HOLD`), the last frame holds under the finale, then a fade to ink. All captions sit lower-left over a bottom + left scrim. Header has a top scrim over the film and turns solid (`.solid`) once the film has scrolled past. Frames load nearest-to-viewer first (fast scrollers never freeze the film); the loader lifts after 12 frames. Clips in `work/clips2/`; rebuild desktop: `CUTS=1 EVERY=1 WIDTH=1600 Q=70 bash ~/.claude/skills/scroll-film-studio/scripts/assemble.sh work/clips2 site/frames s1-facade s2-levitate s3-doves`, then rebuild `frames/phone` with the ffmpeg crop above (assemble's own phone set is a centre crop at 960w and looks soft).

**Stills:** `dining-room-*` was despeckled 10-21 (OpenCV inpaint of the agency sparkles; originals in `work/assets-orig/`); faint red flare ghosts remain at 100%. The pharaoh-bust still is no longer used on the page (blurry + sparkles).

**Source material (all theirs):** footage pulled through the public Vimeo player config (`work/src/vimeo_*.mp4`, 1080p); the agency's sparkle VFX remain in shots 2–4. Logo = their round badge, trimmed, never redrawn. Textures = their own licensed stock at 7%. Commons CC0 2021 exteriors in `work/src/` unused. Their media library also holds "VAGHA Night Club" and "COFFEEINE" logos (Elementor demo leftovers) — a pitch line.

**Type and colour:** Cinzel (the Trajan-style caps their logo ring and films use) + EB Garamond. Navy `#0d1e2b/#132b3c`, gold `#cfa64e`, cream `#efe4c6` from the logo; wine `#5f2626` from their current site.

**Facts and sources:** 1984 opening, private club, Vegas-style magic, psychics/palm readers, dress code, prime rib (Houstonia 2024, Texas Standard 2024); 2008 Hurricane Ike then a fire (ABC13 2024); Dr Mohammad Athari bought it in 2018 (Chronicle/Bisnow); theatre upstairs, large bar, covered patio, ballroom, murals kept (ABC13 + Texas Standard 2024); phone (713) 526-2442 from Facebook/Yelp; hiring from their Sept 2026 flyer. "Opening date to be announced" is deliberate: no date exists anywhere.

**⚠ Owner must confirm before anything goes live:** the rooms and their names; "magician at the table"; "every night ends in applause" (a line, not a promise); the 2018 purchase year; the phone still rings; the events contact; use of their promo footage on the site; a privacy policy (footer link is `#`); the sign-up form is NOT wired (shows a preview message on submit and says so).

**Verified 2026-10-21 (v3):** isolated Playwright Chromium 1228 (phone 390×844, tablet 820×1180, desktop 1280×800, throttled 9 Mbps / 150 ms) — film reaches every shot, ready ≈ 2.8 s phone / 3.4 s desktop, no console errors, no horizontal overflow, header solid below the film. NB the Claude browser pane never resolves `img.decode()` while hidden — a hung loader there is the pane, not the site.

**Verified 2026-10-18 (v2) (scripts/verify.js, isolated Playwright Chromium 1228 via `CHROME_PATH`, never the everyday Chrome):** `__ready` fires; `?jump` shots at every beat at 1905×1000 and 390×844 (`work/shots2/`); `?flat` 1440 capture; no console errors; Cinzel + EB Garamond loaded; no horizontal overflow; jank p95 ≈ 14 ms, one ~160 ms spike per run on the software GPU (startup decode burst, not the scrub). **Not yet scrubbed in a real desktop Chrome on Windows** (the ImageBitmap crash class is avoided by design: plain `<img>` + `decode()`).

**Footer credit:** "Designed by Station.Solutions" (not "hosted"). Spec disclaimer strip at the bottom. Run `link-preflight` on every outside link before it goes to anyone.
