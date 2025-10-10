# Platform-Specific Setup Guide for I Ching

This guide provides detailed setup instructions for building the I Ching application on different operating systems.

## Table of Contents

- [Windows Setup](#windows-setup)
- [macOS Setup](#macos-setup)
- [Linux Ubuntu/Debian Setup](#linux-ubuntudebian-setup)
- [Linux Fedora/RHEL Setup](#linux-fedorarhel-setup)
- [Transferring Projects Between Platforms](#transferring-projects-between-platforms)
- [Common Issues and Solutions](#common-issues-and-solutions)

---

## Windows Setup

### Prerequisites

1. **Node.js** (v16 or higher)
   - Download from: https://nodejs.org/
   - Choose the LTS version
   - Verify installation:
     ```cmd
     node --version
     npm --version
     ```

2. **Rust**
   - Download from: https://rustup.rs/
   - Run the installer and follow prompts
   - Restart your terminal after installation
   - Verify installation:
     ```cmd
     rustc --version
     cargo --version
     ```

3. **Visual Studio Build Tools**
   - Download from: https://visualstudio.microsoft.com/downloads/
   - Install "Build Tools for Visual Studio 2022"
   - Select "Desktop development with C++"
   - This provides the MSVC compiler needed for Rust

4. **WebView2** (Usually pre-installed)
   - Pre-installed on Windows 11
   - For Windows 10, download from: https://developer.microsoft.com/microsoft-edge/webview2/

### Setup Steps

1. Clone or copy the project to your Windows machine
2. Open Command Prompt or PowerShell
3. Navigate to the project directory:
   ```cmd
   cd "F:\Daniel\My Web Sites\radius.center\iching\tauri"
   ```
4. Install dependencies:
   ```cmd
   npm install
   ```
5. Test the setup:
   ```cmd
   quick-dev.bat
   ```

### Building

```cmd
# Development mode
quick-dev.bat

# Production build
quick-build.bat
```

---

## macOS Setup

### Prerequisites

1. **Xcode Command Line Tools**
   ```bash
   xcode-select --install
   ```
   - Follow the prompts to install
   - This provides essential build tools

2. **Homebrew** (Package Manager)
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
   - Follow the post-installation instructions to add Homebrew to your PATH

3. **Node.js**
   ```bash
   brew install node
   ```
   - Verify installation:
     ```bash
     node --version
     npm --version
     ```

4. **Rust**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```
   - Follow the prompts (default installation is recommended)
   - Restart your terminal
   - Verify installation:
     ```bash
     rustc --version
     cargo --version
     ```

### Setup Steps

1. Copy the project to your Mac
2. Open Terminal
3. Navigate to the project directory:
   ```bash
   cd ~/path/to/iching/tauri
   ```
4. Make scripts executable:
   ```bash
   chmod +x quick-dev.sh quick-build.sh
   ```
5. Install dependencies:
   ```bash
   npm install
   ```
6. Test the setup:
   ```bash
   ./quick-dev.sh
   ```

### Building

```bash
# Development mode
./quick-dev.sh

# Production build
./quick-build.sh
```

### Apple Silicon vs Intel

- The build script automatically detects your Mac's architecture
- For Apple Silicon (M1/M2/M3): Builds ARM64 binaries by default
- For Intel Macs: Builds x86_64 binaries
- To build for Intel on Apple Silicon:
  ```bash
  npm run build:mac-intel
  ```

---

## Linux Ubuntu/Debian Setup

### Prerequisites

1. **System Updates**
   ```bash
   sudo apt update
   sudo apt upgrade -y
   ```

2. **Node.js** (via NodeSource)
   ```bash
   # Install Node.js 20.x
   curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
   sudo apt install -y nodejs
   ```
   - Verify installation:
     ```bash
     node --version
     npm --version
     ```

3. **Rust**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```
   - Choose default installation
   - Restart your terminal or run:
     ```bash
     source $HOME/.cargo/env
     ```
   - Verify installation:
     ```bash
     rustc --version
     cargo --version
     ```

4. **Build Dependencies**
   ```bash
   sudo apt install -y \
     libwebkit2gtk-4.1-dev \
     build-essential \
     curl \
     wget \
     file \
     libssl-dev \
     libayatana-appindicator3-dev \
     librsvg2-dev
   ```

### Setup Steps

1. Copy the project to your Linux machine
2. Open Terminal
3. Navigate to the project directory:
   ```bash
   cd ~/path/to/iching/tauri
   ```
4. Make scripts executable:
   ```bash
   chmod +x quick-dev.sh quick-build.sh
   ```
5. Install dependencies:
   ```bash
   npm install
   ```
6. Test the setup:
   ```bash
   ./quick-dev.sh
   ```

### Building

```bash
# Development mode
./quick-dev.sh

# Production build (creates DEB and AppImage)
./quick-build.sh
```

### Installing the Built Package

```bash
# Install DEB package
sudo dpkg -i src-tauri/target/release/bundle/deb/iching_1.0.0_amd64.deb

# Or run AppImage directly
chmod +x src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
./src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
```

---

## Linux Fedora/RHEL Setup

### Prerequisites

1. **System Updates**
   ```bash
   sudo dnf update -y
   ```

2. **Node.js**
   ```bash
   # Install Node.js 20.x
   sudo dnf install -y nodejs
   ```
   - Verify installation:
     ```bash
     node --version
     npm --version
     ```

3. **Rust**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```
   - Choose default installation
   - Restart your terminal or run:
     ```bash
     source $HOME/.cargo/env
     ```
   - Verify installation:
     ```bash
     rustc --version
     cargo --version
     ```

4. **Build Dependencies**
   ```bash
   sudo dnf install -y \
     webkit2gtk4.1-devel \
     openssl-devel \
     curl \
     wget \
     file \
     libappindicator-gtk3-devel \
     librsvg2-devel \
     rpm-build
   ```

### Setup Steps

1. Copy the project to your Fedora/RHEL machine
2. Open Terminal
3. Navigate to the project directory:
   ```bash
   cd ~/path/to/iching/tauri
   ```
4. Make scripts executable:
   ```bash
   chmod +x quick-dev.sh quick-build.sh
   ```
5. Install dependencies:
   ```bash
   npm install
   ```
6. Test the setup:
   ```bash
   ./quick-dev.sh
   ```

### Building

```bash
# Development mode
./quick-dev.sh

# Production build (creates RPM and AppImage)
./quick-build.sh
```

### Installing the Built Package

```bash
# Install RPM package
sudo dnf install src-tauri/target/release/bundle/rpm/iching-1.0.0-1.x86_64.rpm

# Or run AppImage directly
chmod +x src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
./src-tauri/target/release/bundle/appimage/iching_1.0.0_amd64.AppImage
```

---

## Transferring Projects Between Platforms

### What to Transfer

**Include:**
- All source files (`src/` directory)
- Tauri configuration (`src-tauri/` directory)
- Scripts (`quick-dev.sh`, `quick-build.sh`, `quick-dev.bat`, `quick-build.bat`)
- Configuration files (`package.json`, `.gitignore`)
- Documentation files (`.md` files)

**Exclude (these will be regenerated):**
- `node_modules/` directory
- `src-tauri/target/` directory
- Any build artifacts

### Transfer Methods

#### Method 1: Git (Recommended)

```bash
# On source machine
git init
git add .
git commit -m "Initial commit"
git remote add origin <your-repo-url>
git push -u origin main

# On target machine
git clone <your-repo-url>
cd iching/tauri
npm install
```

#### Method 2: USB Drive

1. Copy the project folder (excluding `node_modules` and `target`)
2. On the target machine:
   ```bash
   cd path/to/iching/tauri
   npm install
   ```

#### Method 3: Network Transfer

```bash
# Using scp (from source to target)
scp -r iching/ user@target-machine:~/

# On target machine
cd ~/iching/tauri
npm install
```

### After Transfer

1. **On Unix systems (macOS/Linux):**
   ```bash
   chmod +x quick-dev.sh quick-build.sh
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Test the setup:**
   - Windows: `quick-dev.bat`
   - macOS/Linux: `./quick-dev.sh`

---

## Common Issues and Solutions

### Issue: "command not found: node"

**Solution:** Node.js is not installed or not in PATH
- Reinstall Node.js
- On Unix: Add to PATH in `~/.bashrc` or `~/.zshrc`
- On Windows: Restart terminal after installation

### Issue: "command not found: cargo"

**Solution:** Rust is not installed or not in PATH
- Install Rust from https://rustup.rs/
- On Unix: Run `source $HOME/.cargo/env`
- On Windows: Restart terminal after installation

### Issue: "webkit2gtk not found" (Linux)

**Solution:** Install WebKit dependencies
```bash
# Ubuntu/Debian
sudo apt install libwebkit2gtk-4.1-dev

# Fedora
sudo dnf install webkit2gtk4.1-devel
```

### Issue: "Permission denied" on shell scripts

**Solution:** Make scripts executable
```bash
chmod +x quick-dev.sh quick-build.sh
```

### Issue: Build fails with "linker error" (Windows)

**Solution:** Install Visual Studio Build Tools
- Download from: https://visualstudio.microsoft.com/downloads/
- Select "Desktop development with C++"

### Issue: Very slow first build

**This is normal!**
- First builds take 10-30 minutes due to Rust compilation
- Subsequent builds are much faster (1-5 minutes)
- Don't delete the `target/` directory

### Issue: "EACCES" permission errors (npm)

**Solution:** Fix npm permissions
```bash
# On Unix systems
sudo chown -R $(whoami) ~/.npm
sudo chown -R $(whoami) /usr/local/lib/node_modules
```

### Issue: Different line endings (Windows ↔ Unix)

**Solution:** Configure Git to handle line endings
```bash
# On Windows
git config --global core.autocrlf true

# On Unix
git config --global core.autocrlf input
```

---

## Verification Checklist

After setup, verify everything works:

- [ ] `node --version` shows v16 or higher
- [ ] `npm --version` shows a version number
- [ ] `cargo --version` shows a version number
- [ ] `npm install` completes without errors
- [ ] Development mode starts successfully
- [ ] Build completes successfully (may take 10-30 minutes first time)

---

## Next Steps

Once your platform is set up:

1. Read [BUILD_INSTRUCTIONS_CROSS_PLATFORM.md](BUILD_INSTRUCTIONS_CROSS_PLATFORM.md) for build instructions
2. Read [QUICK_REFERENCE.md](QUICK_REFERENCE.md) for quick command reference
3. Start developing or building!

---

## Getting Help

If you encounter issues not covered here:

1. Check the [Tauri Documentation](https://tauri.app/)
2. Check the [Tauri Prerequisites Guide](https://tauri.app/v1/guides/getting-started/prerequisites)
3. Search for your error message on [Stack Overflow](https://stackoverflow.com/)
4. Check the [Tauri Discord](https://discord.com/invite/tauri) community
