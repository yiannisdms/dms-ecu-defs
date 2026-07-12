# Sample ROMs for the DMS ECU Editor

Real, stock calibration binaries matching definitions in this corpus, so you can open the
DMS ECU Editor (`/admin/tune-editor`) and immediately view/edit real maps.

## How to load
1. Open **`/admin/tune-editor`** (admin login).
2. **Drag the `.bin` into the editor** (or file picker).
3. **Mazda** carries an EPK → the editor **auto-detects** the definition. **BMW** has no EPK →
   pick the `definitionName` from `samples.json` manually.
4. Browse the parameter tree (lazy — click a table to open it as a grid) and edit.

## Samples (`samples.json` is the manifest)

| Sample | Platform | Tables | Auto-detect |
|---|---|---|---|
| bmw-n54-ina0s-original.bin | BMW N54 INA0S | 513 | no (pick manually) |
| bmw-n54-ikm0s-original.bin | BMW N54 IKM0S | 516 | no (pick manually) |
| mazda-nc-l831ed-stock.bin | Mazda MX-5 NC 1.8 (L8) | 507 | **yes** |
| mazda-nc-lfh9ed-stock.bin | Mazda MX-5 NC 2.0 (LF) | 507 | **yes** |
| mazda-nc-lfh9ec-stock.bin | Mazda MX-5 NC 2.0 (LF) | 507 | **yes** |
| mazda-nc-lflxec-stock.bin | Mazda MX-5 NC 2.0 (LF, 17x15) | 532 | **yes** |

BMW bins: [dmacpro91/BMW-XDFs](https://github.com/dmacpro91/BMW-XDFs). Mazda NC defs converted from
[speepsio/romdrop](https://github.com/speepsio/romdrop) EcuFlash metadata (float32 BE, full 507–532-table
calibrations); values validated cell-exact against the DMSlyzer `ncRomMaps` reader. Mazda bins are stock
factory calibrations.

> MazdaEdit-tuned NC bins are **encrypted** (entropy ~8.0) and cannot be opened at fixed offsets — only
> stock/unencrypted reads work here.

## Note: blank tables on stock ROMs
The full NC defs include RomDrop **patch-region** tables (E85/`[Flex]`, Speed Density, Alpha-N,
Fuel Target CL — ~22 of 117 maps). These only exist after applying the RomDrop patch; on a raw
**stock** ROM they are `0xFF` padding and render blank (the 3D surface needs real data). This is
expected — use the normal tables (Load Scaling, Base Timing, MAF, VVT, main fuel/spark). The full
set is kept so patched ROMs work too.
