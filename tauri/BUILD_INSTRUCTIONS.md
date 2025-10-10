# Build Instructions - I Ching Oracle

## Prerequisites

Before building the I Ching Oracle application, ensure you have the following installed:

### Required Software

1. **Node.js** (v16 or later)
   - Download from: https://nodejs.org/
   - Verify installation: `node --version`

2. **Rust** (latest stable)
   - Download from: https://rustup.rs/
   - Verify installation: `rustc --version`

3. **Tauri CLI** (installed via npm)
   - Will be installed automatically with `npm install`

### Windows-Specific Requirements

- **Microsoft Visual Studio C++ Build Tools**
  - Download from: https://visualstudio.microsoft.com/visual-cpp-build-tools/
  - Required components: "Desktop development with C++"

- **WebView2** (usually pre-installed on Windows 10/11)
  - Download if needed: https://developer.microsoft.com/microsoft-edge/webview2/

## Quick Build

### Option 1: Using Batch Script (Easiest)

Simply double-click `quick-build.bat` in the project root directory.

### Option 2: Using Command Line

```bash
# Install dependencies
npm install

# Build the application
npm run build
```

## Build Output

After a successful build, you'll find the installers in:

```
src-tauri/target/release/bundle/
├── msi/          # Windows MSI installer
└── nsis/         # Windows NSIS installer
```

## Development Mode

To run the application in development mode with hot-reload:

### Option 1: Using Batch Script
Double-click `quick-dev.bat`

### Option 2: Using Command Line
```bash
npm run dev
```

## Build Targets

### Windows
```bash
npm run build:windows
```

### Linux
```bash
npm run build:linux
```

### macOS
```bash
npm run build:macos
```

## Troubleshooting

### Build Fails with "cargo not found"
- Ensure Rust is installed and in your PATH
- Restart your terminal/command prompt after installing Rust

### Build Fails with "MSVC not found" (Windows)
- Install Visual Studio C++ Build Tools
- Restart your computer after installation

### WebView2 Error (Windows)
- Install WebView2 Runtime from Microsoft
- Usually pre-installed on Windows 10/11

### Node Modules Error
```bash
# Clear node modules and reinstall
rm -rf node_modules
npm install
```

### Cargo Cache Issues
```bash
# Clear Cargo cache
cd src-tauri
cargo clean
cd ..
npm run build
```

## Build Configuration

The build configuration can be modified in:
- `src-tauri/tauri.conf.json` - Tauri settings
- `src-tauri/Cargo.toml` - Rust dependencies
- `package.json` - Node.js scripts and dependencies

## Release Build Optimization

The release build is optimized for:
- Small file size (LTO enabled)
- Fast startup time
- Minimal memory usage

Settings in `src-tauri/Cargo.toml`:
```toml
[profile.release]
panic = "abort"
codegen-units = 1
lto = true
opt-level = "s"
strip = true
```

## Support

For build issues or questions:
- Check the Tauri documentation: https://tauri.app/
- Review the project README.md
- Check the SETUP.md file for environment setup
