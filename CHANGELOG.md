# onsemi Studio Change Log

## [0.5.17] - 2026-07

### Fixed

- Fixed ZIP extraction hanging indefinitely on recent VS Code versions by upgrading `yauzl` (3.3.0 → 3.4.0) — caused by a Node.js stream compatibility bug in the third-party library ([yauzl#176](https://github.com/thejoshwolfe/yauzl/issues/176))

## [0.5.15] - 2026-06

### Security

- Removed global `NODE_TLS_REJECT_UNAUTHORIZED = '0'` — TLS certificate verification is no longer disabled system-wide
- Improved `onsemi.certificatePath` setting to trust a custom CA certificate for HTTPS requests, Git SSL verification (`GIT_SSL_CAINFO`), and pip installs (`--cert`)

### Added

- **Quick Start View** — enabled by default to guide users through workspace setup, import, and application creation
- **CMake Superbuild / Multi-Project Support** — automatic detection of superbuild patterns, per-configuration `sourceDir` overrides, sub-project tree view, and KConfig integration (`menuconfig`/`guiconfig` commands, `prj.conf` detection)
- **SDK Dependency Resolution** — `sdk.json` manifest with `sdkId`, `sdkVersion`, and `sdkDependencies`; semver range matching; automatic metadata population on repository add; Quick Pick when multiple repos share an `sdkId`
- **CMakePresets.json Import** — preset inheritance resolution, `$env{}` macro expansion via SDK maps, `${sourceDir}`/`${presetName}` substitution, and automatic build configuration generation
- **Multi-App Batch Import** — select and import multiple sample applications at once for both Zephyr and bare-metal CMake / SDK projects; for Zephyr, every selected sample is paired with the board chosen in the wizard
- **Repo-Only Sample Filter** (Zephyr) — toggle in the Import / Create Application sample picker to hide upstream Zephyr samples and show only samples discovered under the selected repository's `samples/` folder
- **Multi-Folder clangd IntelliSense** — status bar folder/sub-project selection, `*_clangd.json` sidecar configs, VS Code variable resolution, and automatic language server restart on switch
- **Per-Project Task Cancellation** — stop in-flight tasks via inline icon, Command Palette, or context menu; status bar spinner; tree view running state
- **Debug Tools** — GDB/J-Link detection tree section with version and install links; debug configuration provider that injects tool paths and validates sessions; Quick Pick launcher for existing debug configurations; Zephyr task runner (`west flash`) also picks up auto-detected J-Link so flashing works when the tools are installed but not on the system PATH
- **Repository Management** — `RemoveRepository` command with confirmation dialog; add/remove SDKs with inline icons
- **Resumable Downloads** — `Range` header support with up to 5 retries on `ECONNRESET`
- Python environment setup and package install commands from Application view context menu

### Improved

- **Debug support** — new Quick Pick to launch existing debug configurations directly; tool path injection into debug adapter environment; port reachability checks for GDB server
- **ELF file management** — deferred initial scan to prevent race conditions; consolidated glob patterns; scans both workspace folders and per-configuration `buildDir` paths; queued concurrent scans; improved matching with project-name priority scoring; correct workspace folder attribution for nested layouts
- **IntelliSense** — clangd uses absolute paths for `--compile-commands-dir`; only promotes real custom clangd paths to workspace settings; Microsoft C/C++ support for multiple sub-project compilation databases; graceful fallback for non-C/C++ folders; active language server restart on sub-project switch
- **Import/Create wizards** — support both Zephyr and bare-metal CMake/SDK projects
- **Tree view** — non-buildable container repos hidden from Projects view; superbuild sub-project build directory scanning; colorized icons for debug tools and project items

### Fixed
- ELF files from sample builds correctly attributed to the sample's workspace folder
- Auto-clean stale `CMakeCache.txt` when `CMAKE_HOME_DIRECTORY` does not match current source directory (project moved/renamed)

## [0.4.6] - 2026-02

Initial public release of onsemi Studio for VS Code.

**Note:** Currently tested on Windows only. Linux and macOS support will be available in upcoming releases.
