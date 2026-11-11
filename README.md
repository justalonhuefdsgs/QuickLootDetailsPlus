# QuickLootDetailsPlus

Corresponding source packages for **QuickLoot Details Plus**.

## Optional ESL source: 1.0.1

[QuickLootDetailsPlus-1.0.1-ESL-source.zip](./QuickLootDetailsPlus-1.0.1-ESL-source.zip?raw=true)

This is the corresponding source for the optional ESL-flagged 1.0.1 package. It preserves all 3,625 entries of the regular 1.0.1 source archive and adds `ESL_VARIANT/` with the flag-only conversion script, tested ESP reference, and variant documentation. It is source code, not a mod-manager installation package.

SHA-256:
```text
4dbc2ccd7cd75356dd7b9af27f3bb718f906988cbf4305697e3e9baaeec735b3  QuickLootDetailsPlus-1.0.1-ESL-source.zip
```

### ESL conversion and build

Follow the regular 1.0.1 build instructions below and read `ESL_VARIANT/README.txt`. From the extracted source archive directory, generate the ESL ESP with:

```powershell
python .\ESL_VARIANT\apply-esl-flag.py .\Editable-reference\QuickLootDetails.esp .\QuickLootDetails.esp
```

The output file must not already exist. The script validates the exact input and output hashes and writes a separate file without changing the original. Use the resulting `QuickLootDetails.esp` in the packaged Data root after the regular build/package steps. The tested result is also included in `ESL_VARIANT/Reference/`.

Only the ESL flag changes. The filename, FormIDs and SEQ data are preserved; no FormID compaction or renumbering was performed. The DLL, scripts, UI and configuration files are unchanged from regular 1.0.1. The original source manifest remains unchanged. The conversion was checked against the tested ESP; no new clean rebuild or byte-for-byte build reproducibility is claimed.

### ESL testing and installation cautions

New-save tests passed on Skyrim 1.5.97 and 1.6.1170 for MCM, QuickLoot and world detail cards, settings changes, and save/reload. Migration from the regular ESP was confirmed on 1.5.97 only. Migration on 1.6.1170 and other versions, controller operation, long play sessions and every save/load-order or provider combination remain unverified.

The runtime is an optional alternative to regular 1.0.1, not a required update or a 1.0.2 release. Use only one QLDP runtime package at a time. Back up saves and the mod-manager profile before switching, retain a pre-switch save, and save to a new slot. To roll back, restore the regular package and load the pre-switch save. New games are recommended; there is no need to switch an existing working regular installation. Do not rename the plugin or compact its FormIDs.

The existing licensing and third-party notices remain applicable. See the source archive and the licensing section below.

## Latest source: 1.0.1

[QuickLootDetailsPlus-1.0.1source.zip](./QuickLootDetailsPlus-1.0.1source.zip?raw=true)

Extract this source ZIP before following the build instructions.

SHA-256:
```text
1399c9fb999e94898ea37a0144be1ea680a38bba608762f091bff7d24db4076a  QuickLootDetailsPlus-1.0.1source.zip
```

### Native build for 1.0.1

Use Windows with an existing Visual Studio C++ toolchain and the tools required by the documentation inside the archive. From the extracted archive directory, run these steps in order:

```powershell
python .\reconstruct-dependencies.py
python .\SourceRoot\tools\prepare_deps.py
python .\SourceRoot\tools\source_manifest.py --root .\SourceRoot --check
.\build-release-embedded.ps1 -BuildRoot .\build-release -UiSwf .\Editable-reference\Interface\QuickLootDetails.swf -IconSwf .\Editable-reference\Interface\QuickLootDetails_CategoryIcons.swf
```

The reconstruction step must run before dependency preparation. It recreates the historical dependency ZIPs from the included expanded files and verifies their original hashes. A different Python/zlib version may fail to recreate identical ZIP bytes; do not bypass a hash mismatch. Do **not** pass `-Diagnostics` or `-ExitDiagnostics` for the release build. Read the source-package and build documentation included in the archive for tool requirements, Papyrus, UI regeneration, and external imports.

### Verification scope for 1.0.1

The release label is 1.0.1; the DLL's internal version remains 0.1.20.0.

Runtime testing was performed with:

- Skyrim 1.5.97 and QuickLoot IE 4.1.2.
- Skyrim 1.6.1170 and QuickLoot IE 4.1.3.

