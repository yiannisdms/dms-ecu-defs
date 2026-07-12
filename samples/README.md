# Sample ROMs for the DMS ECU Editor

Real, stock (ORI) calibration binaries that match definitions in this corpus, so you
can open the DMS ECU Editor (`/admin/tune-editor`) and immediately view/edit real maps.

Source: [dmacpro91/BMW-XDFs](https://github.com/dmacpro91/BMW-XDFs) — the same repo the
BMW definitions here were converted from, so the addresses line up exactly.

## How to load one
1. Open the editor at **`/admin/tune-editor`** (admin login required).
2. **Drag the `.bin` into the editor** (or use the file picker).
3. BMW definitions have no EPK auto-detect, so **select the definition named in
   `samples.json`** (e.g. `BMW N54 N54__INA0S`) from the definition list.
4. Browse the parameter tree — timing, boost/wastegate, fuel, load maps are all live.

> Subaru / Nissan definitions in this corpus **do** carry an EPK, so if you drop a
> matching Subaru/Nissan bin the editor auto-detects the definition — no manual pick.

## Manifest
`samples.json` lists each sample: bin file, matching `definitionFile` / `definitionName`,
param count, endianness, and whether auto-detect applies.

| Sample | Engine | Params | Def |
|---|---|---|---|
| bmw-n54-ina0s-original.bin | N54 (INA0S) | 513 | BMW N54 N54__INA0S |
| bmw-n54-ikm0s-original.bin | N54 (IKM0S) | 516 | BMW N54 N54__IKM0S |

All values spot-checked against the definition before publishing (startup/oil-pressure
scalars, E85/timing/load interpolation maps read as sane engineering units).
