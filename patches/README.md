# RomDrop feature patches (archive)

The 103 RomDrop `.patch` files for the Mazda MX-5 NC calibrations in this corpus, one per ROM
(`mazda-nc-<id>-romdrop.patch`), mapped to their definition in `patches.json`.

## What they do
Each patch unlocks RomDrop feature code on a **stock** ROM: E85/flex-fuel, Speed Density, Alpha-N,
and extra spark/fuel tables (the `[Flex]*` / Speed Density / Alpha-N maps in the full defs, which
live in the `0xf0000+` region and read blank on an unpatched stock ROM).

## How to apply (per ROM) — the safe path
1. Read your stock ROM with the official **romdrop.exe** (menu `R`) — Tactrix Openport, Windows.
2. Apply the patch: **romdrop.exe menu `P | Patch Stock ROM`** → generates a patched calibration.
3. Load the **patched** `.bin` in the DMS editor → the previously-blank feature tables are now
   editable. (The patch adds the *code*; you fill the table *values* — they start empty by design.)

## Why patching isn't reimplemented in the editor
RomDrop's patch algorithm lives in the closed `romdrop.exe` and is checksum-verified (`romdrop.crc`).
It is **not** a simple byte-overlay (verified: the patch file itself is ~98% zero and leaves feature
tables at `0xFF`). Reimplementing it unverified could corrupt an ECU, so we archive the patches and
defer application to romdrop.exe. An in-editor patch button would require the verified algorithm + a
fork rebuild.
