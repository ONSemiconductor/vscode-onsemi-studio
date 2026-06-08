# onsemi Studio
A comprehensive VS Code extension for streamlined embedded development with bare-metal CMake and Zephyr RTOS projects. Provides integrated tools for workspace setup, project management, building, debugging, and IntelliSense configuration—all within a unified development environment.

> **Note:** This extension is currently tested on Windows only. Linux and macOS support will be available in upcoming releases of the extension.

## Features

- **Guided Workspace Setup** - Interactive wizard that detects the project type (Zephyr or bare-metal CMake/SDK) and installs the matching tools automatically
- **Multi-Project Support** - Manage Zephyr RTOS and bare-metal CMake/SDK projects with individual configurations
- **Import & Create Application Wizards** - Bring in existing samples (multi-sample selection for CMake/SDK sources) or author a new application from scratch or a sample template, for both project types
- **Visual Debug Configuration** - Intuitive webview panel for creating and managing debug configurations with support for both the Eclipse CDT GDB adapter and the ASIP debug adapter (for ASIP-capable cores); direct editing of `.vscode/launch.json` is fully supported
- **Active ELF Management** - Automatic detection and selection of ELF files for debugging, with status-bar indicator and quick-pick switching
- **Advanced Build System Integration**
  - Zephyr: West workspace management, Kconfig (menuconfig/guiconfig), sysbuild, memory reports
  - CMake: Multiple configurations, presets, toolchain files, cache variables, per-configuration `sourceDir` for superbuild projects, target selection, KConfig (auto-detected from `menuconfig` / `guiconfig` targets)
- **SDK Dependency Resolution** - Projects declare SDK dependencies by name and semver in `sdk.json`; the extension resolves them against installed SDKs and exports each SDK's `envVarName` for `$env{}` substitution in `CMakePresets.json`
- **Intelligent IntelliSense** - Auto-generate configuration for clangd (default) or Microsoft C/C++ with `compile_commands.json` integration; multi-folder and sub-project aware
- **Integrated Terminal** - Pre-configured project terminals with toolchain paths, Python virtual environment activation (Zephyr and CMake), and environment variables
- **Task Providers** - Custom VS Code task definitions for build, flash, clean, configure, and debug operations
- **Task Cancellation** - Stop in-flight build / configure / clean / flash tasks via inline icon, Command Palette, or context menu
- **Context Menus** - Right-click project folders for quick access to build, debug, and configuration commands
- **Repository Management** - Add and remove SDKs / Repositories with inline icons in the Application view; configuration entries are removed without deleting files on disk

![onsemi Studio in Action](https://github.com/ONSemiconductor/vscode-onsemi-studio/raw/HEAD/docs/videos/onsemi_studio_project_view.gif)

## Documentation

For complete documentation, guides, and examples:

- [Quick Start Guide](#quick-start) - Get up and running in minutes
- [Available Commands](#available-commands) - Complete command reference
- [Configuration Guide](#configuration) - Settings and project configuration
- [Troubleshooting & FAQ](#troubleshooting--faq) - Common issues and solutions

### Quick Start

**Guided setup (recommended, both project types):**
1. **Setup Workspace**: Run `onsemi: Workspace and Tools Setup` to configure your SDK or Repository and install matching tools (the wizard detects bare-metal SDK vs. Zephyr/West and adapts its steps)
2. **Import or Create Application**: Use `onsemi: Import Application` to bring in existing samples (multi-sample for CMake/SDK), or `onsemi: Create New Application` for a new project from scratch or a sample template
3. **Build**: Right-click the project folder → `onsemi: Project: Build`
4. **Debug**: Right-click the project folder → `onsemi: Project: Debug` (the active ELF is auto-detected after build; use the status bar to switch between multiple ELFs)

**Manual setup (open an existing folder):**
1. **Open Folder**: Use `File → Open Folder` to open your project directory
2. **Configure Settings**: Open the Configure Project Settings panel (onsemi Studio Activity Bar → Configuration → Configure Settings) or edit `.vscode/settings.json` directly
3. **Build / Debug** as above

For detailed setup instructions, see the [full documentation](https://onsemiconductor.github.io/vscode-onsemi-studio/index.html).

### Available Commands

The extension provides commands for:
- **Setup**: Workspace and Tools Setup, Import Application, Create New Application (all support Zephyr and bare-metal CMake/SDK)
- **Project Operations**: Build, clean, rebuild, configure, flash, debug, stop running task
- **West / Zephyr**: Workspace initialization, board/shield management, Python environment setup, Kconfig editors
- **KConfig (CMake)**: `menuconfig` / `guiconfig` actions auto-detected from project targets
- **IntelliSense**: Provider switching (clangd default, Microsoft C/C++ as alternative), configuration regeneration
- **Debug Files**: ELF selection, scanning, and management

See [complete command reference](https://onsemiconductor.github.io/vscode-onsemi-studio/commands/index.html) for details.

### Configuration

Configure the extension through:
- **Global Settings**: Repository configurations, tool paths, certificates
- **Project Settings**: Workspace path, board, toolchain, build configurations, environment variables
- **IntelliSense Settings**: Provider selection, auto-generation options

See [configuration documentation](https://onsemiconductor.github.io/vscode-onsemi-studio/configuration/index.html) for comprehensive examples.

### Troubleshooting & FAQ

Common solutions for:
- Build failures (West not found, toolchain issues)
- IntelliSense configuration
- Debugging setup (ELF file detection, configuration creation)
- Board and certificate errors

See [troubleshooting guide](https://onsemiconductor.github.io/vscode-onsemi-studio/troubleshooting/index.html) and [FAQ](https://onsemiconductor.github.io/vscode-onsemi-studio/faq/index.html).

## Included Extensions

This extension automatically installs essential debugging and monitoring tools:

- **Eclipse CDT GDB Debug Adapter** - GDB debugging for embedded targets
- **Memory Inspector** - Memory viewing and editing during debug sessions
- **Peripheral Inspector** - SVD-based peripheral register inspection
- **Serial Monitor** - Integrated serial port communication
