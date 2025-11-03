# 🗺️ Project Roadmap

> **Current Version:** v1.0.0 (Linux Support)  
> **Status:** ✅ Stable Release

This document outlines the planned features and development direction for the JetBrains Trial Reset project.

---

## 🎯 Vision

Create a cross-platform, user-friendly tool to manage JetBrains IDE trial periods with:
- Multiple platform support (Linux, Windows, macOS)
- Multiple interface options (CLI, TUI, GUI)
- Safe and reliable operations
- Professional CI/CD pipeline

---

## 📅 Version History

### ✅ v1.0.0 - Initial Release (2025-11-03)

**Status:** Released

**Features:**
- ✅ Rust CLI with multiple interfaces (CLI/TUI/Rofi)
- ✅ Auto-detect JetBrains products in `~/.config/JetBrains/`
- ✅ Safe trial reset with automatic backups
- ✅ Multi-format output (table/JSON/rofi-format)
- ✅ Desktop notifications (Linux D-Bus)
- ✅ Complete documentation (README, USAGE, INSTALL)
- ✅ CI/CD with GitHub Actions
- ✅ Automated releases with binaries
- ✅ Security audits

**Platform:** Linux only

---

## 🚀 Upcoming Releases

### 🪟 v1.1.0 - Windows Support (Q1 2026)

**Goal:** Cross-platform support for Windows via cross-compilation

**Status:** Planned

**Features:**
- 🔲 Windows binary compilation (`x86_64-pc-windows-msvc`)
- 🔲 Detect Windows JetBrains paths:
  - `%APPDATA%\JetBrains\`
  - `%LOCALAPPDATA%\JetBrains\`
- 🔲 Windows toast notifications (replace D-Bus)
- 🔲 `.exe` releases with Windows installer
- 🔲 Windows-specific documentation

**Technical Changes:**
```rust
// scanner.rs - Add Windows path detection
#[cfg(target_os = "windows")]
fn get_jetbrains_config_dir() -> PathBuf {
    dirs::config_dir()
        .unwrap()
        .join("JetBrains")
}

