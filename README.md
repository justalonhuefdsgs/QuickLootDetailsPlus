# QuickLootDetailsPlus

Corresponding source package for **QuickLoot Details Plus 1.0.0**.

## Download the source

[QuickLootDetailsPlus-1.0.0-source.zip](./QuickLootDetailsPlus-1.0.0-source.zip?raw=true)

This is the unchanged release source archive. It contains 434 files, including project source, UI and Papyrus inputs, dependency source archives, modified Caprica source, editable reference assets, build scripts, manifests, and the existing license and third-party notices. Extract this source ZIP before following the build instructions.

SHA-256:
```text
53b451a6ae3e9359cb9a378fb93e10d08654447ee0f81a5e4bf756588806bf53  QuickLootDetailsPlus-1.0.0-source.zip
```

## Release correspondence

The archive's `RELEASE_MANIFEST.json` matches the manifest in the runtime package `QuickLootDetailsPlus-1.0.0.zip`. All 11 listed runtime files and all 232 source-manifest entries were checked.

- Runtime ZIP SHA-256: `fa66ef2bc9cf4a38f8fdb5cf85f64ffb76de06d66d71a5eddb25d6ba62bac476`
- DLL SHA-256: `1ff0aa07517d7fae30fa95b87d47d1f5ed943b8df5d6b3a763558617c7eb4c03`
- Source manifest SHA-256: `db6283672c8090e6c2d19caaf9c079634bdfd21bf07039e761401ab4d2680878`

This release uses background opacity 0.70, with exit diagnostics and diagnostic logging disabled. Hash correspondence does not establish a clean-room or byte-for-byte reproducible build, and this source publication adds no new game-runtime validation.

## Native build

Use Windows with the existing Visual Studio C++ toolchain and required tools. The recorded defaults are MSVC 14.43.34808 and Windows SDK 10.0.26100.0. CMake, Ninja, Python, and the test tools documented in the archive are also required.

From the extracted archive directory, run:

```powershell
python .\SourceRoot\tools\prepare_deps.py
.\build-release-embedded.ps1 -BuildRoot .\build-release -UiSwf .\Editable-reference\Interface\QuickLootDetails.swf -IconSwf .\Editable-reference\Interface\QuickLootDetails_CategoryIcons.swf
```

The dependency preparation script verifies and extracts the included archives offline. Do **not** pass `-Diagnostics` or `-ExitDiagnostics` for this release configuration. The build wrapper configures the native build, builds it, and runs CTest. Its `-VSPath`, `-Toolset`, and `-SDKVersion` parameters can select an existing installation.

Read `SOURCE_PACKAGE_README.txt` first. For Papyrus, UI regeneration, external imports, and tool requirements, also read `BUILD_138_AND_PEX_137.txt`, `ARTIFACT_INPUTS_138.txt`, and the documentation under `SourceRoot`. Some older candidate documents describe diagnostics-enabled builds; the release wrapper with both diagnostic switches omitted is the configuration for this package.

Skyrim, provider binaries, external SDKs, and proprietary game imports are not supplied.

## Licensing and notices

The archive preserves the existing terms without adding a new license grant.

- `PROJECT_LICENSE_138.md`: project C++, AS2, Papyrus, tests, and build scripts are GPL-3.0-or-later with the included additional permissions.
- `SourceRoot/COPYING.txt` and `SourceRoot/EXCEPTIONS.md`: complete GPL text and project exceptions.
- `SourceRoot/THIRD_PARTY.md`, `SourceRoot/NOTICE.md`, `SourceRoot/licenses/`, and the component source trees: third-party notices and licenses.
- `LICENSE_CONDITIONS_138.txt`: recorded licensing and corresponding-source qualifications.

Third-party components retain their own licenses. The separate reuse terms for the independently authored 061 artwork are not clarified by this publication. Historical candidate notes are retained inside the unchanged archive.
