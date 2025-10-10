# I Ching Oracle - Desktop Application

A desktop application for consulting the ancient I Ching (Book of Changes) oracle, built with Tauri.

## About

The I Ching, or Book of Changes, is an ancient Chinese divination text dating back over 3000 years. This application provides a modern interface to consult the oracle and receive one of 64 hexagram readings with detailed interpretations.

## Features

- **64 Hexagram Readings**: Complete set of I Ching hexagrams with detailed interpretations
- **Dark Mode**: Toggle between light and dark themes
- **Question Input**: Enter your question before consulting the oracle
- **Help Documentation**: Comprehensive guide to understanding the I Ching
- **Offline Access**: Works completely offline once installed
- **Cross-Platform**: Available for Windows, macOS, and Linux

## Quick Start

### Development Mode

Double-click `quick-dev.bat` or run:
```bash
npm run dev
```

### Building

Double-click `quick-build.bat` or run:
```bash
npm run build
```

## Installation

The built installers can be found in:
- Windows MSI: `src-tauri/target/release/bundle/msi/`
- Windows NSIS: `src-tauri/target/release/bundle/nsis/`

## Usage

1. Launch the application
2. (Optional) Enter your question in the text area
3. Click "Submit" to receive a hexagram reading
4. Read the interpretation and guidance
5. Click "Reset" to clear and start a new reading
6. Click "?" for help documentation

## Technology Stack

- **Frontend**: HTML, CSS, JavaScript
- **Backend**: Rust (Tauri)
- **Build System**: Tauri 2.0

## Project Structure

```
iching/
├── src/                    # Frontend source files
│   ├── index.html         # Main application HTML
│   ├── help.html          # Help documentation
│   ├── *.png              # Hexagram images (64 files)
│   └── help_files/        # Help documentation assets
├── src-tauri/             # Tauri backend
│   ├── src/               # Rust source files
│   ├── icons/             # Application icons
│   ├── Cargo.toml         # Rust dependencies
│   └── tauri.conf.json    # Tauri configuration
├── package.json           # Node.js dependencies
├── quick-dev.bat          # Quick development script
└── quick-build.bat        # Quick build script
```

## License

MIT License - Copyright © 2025 Radius.Center

## Credits

- I Ching translations and interpretations from traditional sources
- Built with [Tauri](https://tauri.app/)
- Developed by Radius.Center