#[cfg(target_os = "linux")]
fn get_jetbrains_config_dir() -> PathBuf {
    dirs::config_dir()
        .unwrap()
        .join("JetBrains")
}
```

**CI/CD Updates:**
- Add Windows runner in `release.yml`
- Cross-compile with `cross-rs` or native Windows runner
- Generate `jb-reset-windows-x86_64.exe`

**Dependencies:**
- Replace `notify-rust` D-Bus with Windows notifications
- Test `dirs` crate on Windows paths
- Ensure all dependencies are Windows-compatible

**Estimated Effort:** 2-3 weeks

---

### 🍎 v1.2.0 - macOS Support (Q2 2026)

**Goal:** Support for macOS (Intel and Apple Silicon)

**Status:** Planned

**Features:**
- 🔲 macOS Intel binary (`x86_64-apple-darwin`)
- 🔲 macOS Apple Silicon binary (`aarch64-apple-darwin`)
- 🔲 Native macOS notifications
- 🔲 Homebrew formula for easy installation
- 🔲 macOS-specific documentation

**Technical Changes:**
- Test JetBrains paths on macOS (similar to Linux)
- Add macOS notification system integration
- Code signing for macOS binaries (optional)

**CI/CD Updates:**
- Add macOS runners for both architectures
- Generate universal binary (optional)
- Create `.dmg` installer (optional)

**Estimated Effort:** 1-2 weeks

---

### 🎨 v2.0.0 - GUI Implementation (Q3 2026)

**Goal:** Implement graphical user interface with GTK4

**Status:** Planned

**Features:**
- 🔲 Native GTK4 window with relm4 framework
- 🔲 Visual product list with status indicators
- 🔲 One-click reset buttons
- 🔲 Progress indicators and animations
- 🔲 System tray integration
- 🔲 Desktop integration (Linux)
- 🔲 Preferences/settings dialog
- 🔲 Dark mode support

**Technical Changes:**
- Implement `src/gui/` modules (currently empty)
- Design UI with GTK4 and libadwaita
- Add application icon and desktop entry
- Internationalization support (i18n)

**Dependencies:**
- GTK4 (already in Cargo.toml as optional)
- libadwaita (already in Cargo.toml as optional)
- relm4 framework (already in Cargo.toml as optional)

**Platform Support:**
- Linux: Native GTK4
- Windows: Consider alternative GUI (egui or native)
- macOS: Consider alternative GUI or GTK4 via Homebrew

**Estimated Effort:** 4-6 weeks

---

## 🔮 Future Enhancements

### v1.x.x - Continuous Improvements

**Bug Fixes & Polish:**
- 🔲 Community-reported bug fixes
- 🔲 Performance optimizations
- 🔲 Documentation improvements
- 🔲 Error message improvements
- 🔲 Better logging and debugging

**Minor Features:**
- 🔲 Automatic backup cleanup (keep last N backups)
- 🔲 Restore from backup feature
- 🔲 Export/import settings
- 🔲 Configuration file support

---

### v2.x.x - Advanced Features

**Package Managers:**
- 🔲 AUR package for Arch Linux
- 🔲 Homebrew formula for macOS
- 🔲 Chocolatey package for Windows
- 🔲 Snap/Flatpak for Linux
- 🔲 Publish to crates.io

**Enhanced Functionality:**
- 🔲 Automatic trial expiration detection
- 🔲 Notification when trial is about to expire
- 🔲 Scheduled automatic resets (cron/task scheduler)
- 🔲 Backup compression and encryption
- 🔲 Cloud backup sync (optional)

**Product Support:**
- 🔲 Support more JetBrains products
- 🔲 Beta/EAP version support
- 🔲 Custom product detection
- 🔲 Toolbox integration

---

### v3.0.0 - Enterprise Features

**Advanced Management:**
- 🔲 Multi-user support
- 🔲 Remote management API
- 🔲 Web-based dashboard
- 🔲 License key management
- 🔲 Usage statistics and reporting

**Internationalization:**
- 🔲 Spanish (es)
- 🔲 French (fr)
- 🔲 German (de)
- 🔲 Chinese (zh)
- 🔲 Japanese (ja)
- 🔲 Russian (ru)

---

## 🤝 Contributing

Want to help implement these features? Check out our [Contributing Guidelines](CONTRIBUTING.md) (coming soon).

**Priority Areas for Contribution:**
1. 🪟 Windows support (v1.1.0)
2. 🍎 macOS testing and support (v1.2.0)
3. 🎨 GUI design and implementation (v2.0.0)
4. 📦 Package manager integrations
5. 🌍 Translations and i18n

---

## 📊 Development Priorities

**High Priority:**
- Windows cross-compilation (most requested)
- Bug fixes and stability
- Documentation improvements

**Medium Priority:**
- macOS support
- Package manager availability
- GUI implementation

**Low Priority:**
- Enterprise features
- Advanced integrations
- Cloud features

---

## 📝 Version Numbering

We follow [Semantic Versioning](https://semver.org/):

- **Major (x.0.0):** Breaking changes, major new features
- **Minor (1.x.0):** New features, backward compatible
- **Patch (1.0.x):** Bug fixes, minor improvements

---

## 💬 Feedback

Have suggestions for the roadmap? 

- 🐛 **Bug Reports:** [GitHub Issues](https://github.com/ind4skylivey/jetbrains-trial-reset/issues)
- 💡 **Feature Requests:** [GitHub Discussions](https://github.com/ind4skylivey/jetbrains-trial-reset/discussions)
- 📧 **Contact:** Open an issue on GitHub

---

## 🏁 Milestones

| Version | Status | Target | Description |
|---------|--------|--------|-------------|
| v1.0.0 | ✅ Released | 2025-11 | Linux support, CI/CD |
| v1.1.0 | 🔄 Planned | 2026-Q1 | Windows support |
| v1.2.0 | 🔄 Planned | 2026-Q2 | macOS support |
| v2.0.0 | 🔄 Planned | 2026-Q3 | GUI implementation |
| v3.0.0 | 💭 Future | TBD | Enterprise features |

---

<div align="center">

**Last Updated:** 2025-11-03  
**Maintainer:** [@il1v3y](https://github.com/il1v3y)

[⬆ Back to README](README.md)

</div>
