# SteamLess Proton

**Windows Compatibility Tool for Linux - Run Your Windows Apps and Games**

---

## What is SteamLess Proton?

SteamLess Proton is a professional Windows compatibility solution for Linux that leverages Steam's battle-tested Proton technology to run Windows applications without requiring Steam itself. Unlike other compatibility tools that focus solely on gaming, SteamLess provides enterprise-grade application isolation, seamless desktop integration, and comprehensive dependency management - all through an intuitive GUI that eliminates terminal commands entirely.

Each Windows application runs in its own isolated environment with real C: drives, Windows registries, and full access to the Windows ecosystem. Whether you're a gamer wanting to play Battle.net titles, a developer using Windows-only tools, or a professional running business software, SteamLess makes Windows compatibility on Linux as simple as installing software on Windows itself.

**No Wine required. No Steam required. No terminal commands required.**

---

## Key Features

### Desktop Integration
- **Right-click any .exe** → "Open with SteamLess Proton" → guided setup wizard that handles everything automatically
- Create professional desktop shortcuts and start menu entries for seamless Linux integration
- Each app gets its own isolated Windows environment, preventing conflicts between applications

### No Wine/winetricks Needed
- **Sideload any .exe** directly into your apps via right-click menu - no more hunting for dependencies
- Need DirectX for that old game? Run the actual Microsoft installer. Need .NET for business software? Install the real redistributable.
- Install Windows dependencies just like you would on actual Windows - SteamLess handles the complexity
- Zero terminal commands, no winetricks scripts, no compatibility layer guesswork

### Works With or Without Steam
- **No Steam installed?** SteamLess automatically downloads and configures GE-Proton for optimal performance
- **Steam installed?** SteamLess intelligently detects and utilizes Steam's Proton versions for maximum compatibility
- Automatic fallback handling ensures you always have working Proton, regardless of your setup

### Advanced Features
- **Dual-boot save sync** - Seamlessly sync game saves between Windows and Linux partitions with automatic conflict detection and resolution
- **Windows version control** - Run legacy applications as Windows XP, or modern apps as Windows 11 - per application
- **GameMode & MangoHUD integration** - Toggle performance optimizations and real-time FPS monitoring per application
- **Custom environment variables** - Full control over Linux environment variables (DRI_PRIME for GPU switching, VK_ICD_FILENAMES for Vulkan, etc.) to solve edge cases
- **Custom launch arguments** - Pass command-line arguments directly to Windows executables for advanced configuration
- **Custom Driveletter mapping** - Map any Linux directory as Windows drive letters (Z: for home, network shares as N:, etc.)
- **Custom theming** - Automatic KDE Plasma + GTK theme fusion plus 4 built-in professional themes

### KNOWN LIMITATIONS
- **Kernel-level anti-cheat games** (Fortnite, Valorant, Battlefield 2042, etc.) are deliberately disabled on Linux by their developers as an anti-piracy measure. This is a corporate decision, not a technical limitation of SteamLess.
- **Microsoft's Ecosystem Lock-in**: Microsoft actively pays partners to prevent Linux compatibility, artificially maintaining Windows market dominance. SteamLess works around this where possible.
- **GOG Galaxy**: The launcher installs and runs, but has issues installing games directly. **Solution**: Use GOG's offline installers instead - they work perfectly with SteamLess Proton.

---

## Installation

**[Download from itch.io](https://zivena.itch.io/steamless-proton)**

### Professional GUI Installer
SteamLess comes with a sophisticated Windows-style executable installer that handles everything automatically—think installing software on Windows: no terminal commands, no dependency hunting, just professional setup that "just works."

**What It Does:**
- **Embedded Application** - The entire SteamLess app is bundled in the executable, no separate downloads needed
- **Theme Fusion Detection** - Automatically detects and matches your KDE Plasma + GTK theme for seamless integration
- **Multi-Step Wizard** - Professional installation wizard with welcome screen, options selection, and progress monitoring
- **Desktop Integration** - Sets up right-click context menus, desktop shortcuts, and file associations
- **Global Command Access** - Installs system-wide 'steamless' command for terminal usage
- **Status Monitoring** - Real-time installation progress with error handling and rollback capabilities
- **Virtual Environment Setup** - Creates isolated Python environment to avoid system conflicts

**Dependency Management:**
The installer checks your system and installs everything required for Proton to work properly. No more common compatibility issues:

- **Python Environment**: Python 3.6+, Tkinter for the GUI, venv so SteamLess doesn't mess with your system Python
- **System Tools**: rsync for syncing those precious game saves, curl for downloading GE-Proton and updates
- **32-bit Libraries**: Full multilib setup (lib32-glibc, lib32-freetype2, fontconfig, etc.) because 32-bit games aren't dead yet
- **Wine/Proton Libraries**: All the 32-bit dependencies Proton needs to run Windows stuff without breaking
- **Steam Runtime**: Uses proper containerization for Steam Proton execution
- **Cross-Distribution**: Adapts to whatever package manager you're using (pacman on Arch, apt on Ubuntu, etc.)

**Installation Process:**
1. **Optional but Recommended:** Install xterm for the best installer experience: `sudo pacman -S xterm` (Arch) or `sudo apt install xterm` (Ubuntu/Debian)
2. Download the `SteamLess-Installer` executable from itch.io
3. Run the executable
4. Choose installation options through the GUI wizard
5. **Terminal Integration:** The installer uses an integrated xterm window to handle parts that must be installed via terminal (dependency installation, system integration)
6. **Password Entry:** You'll need to enter your sudo password in the xterm (or external terminal if xterm isn't available) when installing system dependencies - this is standard Linux package management
7. **Transparency:** The terminal shows everything it's doing in real-time - no hidden commands or mystery operations
8. Desktop integration is configured for immediate use

