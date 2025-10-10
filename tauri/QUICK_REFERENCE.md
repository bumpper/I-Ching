# I Ching - Quick Reference Guide

Quick command reference for building and developing the I Ching application across different platforms.

## Quick Start

### Windows
```cmd
# Development
quick-dev.bat

# Build
quick-build.bat
```

### macOS/Linux
```bash
# First time: Make scripts executable
chmod +x quick-dev.sh quick-build.sh

# Development
./quick-dev.sh

# Build
./quick-build.sh
```

---

## NPM Scripts Reference

### Development Commands

```bash
# Generic development (auto-detects platform)
npm run dev

# Platform-specific development
npm run dev:windows    # Windows
npm run dev:mac        # macOS
npm run dev:linux      # Linux
```

### Build Commands

```bash
# Generic build (auto-detects platform)
npm run build

# Windows builds
npm run build:windows  # MSI + NSIS installers

# macOS builds
npm run build:mac      # DMG + APP (Apple Silicon)
npm run build:mac-intel # DMG + APP (Intel)
npm run build:macos    # Alias for build:mac

# Linux builds
npm run build:linux        # DEB + AppImage
npm run build:linux-deb    # DEB + AppImage (Ubuntu/Debian)
npm run build:linux-rpm    # RPM only (Fedora/RHEL)
npm run build:fedora       # RPM + AppImage (Fedora)
```

### Utility Commands

```bash
# Display platform information
npm run platform:info

# Clean build artifacts
npm run clean

# Clean everything (including node_modules)
npm run clean:all
```

---

## Prerequisites Summary

### All Platforms
- Node.js 16+
- Rust (latest stable)

### Windows
- Visual Studio Build Tools (C++)
- WebView2 Runtime

### macOS
- Xcode Command Line Tools
- Homebrew (recommended)

### Linux (Ubuntu/Debian)
```bash
sudo apt install libwebkit2gtk-4.1-dev build-essential curl wget file libssl-dev libayatana-appindicator3-dev librsvg2-dev
```

### Linux (Fedora/RHEL)
```bash
sudo dnf install webkit2gtk4.1-devel openssl-devel curl wget file libappindicator-gtk3-devel librsvg2-devel rpm-build
```

---

## Output Locations

### Windows
```
src-tauri\target\release\bundle\
├── msi\iching_1.0.0_x64_en-US.msi
└── nsis\iching_1.0.0_x64-setup.exe
```

### macOS
```
src-tauri/target/release/bundle/
├── dmg/iching_1.0.0_aarch64.dmg
└── macos/iching.app
```

### Linux (Ubuntu/Debian)
```
src-tauri/target/release/bundle/
├── deb/iching_1.0.0_amd64.deb
└── appimage/iching_1.0.0_amd64.AppImage
```

### Linux (Fedora/RHEL)
```
src-tauri/target/release/bundle/
├── rpm/iching-1.0.0-1.x86_64.rpm
└── appimage/iching_1.0.0_amd64.AppImage
```

---

## Common Tasks

### Install Dependencies
```bash
npm install
```

### Update Dependencies
```bash
npm update
```

### Update Rust
```bash
rustup update
```

### Check Platform Info
```bash
npm run platform:info
```

### Clean Build Cache
```bash
npm run clean
```

### Install Built Package

**Windows:**
- Double-click the MSI or NSIS installer

**macOS:**
- Open the DMG and drag to Applications
- Or double-click the .app file

**Linux (DEB):**
```bash
sudo dpkg -i src-tauri/target/release/bundle/deb/iching_1.0.0_amd64.deb
```

**Linux (RPM):**
```bash
sudo dnf install src-tauri/target/release/bundle/rpm/iching-1.0.0-1.x86_64.rpm
```

**Linux (AppImage):**
```bash
chmod +x src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
./src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
```

---

## Troubleshooting Quick Fixes

### "cargo not found"
```bash
# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Then restart terminal or run:
source $HOME/.cargo/env  # Unix
# Or restart terminal on Windows
```

### "node not found"
- Install Node.js from https://nodejs.org/
- Restart terminal after installation

### "Permission denied" (Unix)
```bash
chmod +x quick-dev.sh quick-build.sh
```

### "webkit2gtk not found" (Linux)
```bash
# Ubuntu/Debian
sudo apt install libwebkit2gtk-4.1-dev

# Fedora
sudo dnf install webkit2gtk4.1-devel
```

### Build is slow
- First build: 10-30 minutes (normal)
- Subsequent builds: 1-5 minutes
- Don't delete `target/` directory

### "EACCES" npm errors (Unix)
```bash
sudo chown -R $(whoami) ~/.npm
```

---

## File Structure

```
iching/tauri/
├── scripts/
│   └── platform-utils.js          # Platform detection
├── src/                            # HTML/CSS/JS application
│   ├── index.html
│   ├── help.html
│   ├── *.png                       # Hexagram images
│   └── help_files/
├── src-tauri/                      # Tauri backend
│   ├── src/
│   │   ├── main.rs
│   │   └── lib.rs
│   ├── tauri.conf.json
│   └── Cargo.toml
├── quick-dev.bat                   # Windows dev script
├── quick-build.bat                 # Windows build script
├── quick-dev.sh                    # Unix dev script
├── quick-build.sh                  # Unix build script
├── package.json                    # Node.js config
├── BUILD_INSTRUCTIONS_CROSS_PLATFORM.md
├── PLATFORM_SETUP.md
├── CROSS_PLATFORM_SUMMARY.md
└── QUICK_REFERENCE.md              # This file
```

---

## Development Workflow

1. **Make changes** to files in `src/` directory
2. **Test in dev mode:**
   - Windows: `quick-dev.bat`
   - Unix: `./quick-dev.sh`
3. **Build for production:**
   - Windows: `quick-build.bat`
   - Unix: `./quick-build.sh`
4. **Test the installer** on target platform
5. **Distribute** the installer

---

## Platform-Specific Notes

### Windows
- Requires administrator rights to install MSI
- WebView2 required (pre-installed on Win11)
- Use Command Prompt or PowerShell

### macOS
- Apps must be signed for distribution
- Notarization required for macOS 10.15+
- Use Terminal

### Linux
- DEB for Debian/Ubuntu/Mint
- RPM for Fedora/RHEL/CentOS
- AppImage works on most distributions
- Use Terminal

---

## Getting Help

- **Full Build Guide:** [BUILD_INSTRUCTIONS_CROSS_PLATFORM.md](BUILD_INSTRUCTIONS_CROSS_PLATFORM.md)
- **Setup Guide:** [PLATFORM_SETUP.md](PLATFORM_SETUP.md)
- **Summary:** [CROSS_PLATFORM_SUMMARY.md](CROSS_PLATFORM_SUMMARY.md)
- **Tauri Docs:** https://tauri.app/
- **Tauri Discord:** https://discord.com/invite/tauri

---

## Version Information

- **Application:** I Ching v1.0.0
- **Tauri:** 2.0.0
- **Node.js:** 16+ required
- **Rust:** Latest stable

---

**Quick Tip:** Run `npm run platform:info` to see your current platform configuration and available build targets.