The Skyrim 1.5.97 / QuickLoot IE 4.1.2 test was completed after the source-package README was written. The tested DLL and SWF hashes matched the 1.0.1 candidate, and all three user-observed checks were reported as passing. This newer result supplements the testing scope recorded inside the unchanged archive.

Other Skyrim or provider versions and controller operation remain unverified. A clean rebuild from the distributed source package has not been verified. The source archive hash does not establish a clean-room or byte-for-byte reproducible build.

## Previous source: 1.0.0

The 1.0.0 archive and its original verification details are retained below.

Corresponding source package for **QuickLoot Details Plus 1.0.0**.

### Download the source

[QuickLootDetailsPlus-1.0.0-source.zip](./QuickLootDetailsPlus-1.0.0-source.zip?raw=true)

This is the unchanged release source archive. It contains 434 files, including project source, UI and Papyrus inputs, dependency source archives, modified Caprica source, editable reference assets, build scripts, manifests, and the existing license and third-party notices. Extract this source ZIP before following the build instructions.

SHA-256:
```text
53b451a6ae3e9359cb9a378fb93e10d08654447ee0f81a5e4bf756588806bf53  QuickLootDetailsPlus-1.0.0-source.zip
```

### Release correspondence

The archive's `RELEASE_MANIFEST.json` matches the manifest in the runtime package `QuickLootDetailsPlus-1.0.0.zip`. All 11 listed runtime files and all 232 source-manifest entries were checked.

- Runtime ZIP SHA-256: `fa66ef2bc9cf4a38f8fdb5cf85f64ffb76de06d66d71a5eddb25d6ba62bac476`
- DLL SHA-256: `1ff0aa07517d7fae30fa95b87d47d1f5ed943b8df5d6b3a763558617c7eb4c03`
- Source manifest SHA-256: `db6283672c8090e6c2d19caaf9c079634bdfd21bf07039e761401ab4d2680878`

This release uses background opacity 0.70, with exit diagnostics and diagnostic logging disabled. Hash correspondence does not establish a clean-room or byte-for-byte reproducible build, and this source publication adds no new game-runtime validation.

### Native build

Use Windows with the existing Visual Studio C++ toolchain and required tools. The recorded defaults are MSVC 14.43.34808 and Windows SDK 10.0.26100.0. CMake, Ninja, Python, and the test tools documented in the archive are also required.

From the extracted archive directory, run:

```powershell
python .\SourceRoot\tools\prepare_deps.py
.\build-release-embedded.ps1 -BuildRoot .\build-release -UiSwf .\Editable-reference\Interface\QuickLootDetails.swf -IconSwf .\Editable-reference\Interface\QuickLootDetails_CategoryIcons.swf
```

The dependency preparation script verifies and extracts the included archives offline. Do **not** pass `-Diagnostics` or `-ExitDiagnostics` for this release configuration. The build wrapper configures the native build, builds it, and runs CTest. Its `-VSPath`, `-Toolset`, and `-SDKVersion` parameters can select an existing installation.

Read `SOURCE_PACKAGE_README.txt` first. For Papyrus, UI regeneration, external imports, and tool requirements, also read `BUILD_138_AND_PEX_137.txt`, `ARTIFACT_INPUTS_138.txt`, and the documentation under `SourceRoot`. Some older candidate documents describe diagnostics-enabled builds; the release wrapper with both diagnostic switches omitted is the configuration for this package.

Skyrim, provider binaries, external SDKs, and proprietary game imports are not supplied.

### Licensing and notices

The archive preserves the existing terms without adding a new license grant.

- `PROJECT_LICENSE_138.md`: project C++, AS2, Papyrus, tests, and build scripts are GPL-3.0-or-later with the included additional permissions.
- `SourceRoot/COPYING.txt` and `SourceRoot/EXCEPTIONS.md`: complete GPL text and project exceptions.
- `SourceRoot/THIRD_PARTY.md`, `SourceRoot/NOTICE.md`, `SourceRoot/licenses/`, and the component source trees: third-party notices and licenses.
- `LICENSE_CONDITIONS_138.txt`: recorded licensing and corresponding-source qualifications.

Third-party components retain their own licenses. The separate reuse terms for the independently authored 061 artwork are not clarified by this publication. Historical candidate notes are retained inside the unchanged archive.