**Why Terminal Integration?**
Some parts of Linux system setup (like installing packages or setting up desktop integration) absolutely require terminal commands. Rather than hiding this complexity, SteamLess makes it as simple as possible:
- **Integrated xterm:** Opens automatically within the installer GUI
- **Clear instructions:** Tells you exactly what it's doing and why
- **Your control:** You see every command as it runs, and can cancel anytime
- **Fallback support:** Works with your existing terminal if xterm isn't installed

Designed for and tested on Arch, Mint, and Ubuntu. Will likely work on any modern 64-bit Linux distribution.

**System Requirements:**
- **For the installer itself:** Any modern Linux distribution
- **For running Windows apps:** Same requirements as Proton/Steam (Vulkan GPU recommended)

## Technical Architecture

SteamLess Proton is an orchestration system that manages multiple compatibility layers, isolated environments, and cross-platform integration. People keep asking "why not just use Lutris?" Here's the technical difference:

**Modular Component Architecture:**
- **launcher.py** (728-799): Core orchestration engine handling dual Proton execution paths
- **proton_manager.py**: Proton version detection, download, and environment setup
- **app_management.py**: Isolated Wine prefix management with per-app configurations
- **config.py**: JSON-based persistence with validation and migration support
- **data_sync.py**: Rsync-based save synchronization with NTFS detection and conflict resolution

**Execution Flow:**
1. **App Launch**: User selects app → launcher.py resolves Proton version and prefix path
2. **Environment Setup**: proton_manager.py configures STEAM_COMPAT_* variables based on Proton type
3. **Prefix Management**: app_management.py ensures isolated Wine environment with custom drive mappings
4. **Dependency Injection**: Sideloaded executables run in the app's isolated context
5. **Save Sync**: data_sync.py handles cross-platform save migration with timestamp comparison

**Custom Proton Orchestration:**
- **Dual execution paths**: GE-Proton runs direct, Steam Proton uses full containerization
- **Dynamic environment variables**: Different `STEAM_COMPAT_CLIENT_INSTALL_PATH` for each Proton type (fixes BDO and other Steam-dependent games)
- **GE-Proton drive mapping monitor**: Re-applies mappings after wineboot overwrites them
- **Steam-dependent game support**: Detects Proton type and sets correct environment variables (launcher.py:640-653)

**Isolation & Security:**
- **Per-App Prefixes**: Each application gets its own Wine environment (C: drive, registry, etc.)
- **Drive Mapping**: Linux directories mounted as Windows drive letters (Z: for home, custom mappings)
- **Environment Containment**: Custom environment variables per application without system pollution
- **Dependency Scoping**: Windows runtimes and libraries isolated to prevent conflicts

**Cross-Platform Integration:**
- **Desktop Integration**: MIME types, right-click menus, and shortcuts via steamless.desktop
- **Theme Fusion**: Automatic detection of KDE Plasma + GTK themes for native appearance
- **Package Manager Adaptation**: Universal installer supporting pacman, apt, dnf, and zypper
- **File Association**: .exe files open with SteamLess wizard for seamless onboarding


## Why SteamLess Proton Exists

After 30 years on Windows, I switched to Linux in 2024 and fell in love with finally having control over my system. But I quickly discovered that "Linux gaming" was mostly just Steam gaming - the vast majority of Windows software remained completely inaccessible. My heavily-modded Skyrim setup, professional Blender workflow, and business applications were suddenly broken.

Wine and Lutris promised compatibility but delivered frustration: dependency hell, broken installations, and endless tinkering. I spent weeks trying to get basic applications running, only to have them break with the next update.

So I figured out how to use Proton directly - Steam's battle-tested compatibility layer that makes thousands of Windows games work on Linux. I built a GUI for myself that handled all the complexity: automatic Proton management, isolated environments, dependency injection, and seamless desktop integration.

It worked so well I realized other people needed this too. SteamLess isn't just another compatibility tool - it's a professional solution that enables the use of the entire Windows software ecosystem to Linux, making Windows compatibility as simple as installing software on Windows itself.

**SteamLess Proton is the tool I built for myself and used every day before deciding to share it.**

Built by Sky Wright, a 31-year-old trans woman and indie developer who switched to Linux in 2024 after 26 years on Windows. Frustrated with the complexity of running Windows apps on Linux, I built SteamLess Proton for myself while surviving on minimal resources. Battle-tested daily for 6+ months, it became the tool I needed to exist.

**Commercial Software with Full Transparency:**
SteamLess Proton is commercial software with **auditable source code**. You can inspect exactly what it does on your system - no telemetry, no mystery binaries, no hidden behavior.

**One-time purchase. Free updates. No subscriptions. No DRM.**

**Professional Documentation & Development:**
Every aspect of SteamLess Proton, from the code to this documentation, is crafted with the same attention to detail. The comprehensive technical explanations, real-world testing results, and transparent development process demonstrate a commitment to quality that goes beyond "vibe coding."

See [LICENSE](LICENSE) for complete terms.

---

**[Get SteamLess Proton on itch.io →](https://zivena.itch.io/steamless-proton)**
