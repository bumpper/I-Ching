# Project Summary - I Ching Oracle Desktop Application

## Overview

**Project Name**: I Ching Oracle  
**Version**: 1.0.0  
**Type**: Desktop Application  
**Framework**: Tauri 2.0  
**Platform**: Cross-platform (Windows, macOS, Linux)  
**License**: MIT  
**Author**: Radius.Center

## Description

A desktop application that provides access to the ancient I Ching (Book of Changes) oracle system. Users can consult the oracle by asking questions and receiving one of 64 hexagram readings with detailed interpretations based on traditional Chinese wisdom.

## Key Features

### Core Functionality
- **64 Hexagram System**: Complete set of I Ching hexagrams with authentic interpretations
- **Question Input**: Optional text area for users to focus their inquiry
- **Random Selection**: Authentic random hexagram selection algorithm
- **Detailed Readings**: Comprehensive interpretations for each hexagram

### User Interface
- **Clean Design**: Simple, intuitive interface focused on the reading experience
- **Dark Mode**: Toggle between light and dark themes with persistent preference
- **Responsive Layout**: Adapts to different window sizes
- **Help System**: Built-in comprehensive help documentation

### Technical Features
- **Offline Operation**: Fully functional without internet connection
- **Fast Performance**: Native desktop performance via Tauri
- **Small Footprint**: Optimized build size (~5-10 MB)
- **Cross-Platform**: Single codebase for Windows, macOS, and Linux

## Technology Stack

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Modern styling with dark mode support
- **JavaScript**: Vanilla JS (no frameworks)
- **Assets**: 64 PNG hexagram images + help documentation

### Backend
- **Rust**: System-level programming language
- **Tauri 2.0**: Desktop application framework
- **Cargo**: Rust package manager

### Build Tools
- **npm**: Node package manager
- **Tauri CLI**: Build and development tools
- **Cargo**: Rust build system

## Project Structure

```
iching/
├── src/                          # Frontend application
│   ├── index.html               # Main application interface
│   ├── help.html                # Help documentation
│   ├── favicon.ico              # Application favicon
│   ├── 01 Creative.png          # Hexagram images (64 total)
│   ├── 02 Receptive.png
│   ├── ... (62 more hexagrams)
│   └── help_files/              # Help documentation assets
│       ├── colorschememapping.xml
│       ├── filelist.xml
│       ├── themedata.thmx
│       └── image001-064.gif     # Help images
├── src-tauri/                    # Tauri backend
│   ├── src/
│   │   ├── main.rs              # Rust entry point
│   │   └── lib.rs               # Library code
│   ├── icons/                    # Application icons
│   │   ├── 32x32.png
│   │   ├── 128x128.png
│   │   ├── 128x128@2x.png
│   │   ├── icon.icns            # macOS icon
│   │   └── icon.ico             # Windows icon
│   ├── capabilities/
│   │   └── default.json         # Permission configuration
│   ├── Cargo.toml               # Rust dependencies
│   ├── tauri.conf.json          # Tauri configuration
│   ├── build.rs                 # Build script
│   └── .gitignore               # Rust ignore rules
├── package.json                  # Node.js configuration
├── .gitignore                    # Git ignore rules
├── quick-dev.bat                 # Development launcher
├── quick-build.bat               # Build script
├── README.md                     # Project overview
├── BUILD_INSTRUCTIONS.md         # Build guide
├── START_HERE.md                 # Quick start guide
└── PROJECT_SUMMARY.md            # This file
```

## Dependencies

### Node.js Dependencies
```json
{
  "devDependencies": {
    "@tauri-apps/cli": "^2.0.0"
  }
}
```

### Rust Dependencies
```toml
[dependencies]
tauri = { version = "2.0", features = ["protocol-asset"] }
tauri-plugin-shell = "2.0"
serde = { version = "1", features = ["derive"] }
serde_json = "1"

[build-dependencies]
tauri-build = { version = "2.0", features = [] }
```

## Configuration

### Application Settings
- **Product Name**: I-Ching
- **Identifier**: center.radius.iching
- **Window Size**: 900x800 (default), resizable
- **Minimum Size**: 600x500
- **Bundle Targets**: MSI, NSIS, DEB, RPM, DMG, APP

### Build Optimization
- **Panic Mode**: Abort (release)
- **LTO**: Enabled
- **Optimization Level**: Size ("s")
- **Strip**: Enabled
- **Codegen Units**: 1

## Development Workflow

### Development Mode
```bash
npm run dev
# or
quick-dev.bat
```

### Production Build
```bash
npm run build
# or
quick-build.bat
```

### Platform-Specific Builds
```bash
npm run build:windows  # Windows MSI/NSIS
npm run build:linux    # Linux DEB/RPM
npm run build:macos    # macOS DMG/APP
```

## File Sizes

### Source Code
- Frontend HTML/CSS/JS: ~150 KB
- Hexagram Images (64): ~2 MB
- Help Documentation: ~500 KB
- Total Source: ~2.7 MB

### Built Application
- Windows Installer: ~5-8 MB
- Installed Size: ~10-15 MB
- Memory Usage: ~50-100 MB (runtime)

## Features Breakdown

### Hexagram System
- 64 unique hexagrams with traditional Chinese names
- English translations and interpretations
- Binary notation (e.g., "111111" for Creative)
- Visual representation via PNG images

### User Experience
- Simple 3-step process: Question → Submit → Read
- Optional question input (can submit without question)
- Reset button to clear and start new reading
- Persistent dark mode preference
- Help button with comprehensive documentation

### Technical Implementation
- Asset protocol for local file serving
- LocalStorage for user preferences
- Responsive CSS layout
- No external dependencies (runtime)
- No internet connection required

## Security & Privacy

- **No Data Collection**: Application doesn't collect or transmit any user data
- **Offline Operation**: No network requests made
- **Local Storage Only**: Preferences stored locally
- **No Analytics**: No tracking or telemetry
- **Open Source**: Code is transparent and auditable

## Future Enhancements (Potential)

- [ ] Multiple translation options
- [ ] Reading history
- [ ] Bookmark favorite hexagrams
- [ ] Export readings to PDF/text
- [ ] Changing lines interpretation
- [ ] Hexagram relationships visualization
- [ ] Custom themes
- [ ] Multiple language support

## Build Artifacts

### Windows
- `I-Ching_1.0.0_x64_en-US.msi` - MSI installer
- `I-Ching_1.0.0_x64-setup.exe` - NSIS installer

### Linux
- `i-ching_1.0.0_amd64.deb` - Debian package
- `i-ching-1.0.0-1.x86_64.rpm` - RPM package

### macOS
- `I-Ching.app` - Application bundle
- `I-Ching_1.0.0_x64.dmg` - DMG installer

## Support & Documentation

- **README.md**: Project overview and quick start
- **BUILD_INSTRUCTIONS.md**: Detailed build guide
- **START_HERE.md**: Beginner-friendly introduction
- **In-App Help**: Comprehensive help documentation

## License

MIT License - Copyright © 2025 Radius.Center

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## Contact

**Developer**: Radius.Center  
**Website**: https://radius.center  
**Project Repository**: (if applicable)

---

**Last Updated**: 2025  
**Document Version**: 1.0
