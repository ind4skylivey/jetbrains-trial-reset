<div align="center">

# 🦀 JetBrains Trial Reset

### *Ultra-fast trial period reset tool for JetBrains IDEs*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Rust](https://img.shields.io/badge/Rust-1.70+-orange.svg)](https://www.rust-lang.org/)
[![Platform](https://img.shields.io/badge/Platform-Linux-blue.svg)](https://www.linux.org/)
[![Made with Rust](https://img.shields.io/badge/Made%20with-Rust-red.svg)](https://www.rust-lang.org/)
[![GitHub stars](https://img.shields.io/github/stars/ind4skylivey/jetbrains-trial-reset?style=social)](https://github.com/ind4skylivey/jetbrains-trial-reset)

**Lightweight** • **Blazingly Fast** • **Safe** • **Open Source**

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Documentation](#-documentation)

</div>

---

## 🎯 What is this?

A **modern**, **blazingly fast** CLI tool written in Rust that helps you manage JetBrains IDE trial periods on Linux. With automatic backups, multi-interface support, and desktop integration.

```bash
jb-reset reset --all  # Reset all trials in <200ms
```

<div align="center">

### ⚡ Performance Metrics

| Operation | Time | Memory |
|-----------|------|--------|
| Startup | < 100ms | < 5MB |
| Scan (10 products) | < 50ms | < 8MB |
| Reset per product | < 200ms | < 10MB |

</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

### 🚀 **Core Features**
- 🔍 **Auto-detect** all installed JetBrains products
- 🔄 **One-command reset** with automatic backup
- 💾 **Safe operations** with rollback support
- 🎯 **Selective or batch** reset
- 📦 **Single binary** (~3-5MB, no dependencies)

</td>
<td width="50%">

### 🎨 **User Experience**
- 📊 **Beautiful CLI** with colored output
- 🚀 **Rofi/dmenu** integration
- 🔔 **Desktop notifications**
- 💻 **Interactive TUI** menu
- 🌐 **JSON output** for scripting

</td>
</tr>
</table>

---

## 🧰 Supported Products

<div align="center">

| IDE | Supported | IDE | Supported |
|-----|-----------|-----|-----------|
| IntelliJ IDEA | ✅ | PyCharm | ✅ |
| WebStorm | ✅ | PhpStorm | ✅ |
| CLion | ✅ | GoLand | ✅ |
| Rider | ✅ | DataGrip | ✅ |
| RubyMine | ✅ | RustRover | ✅ |
| Android Studio | ✅ | Fleet | ✅ |

</div>

---

## 📦 Installation

### Quick Install (Recommended)

```bash
git clone https://github.com/il1v3y/jetbrains-trial-reset.git
cd jetbrains-trial-reset
sudo ./scripts/install.sh
```

### Manual Build

```bash
# Install Rust if needed
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Build from source
cargo build --release

# Install
sudo cp target/release/jb-reset /usr/local/bin/
```

### Package Managers

```bash
# Coming soon
# Arch AUR
yay -S jetbrains-trial-reset

# Homebrew
brew install jetbrains-trial-reset
```

---

## 🚀 Usage

### Basic Commands

```bash
# List all installed products
jb-reset list

# Reset all trials
jb-reset reset --all

# Reset specific product
jb-reset reset intellij

# Preview changes (dry-run)
jb-reset reset --all --dry-run
```

### Advanced Usage

```bash
# JSON output for scripting
jb-reset list --json

# Interactive TUI menu
jb-reset-gui

# Rofi launcher
jb-reset-rofi
```

### Example Output

```console
$ jb-reset list

Installed JetBrains Products:
────────────────────────────────────────────────────────────────
🧠 IntelliJ IDEA (2025.2) │ Active (6 days remaining)
🐍 PyCharm (2024.3)       │ Active (15 days remaining)
🌐 WebStorm (2024.2)      │ Expired
────────────────────────────────────────────────────────────────
```

---

## 🏗️ Tech Stack

<div align="center">

![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

</div>

**Built with:**

- **[Rust](https://www.rust-lang.org/)** - Systems programming language
- **[Clap](https://github.com/clap-rs/clap)** - Command-line argument parser
- **[Serde](https://serde.rs/)** - Serialization framework
- **[Roxmltree](https://github.com/RazrFalcon/roxmltree)** - XML parser
- **[Colored](https://github.com/mackwic/colored)** - Terminal colors
- **[Notify-rust](https://github.com/hoodie/notify-rust)** - Desktop notifications

---

## 📚 Documentation

- **[Usage Guide](USAGE.md)** - Detailed usage examples
- **[Commands Reference](COMMANDS.md)** - All available commands
- **[Installation Guide](INSTALL.md)** - Installation instructions

---

## 🔒 How It Works

<details>
<summary><b>Click to expand</b></summary>

### Reset Process

1. **Scan** - Detect installed products in `~/.config/JetBrains/`
2. **Backup** - Create timestamped backup in `~/.jetbrains-trial-backups/`
3. **Clean XML** - Remove `evlsprt*` and `trial.state*` keys from `other.xml`
4. **Remove Dirs** - Delete eval directories and cache
5. **Notify** - Send desktop notification

### Safety Features

- ✅ Automatic backup before any changes
- ✅ Dry-run mode to preview changes
- ✅ No root/sudo required
- ✅ Only modifies user-owned files
- ✅ Detailed logs of all operations
- ✅ Rollback support

</details>

---

## 🎨 Multiple Interfaces

<table>
<tr>
<td width="33%" align="center">

### 💻 CLI
Direct command-line interface
```bash
jb-reset list
```

</td>
<td width="33%" align="center">

### 🎯 TUI
Interactive terminal menu
```bash
jb-reset-gui
```

</td>
<td width="33%" align="center">

### 🚀 Rofi
Graphical launcher
```bash
jb-reset-rofi
```

</td>
</tr>
</table>

---

## ⚠️ Legal & Ethical Notice

> **Educational Purpose Only**

This tool is provided for **educational and research purposes** only.

- ✅ Use only for **legitimate testing** and **evaluation**
- ✅ **Respect software licensing** terms and conditions
- ✅ **Purchase a license** if you use the software professionally
- ❌ The authors are **not responsible** for misuse

### 💡 Support JetBrains

JetBrains offers **free licenses** for:
- 🎓 **Students** (free for educational use)
- 🌟 **Open Source** projects (free for qualifying projects)
- 🏢 **Community Editions** (IntelliJ IDEA, PyCharm)

**Support developers** by purchasing legitimate licenses: [jetbrains.com/store](https://www.jetbrains.com/store/)

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. 🍴 **Fork** the repository
2. 🌱 **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. 💾 **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. 📤 **Push** to the branch (`git push origin feature/amazing-feature`)
5. 🔃 **Open** a Pull Request

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License - Copyright (c) 2025 il1v3y
```

---

## 👨‍💻 Author

<div align="center">

**il1v3y**

Security Researcher • Red Team Operator • Python/PHP/Rust Developer

[![GitHub](https://img.shields.io/badge/GitHub-il1v3y-black?style=flat&logo=github)](https://github.com/ind4skylivey)

</div>

---

## 🙏 Acknowledgments

- 💙 **JetBrains** for creating amazing IDEs
- 🦀 **Rust Community** for excellent tooling and support
- 🖥️ **Linux Community** for inspiration and feedback

---

<div align="center">

### ⭐ If you find this project useful, please consider giving it a star!

**Made with ❤️ and Rust**

[⬆ Back to Top](#-jetbrains-trial-reset)

</div>
