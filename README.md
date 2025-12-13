# SteamLess Proton

**Windows Compatibility Tool for Linux - Run Your Windows Apps and Games**

[![Available on itch.io](https://img.shields.io/badge/Available%20on-itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://zivena.itch.io/steamless-proton)


---

## What is SteamLess Proton?

SteamLess Proton is a Windows compatibility tool for Linux. It lets you run Windows games and applications on Linux using Proton - Steam's battle-tested compatibility layer - without needing Steam running or even installed.

You get a standalone GUI to manage all your Windows apps with isolated environments per application, desktop integration, and zero terminal commands required. Each app gets real C: drives, Windows registries, and the ability to run any Windows .exe file.

**No Wine required. No Steam required.**

---

## Key Features

### Desktop Integration
- **Right-click any .exe** → "Open with SteamLess Proton" → guided setup wizard
- Create desktop shortcuts for your installed Windows apps
- Each app gets its own isolated Windows environment automatically

### No Wine/winetricks Needed
- **Sideload any .exe** directly into your apps via right-click menu
- Need DirectX? Run the actual Microsoft installer. Need .NET? Run the real redistributable.
- Install Windows dependencies just like you would on actual Windows
- No terminal commands, no winetricks scripts, no guessing

### Works With or Without Steam
- **No Steam?** SteamLess Proton auto-installs GE-Proton when you first launch
- **Steam installed?** SteamLess Proton automatically finds Steam's Proton versions for even better compatibility

### Advanced Features
- **Dual-boot save sync** - Seamlessly sync game saves between Windows and Linux with conflict detection
- **Windows version control** - Run apps as Windows XP through Windows 11
- **GameMode & MangoHUD** - Toggle performance optimizations per application
- **Custom Driveletter mapping** - Map any linux folder as a drive inside the windows emu
- **Custom theming** - KDE Plasma and GDK theme auto-fusion plus 4 built-in themes

---

## Known Limitations

- **Kernel-level anti-cheat games** (Fortnite, Valorant, Battlefield 2042, etc.) won't work. This is a top-level decision by the respective corporations to hard disable Linux in these titles - not a failure of SteamLess Proton.
- **GOG Galaxy**: Has compatibility issues with game installation and launching. **Workaround**: After installing a game through Galaxy, the installed game must be added as a separate app in SteamLess Proton to launch. Additionally, you may need to manually rename the `Dependencies-temp` folder to `Dependencies` in the GOG Galaxy installation directory. **Recommended approach**: Download GOG games as standalone offline installers instead of using the Galaxy client.

---

## Installation

**[Download from itch.io](https://zivena.itch.io/steamless-proton)**

1. Download the installer
2. Extract the zip file
3. Run `SteamLessProton-Installer`
4. Follow the setup wizard (handles all dependencies automatically)
5. Right-click any .exe file → "Open with SteamLess Proton" to get started

Designed for and tested on Arch, Mint, and Ubuntu. Will likely work on any modern 64-bit Linux distribution.

---

## System Requirements

**For SteamLess Proton itself:**
- Any modern 64-bit Linux distribution
- Minimal resources (Python + Tkinter - installer handles dependencies)

**For running Windows apps:**
- Same requirements as Proton/Steam
- Vulkan-compatible GPU recommended
- Actual requirements depend on the Windows software you're running

---

## Why SteamLess Proton Exists

After 30 years on Windows, I switched to Linux in 2024 and fell in love with finally having control over my system. But running my heavily-modded game library and professional tools (Unity, Blender) through Wine and Lutris was a nightmare.

So I figured out how to use Proton directly, built a GUI for myself, and used it daily for 6+ months. It worked so well I realized other people need this too.

**SteamLess Proton is the tool I built for myself and used every day before deciding to share it.**

---

## Commercial Software with Full Transparency

SteamLess Proton is commercial software with **auditable source code**. You can inspect exactly what it does on your system - no telemetry, no mystery binaries, no hidden behavior.

**One-time purchase. Free updates. No subscriptions. No DRM.**

See [LICENSE](LICENSE) for complete terms.

---

## Documentation & Support

Complete documentation is included with your purchase and available after installation in the `docs/` folder.

**Found a bug or have a feature request?** [Open an issue](https://github.com/Sky-Wright/SteamLess-Proton/issues) on GitHub.

---

## About the Developer

Built by an indie developer who switched to Linux in 2024 and needed this to exist. Battle-tested daily for 6+ months before release.

**Find my work:**
- [itch.io](https://zivena.itch.io) - Commercial projects
- [GitHub](https://github.com/Sky-Wright) - Open source tools, documentation, and support
- [Patreon](https://www.patreon.com/c/Sky_Wright) - Support ongoing development

---

**[Get SteamLess Proton on itch.io →](https://zivena.itch.io/steamless-proton)**
