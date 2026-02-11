# onsemi Studio
A comprehensive VS Code extension for streamlined embedded development with bare-metal CMake and Zephyr RTOS projects. Provides integrated tools for workspace setup, project management, building, debugging, and IntelliSense configuration—all within a unified development environment.

> **Note:** This extension is currently tested on Windows only. Linux and macOS support will be available in upcoming releases of the extension.

## Features

- **Guided Workspace Setup** - Interactive wizard for Zephyr repository configuration and automated tool installation
- **Multi-Project Support** - Manage Zephyr RTOS and bare-metal CMake projects with individual configurations
- **Visual Debug Configuration** - Intuitive webview panel for creating and managing debug configurations with support for GDB and ASIP adapters
- **Active ELF Management** - Automatic detection and selection of ELF files for debugging with status bar integration
- **Advanced Build System Integration**
  - Zephyr: West workspace management, Kconfig (menuconfig/guiconfig), sysbuild, memory reports
  - CMake: Multiple configurations, presets, toolchain files, cache variables, target selection
- **Intelligent IntelliSense** - Auto-generate configuration for clangd or Microsoft C/C++ with compile commands integration
- **Integrated Terminal** - Pre-configured project terminals with toolchain paths and environment variables
- **Task Providers** - Custom VS Code task definitions for build, flash, clean, and debug operations
- **Context Menus** - Right-click project folders for quick access to build, debug, and configuration commands
- **Repository Management** - Multi-repository support with per-repository tool and settings management

![onsemi Studio in Action](https://github.com/ONSemiconductor/vscode-onsemi-studio/raw/HEAD/docs/videos/onsemi_studio_project_view.gif)

## Documentation

For complete documentation, guides, and examples:

- [Quick Start Guide](#quick-start) - Get up and running in minutes
- [Available Commands](#available-commands) - Complete command reference
- [Configuration Guide](#configuration) - Settings and project configuration
- [Troubleshooting & FAQ](#troubleshooting--faq) - Common issues and solutions

### Quick Start

**For Zephyr Projects:**
1. **Setup Workspace**: Run `onsemi: Workspace and Tools Setup` to configure your workspace and install tools
2. **Import or Create Project**: Use `onsemi: Import Application` to add a sample, or `onsemi: Create New Application` for a new project
3. **Build**: Right-click project folder → `onsemi: Project: Build`
4. **Debug**: Right-click project folder → `onsemi: Project: Debug` (ELF auto-detected after build)

**For CMake Projects:**
1. **Open Folder**: Use `File → Open Folder` in VS Code to open your CMake project
2. **Configure Settings**: Use the Configure Settings Panel UI (onsemi Studio Activity Bar → Configuration → Configuration Settings) or manually edit `.vscode/settings.json` with toolchain and build configurations
3. **Build**: Right-click project folder → `onsemi: Project: Build`
4. **Debug**: Right-click project folder → `onsemi: Project: Debug`

For detailed setup instructions, see the [full documentation](https://onsemiconductor.github.io/vscode-onsemi-studio/index.html).

### Available Commands

The extension provides commands for:
- **Setup** (Zephyr only): Workspace configuration, application import/creation
- **Project Operations**: Build, clean, rebuild, configure, flash, debug
- **West/Zephyr**: Workspace initialization, board/shield management, Python environment setup, Kconfig editors
- **IntelliSense**: Provider switching, configuration regeneration
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
