# SteamLess Proton

**Advanced Proton Orchestrator for Linux**  
**Professional GUI • True Isolation • Zero Terminal Required**

Run **any** Windows .exe — Epic, Battle.net, GOG Galaxy, EA App, heavily modded Skyrim, Blender workflows, legacy apps — exactly like on Windows, but with superior Linux control and isolation.

Built by a 25-year Windows veteran who became a Linux power user solving the exact frustrations this tool eliminates.

### Highlighted Features

- **Right-click .exe → run with SteamLess → guided wizard → perfect desktop integration**  
  Each app runs in its own isolated environment with real C: drives and registries.

- **Independent dual-path Proton engine — does NOT use UMU**  
  Ironically, I didn’t know UMU existed until very recently — to build this I reverse-engineered Steam’s Proton usage itself. This app does not utilize any facet of UMU.  
  SteamLess operates exactly as Steam does, just outside of Steam with customizable paths.  
  Custom: direct low-overhead GE-Proton + full Steam Runtime containerization-(when Steam is present and SteamLess detects Steam's Proton versions are installed).  
  Includes toggle per app to select which Proton version to launch with (supports custom Proton builds).

- **Professional GUI Installer**  
  Windows-style multi-step wizard that handles everything: auto theme fusion, installs deps, sets up right-click menus/shortcuts/associations, transparent xterm auditing (see every sudo command live), venv isolation, rollback support — a true "Windows installer for Linux".

- **Effortless GUI sideload**  
  Right-click any app in the GUI → "Sideload EXE" (any .exe/.bat/.msi supported) → default file browser opens → pick **any** executable from **anywhere** → it runs directly inside that app’s dedicated Proton prefix.  
  No manual file copying • No protontricks/winetricks CLI • No navigating hidden compatdata paths.  
  Install real Microsoft DirectX/.NET/VCRedist, apply patches/mods, run setups directly into your app's existing prefixes — solve Windows dependency issues exactly like you would on Windows. 

- **Deep per-app customization**  
  Windows version spoofing (XP–11) executed via .bat which orchestrates direct registry edits within a prefix resulting in native Windows version control,  
  custom drive/ISO/network mapping,  
  env vars (Linux launch vars),  
  launch args (Windows launch args),  
  GameMode/MangoHUD toggles — all configurable per app without ever touching the terminal.

- **True per-app isolation**  
  Dedicated Proton prefix per app by default (supports shared prefixes too) — KISS design, no symlinks, no shared prefixes unless you choose to make apps share a prefix.

- **Advanced dual-boot save sync**  
  NTFS-aware, bidirectional, timestamp-smart, conflict detection/resolution, dry-run previews — for savegames, projects, whatever. Simply runs rsync between two folders before and after app runs when enabled for that app.

- **Polished, native-feeling GUI**  
  Automatic KDE/GTK theme fusion, tile/list views, icon extraction from .exe files — I've gone through great effort to make sure this feels *integrated* not bolted on.

If you want maximum depth, reliability, and control without fragmentation or CLI dependency, this is the tool.

### Technical details

- Official GE-Proton is downloaded by SteamLess installer from GloriousEggroll’s GitHub during initial setup 
- Setup checks dependencies and auto-installs any needed for optimal proton functionality- even on a fresh linux install all you need is to run the installer and it will do everything you need to make that distro ready for proton gaming- distro-specific deps (32-bit libs, multilib, rsync, etc.)  
- Dual execution: direct GE-Proton orchestration (performance) + full Steam Runtime containerized orchestration (max compatibility)  
- Dedicated prefix architecture (optional sharing)  
- Self-healing config recovery & migration scripts for update/OS resilience  
- **Auditable source code** — pay once, inspect the entire Python codebase. No telemetry.

Hardened as my daily driver for 6+ months — battle-tested on real workflows.

### Known Limitations

- Kernel anti-cheat games (Valorant, Fortnite, etc.) blocked by developers — not a tool issue  
- GOG Galaxy: prefer offline installers for best results

### Installation – Professional & Transparent

Download the GUI installer from:  
**[https://zivena.itch.io/steamless-proton](https://zivena.itch.io/steamless-proton)** → Run → Follow the wizard (sudo only for deps)

Tested on Arch, Ubuntu/Mint/Pop, Fedora, openSUSE, Debian.

**One-time purchase • Free updates forever • No DRM**

**Power users get depth and control.**  
**Windows migrants get effortless simplicity.**  
**This is my bridge for both worlds.**

**[Get SteamLess Proton Now →](https://zivena.itch.io/steamless-proton)**

Full docs + auditable source included with purchase.
