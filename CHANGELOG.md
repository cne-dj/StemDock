# Changelog

## 0.11 (build 9) — 2026-11-06
- Firmware 05n: new UTILITY row STEM MODE (default ON, takes effect after a restart; OFF = pure CDJ, no stem database); PAD MODE defaults to OFF
- Navigation: LOOP MODE 1x = loop mode (PAD MODE: AUTO LOOP, JUMP, HOT CUE, SLICER), 2x = stem mode, 3rd press = normal view; BACK opens Browse
- No zoom on the pad and stem pages
- Title bar and INFO list on the pad and stem pages; push in INFO selects and updates immediately
- Fixed: hang on track change
- The app writes only C2KNXSM.UPD and C2KNXSG.UPD; input: the complete Pioneer file C2KNXS.UPD 1.44

## 0.09 (build 8) — 2026-11-04
- Optional check for new versions via GitHub releases (betas count)
- MANUAL tab removed: short help (?) on the cards, link "Manual on GitHub"
- Flash and way-back notes in the firmware help
- README with screenshots and flow diagrams

## 0.08 (build 7) — 2026-11-04
- Always 4 layers, alignment when writing, settings and texts revised
- Optional check for new versions (Settings > Info, default off); BETA notice

## 0.07 (build 6) — 2026-11-04
- writes STEMS/idmap.bin automatically after every stick write (clear error if it fails)
- stem rows keep their exstem track id across incremental writes (id kept in the manifest)
- remove a track's layers from the stick (confirmation, .cst + exstem.pdb + idmap.bin)
- optional: also save single layers (Vocal/Melody/Bass/Drums as WAV) to a chosen folder, default off (SETTINGS)

## 0.06 (build 5) — 2026-10-22
- CNE palette and web typography (Space Grotesk/Inter/IBM Plex Mono), new app icon

## 0.05 (build 4) — 2026-10-16
- firmware fix: DSP gate, no stage-1, STEM only for stem tracks

## 0.04 (build 3) — 2026-10-15
- firmware version detection, umlauts, footer cleanup

## 0.03 (build 2) — 2026-10-15
- PREP: multi-track, guided layer import, song checks

## 0.02 (build 1) — 2026-10-15
- design kit: tokens, light/dark, system font, native controls; no local HTTP server, no build paths in bundle

## 0.01 (build 0) — 2026-10-15
- First versioned state: firmware patcher, PREP (layers onto the stick), separation add-on install.
