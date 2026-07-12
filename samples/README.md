# Sample ROMs for the DMS ECU Editor

Real, stock calibration binaries that match definitions in this corpus, so you can open
the DMS ECU Editor (`/admin/tune-editor`) and immediately view/edit real maps.

## How to load
1. Open **`/admin/tune-editor`** (admin login).
2. **Drag the `.bin` into the editor** (or file picker).
3. **Mazda / Subaru / Nissan** carry an EPK → the editor **auto-detects** the definition.
   **BMW** has no EPK → pick the `definitionName` from `samples.json` manually.
4. Browse the parameter tree and edit.

## Samples (`samples.json` is the manifest)

| Sample | Platform | Auto-detect | Def |
|---|---|---|---|
| bmw-n54-ina0s-original.bin | BMW N54 INA0S | no (pick manually) | BMW N54 N54__INA0S |
| bmw-n54-ikm0s-original.bin | BMW N54 IKM0S | no (pick manually) | BMW N54 N54__IKM0S |
| mazda-nc-lfh9ed-stock.bin | Mazda MX-5 NC (LF) | **yes** | Mazda MX-5 NC LFH9ED |
| mazda-nc-l831ed-stock.bin | Mazda MX-5 NC (LF) | **yes** | Mazda MX-5 NC L831ED |

BMW bins: [dmacpro91/BMW-XDFs](https://github.com/dmacpro91/BMW-XDFs) (same source as the defs).
Mazda NC defs: converted from the RomDrop EcuFlash defs (float32 BE — MAF transfer fn, Load
Scaling RPM×Load, injector PW / global fuel scalars); every cell validated against the DMSlyzer
`ncRomMaps` reader before publishing. Mazda bins are stock factory calibrations.

> Note: MazdaEdit-tuned NC bins are **encrypted** (entropy ~8.0, no padding) and cannot be
> opened at fixed offsets — only stock/unencrypted reads work here.
