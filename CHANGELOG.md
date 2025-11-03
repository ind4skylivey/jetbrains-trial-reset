# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned
- Windows support via cross-compilation
- macOS support (Intel and Apple Silicon)
- GUI implementation with GTK4

## [1.0.0] - 2025-11-03

### Added
- Initial stable release
- Rust CLI with multiple interfaces (CLI/TUI/Rofi)
- Auto-detect JetBrains products in `~/.config/JetBrains/`
- Safe trial reset with automatic backups
- Multi-format output support (table, JSON, rofi-format)
- Desktop notifications via D-Bus (Linux)
- Complete documentation (README, USAGE, COMMANDS, INSTALL)
- CI/CD with GitHub Actions
- Automated releases with binary artifacts
- Security audit workflow (weekly)
- 12 supported JetBrains products:
  - IntelliJ IDEA (Community/Ultimate)
  - PyCharm (Community/Professional)
  - WebStorm
  - PhpStorm
  - CLion
  - GoLand
  - Rider
  - DataGrip
  - RubyMine
  - RustRover
  - Android Studio
  - Fleet

### Technical Details
- **Language:** Rust 1.70+
- **Platform:** Linux (x86_64)
- **Binary Size:** ~717 KB (stripped)
- **Dependencies:** 
  - clap 4.4 (CLI parsing)
  - serde/serde_json (serialization)
  - colored 2.1 (terminal colors)
  - notify-rust 4.10 (notifications)
  - roxmltree 0.19 (XML parsing)
- **Performance:**
  - Startup: < 100ms
  - Scan: < 50ms (10 products)
  - Reset: < 200ms per product
  - Memory: < 10MB

### CI/CD
- Automated testing on push/PR (stable and beta Rust)
- Code formatting checks (cargo fmt)
- Linter checks (cargo clippy)
- Security audits (cargo audit)
- Automated binary releases on tags

### Documentation
- Professional README with badges
- Detailed usage guide (USAGE.md)
- Command reference (COMMANDS.md)
- Installation instructions (INSTALL.md)
- MIT License with educational disclaimer
- Security checklist

### Safety Features
- Automatic backup before any changes
- Dry-run mode for preview
- Timestamped backups in `~/.jetbrains-trial-backups/`
- No root/sudo required
- Only modifies user-owned files

## Release Notes

### v1.0.0 - "Initial Launch"

This is the first stable release of JetBrains Trial Reset for Linux. The project started as an analysis of existing trial reset tools and evolved into a complete, professional Rust implementation.

**Highlights:**
- ✨ Clean, modern Rust codebase (1,017 lines)
- 🚀 Blazingly fast performance (< 200ms per reset)
- 🛡️ Safe operations with automatic backups
- 📦 Single binary, no dependencies
- 🎨 Multiple interfaces (CLI/TUI/Rofi)
- 🤖 Professional CI/CD pipeline
- 📖 Complete documentation

**Known Limitations:**
- Linux only (Windows/macOS support planned for v1.1.0/v1.2.0)
- Desktop notifications require D-Bus
- GTK4 GUI not yet implemented (planned for v2.0.0)

**Installation:**
```bash
wget https://github.com/ind4skylivey/jetbrains-trial-reset/releases/download/v1.0.0/jb-reset-linux-x86_64
chmod +x jb-reset-linux-x86_64
sudo mv jb-reset-linux-x86_64 /usr/local/bin/jb-reset
```

**Usage:**
```bash
# List installed products
jb-reset list

# Reset all trials
jb-reset reset --all

# Interactive TUI menu
jb-reset-gui
```

---

## Version History Summary

| Version | Date | Description | Breaking Changes |
|---------|------|-------------|------------------|
| 1.0.0 | 2025-11-03 | Initial stable release | N/A (first release) |

---

## Upgrade Guide

### From Source to v1.0.0

If you were using the tool from source before the release:

```bash
# Remove old source installation
rm -f ~/.local/bin/jb-reset

# Download and install v1.0.0 binary
wget https://github.com/ind4skylivey/jetbrains-trial-reset/releases/download/v1.0.0/jb-reset-linux-x86_64
chmod +x jb-reset-linux-x86_64
sudo mv jb-reset-linux-x86_64 /usr/local/bin/jb-reset

# Verify installation
jb-reset --version
```

---

## Links

- **Repository:** https://github.com/ind4skylivey/jetbrains-trial-reset
- **Releases:** https://github.com/ind4skylivey/jetbrains-trial-reset/releases
- **Issues:** https://github.com/ind4skylivey/jetbrains-trial-reset/issues
- **Roadmap:** [ROADMAP.md](ROADMAP.md)

---

<div align="center">

**Maintained by [@il1v3y](https://github.com/il1v3y)**

[⬆ Back to README](README.md)

</div>
