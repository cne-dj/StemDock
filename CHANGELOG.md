# Changelog

## 0.9 (build 8) — 2026-11-04
- Optionale Pruefung auf neue Versionen ueber die GitHub-Releases (Betas zaehlen mit)
- MANUAL-Reiter entfernt: Kurzhilfe (?) auf den Karten, Link "Anleitung auf GitHub"
- Flash- und Rueckweg-Hinweise in der Firmware-Hilfe
- README mit Screenshots und Schemata

## 0.8 (build 7) — 2026-11-04
- Immer 4 Layer, Ausrichtung beim Schreiben, Einstellungen und Texte ueberarbeitet
- Optionale Pruefung auf neue Versionen (Einstellungen > Info, Standard aus); BETA-Hinweis

## 0.7 (build 6) — 2026-11-04
- writes STEMS/idmap.bin automatically after every stick write (clear error if it fails)
- stem rows keep their exstem track id across incremental writes (id kept in the manifest)
- remove a track's layers from the stick (confirmation, .cst + exstem.pdb + idmap.bin)
- optional: also save single layers (Vocal/Melody/Bass/Drums as WAV) to a chosen folder, default off (SETTINGS)

## 0.6 (build 5) — 2026-10-22
- CNE palette and web typography (Space Grotesk/Inter/IBM Plex Mono), new app icon

## 0.5 (build 4) — 2026-10-16
- firmware fix: DSP gate, no stage-1, STEM only for stem tracks

## 0.4 (build 3) — 2026-10-15
- firmware version detection, umlauts, footer cleanup

## 0.3 (build 2) — 2026-10-15
- PREP: multi-track, guided layer import, song checks

## 0.2 (build 1) — 2026-10-15
- design kit: tokens, light/dark, system font, native controls; no local HTTP server, no build paths in bundle

## 0.1 (build 0) — 2026-10-15
- First versioned state: firmware patcher, PREP (layers onto the stick), separation add-on install.
