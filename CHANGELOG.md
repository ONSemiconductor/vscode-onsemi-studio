# onsemi Studio Change Log

## [0.6.19] - 2026-09

### Fixed

- **Toolchain install failures on Windows** — Installing an SDK toolchain (e.g. the Zephyr SDK) no longer fails intermittently when antivirus or another process briefly locks files during extraction, or when a previous partial install is left behind.
- **Extension activation failure** — Fixed an issue that prevented the extension from activating on some systems.
- **Duplicate repository entries from drive-letter casing** — Adding the same folder with different drive-letter casing (`c:\` vs `C:\`) no longer creates two entries; existing duplicates are merged automatically.
- **Setup no longer aborts on inaccessible toolchains** — When an access-restricted toolchain can't be downloaded, it is skipped and the remaining tools still install. The Finish step lists what was skipped so it can be installed later.
- **Duplicate tool entries** — A tool whose version changed is no longer listed twice; each tool keeps a single entry.
- **Invalid certificate path aborting West install** — A misconfigured `onsemi.certificatePath` (a folder or missing file) is now skipped with a log message instead of failing workspace setup.
- **Package installs under uv** — West/requirements installs no longer fail in uv-managed environments; the custom CA is applied correctly and `onsemi.allowInsecureTls` is honored.
- **Stale CMake cache on configuration switch** — Switching build configurations that share a build directory no longer reuses the previous configuration's cache, so a manual clean build is no longer required.

### Added

- **J-Link minimum-version check** — onsemi Studio now warns (non-blocking) when the installed SEGGER J-Link is missing or older than the version your SDK recommends, with a shortcut to the download page. Debugging and flashing are never blocked.
- **Repository Tools panel** — A new panel lists each registered repository and its configured tools (version, source, and whether the install path exists on disk), with inline editing, adding, and removing of tool paths.
- **Windows certificate-store support for Git/West** — New `onsemi.git.useWindowsSchannel` setting (on by default, Windows-only) allows Git and West to validate server certificates against the Windows certificate store for improved compatibility in enterprise environments.
- **Board-aware sample filtering (Zephyr)** — The Import/Create Application sample picker can filter samples to those compatible with the selected board, with a **Compatible / All** toggle, a green **Recommended** badge, and an amber **Toolchain incompatible** warning.
- **Zephyr snippets** — Build configurations can now select Zephyr snippets (passed to `west build` as `-S`), with a **Snippets** multi-select in Configure Settings and a `West: List Snippets` command.
- **NVM Image Tool panel** — A new panel configures and launches the NVM image tool (`nvmi`). It is shown only for SDKs that declare NVM support.
- **Remove Folder from Workspace** — A new project context-menu action removes a project folder from the current VS Code workspace.
- **Cancel Repository Setup** — You can now cancel an in-progress clone/download/extract during workspace setup and return cleanly to the form.
- **Automatic CMakePresets.json sync** — Build configurations update automatically when `CMakePresets.json` changes, including support for `include` directives and `$penv{}` macros.

### Changed

- **ASIP (lpdsp32) debug configuration** — The ASIP debug configuration fields now match the current SDK (`gdbforasipArgs` and a structured `debug_client_options` with host/port/core). Re-save existing ASIP configurations from the Debug Configuration panel to update them.

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