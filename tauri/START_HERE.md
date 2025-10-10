# START HERE - I Ching Oracle Desktop Application

Welcome to the I Ching Oracle desktop application project! This guide will help you get started quickly.

## What is This Project?

This is a desktop application that brings the ancient I Ching (Book of Changes) oracle to your computer. The I Ching is a 3000-year-old Chinese divination system that provides wisdom and guidance through 64 hexagram readings.

## Quick Start (For Users)

### Running the Application

1. **Development Mode** (for testing):
   - Double-click `quick-dev.bat`
   - Wait for the application window to open
   - The app will reload automatically when you make changes

2. **Building an Installer** (for distribution):
   - Double-click `quick-build.bat`
   - Wait for the build to complete
   - Find your installer in `src-tauri/target/release/bundle/`

## Quick Start (For Developers)

### First Time Setup

1. **Install Prerequisites**:
   - Node.js: https://nodejs.org/
   - Rust: https://rustup.rs/
   - See `SETUP.md` for detailed instructions

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run Development Server**:
   ```bash
   npm run dev
   ```

## Project Structure

```
iching/
├── src/                    # Web application files
│   ├── index.html         # Main application
│   ├── help.html          # Help documentation
│   ├── *.png              # 64 hexagram images
│   └── help_files/        # Help assets
├── src-tauri/             # Tauri (Rust) backend
│   ├── src/               # Rust source code
│   ├── icons/             # App icons
│   └── tauri.conf.json    # Configuration
├── quick-dev.bat          # Quick start development
├── quick-build.bat        # Quick build installer
└── README.md              # Project overview
```

## Key Features

- ✅ 64 complete hexagram readings with interpretations
- ✅ Dark mode support
- ✅ Question input for focused readings
- ✅ Comprehensive help documentation
- ✅ Offline functionality
- ✅ Cross-platform (Windows, macOS, Linux)

## Common Tasks

### Testing the Application
```bash
npm run dev
```

### Building for Production
```bash
npm run build
```

### Cleaning Build Artifacts
```bash
cd src-tauri
cargo clean
cd ..
```

## Important Files

- **`package.json`** - Node.js dependencies and scripts
- **`src-tauri/Cargo.toml`** - Rust dependencies
- **`src-tauri/tauri.conf.json`** - Application configuration
- **`src/index.html`** - Main application interface

## Need Help?

1. **Build Issues**: See `BUILD_INSTRUCTIONS.md`
2. **Setup Problems**: See `SETUP.md`
3. **Project Overview**: See `README.md`
4. **Tauri Documentation**: https://tauri.app/

## Next Steps

1. ✅ Read this file (you're here!)
2. 📖 Review `SETUP.md` for environment setup
3. 🔨 Review `BUILD_INSTRUCTIONS.md` for building
4. 🚀 Run `quick-dev.bat` to see the app in action
5. 📝 Review `README.md` for project details

## Application Usage

Once the application is running:

1. **Enter a Question** (optional): Type your question in the text area
2. **Submit**: Click the "Submit" button to receive a hexagram
3. **Read the Interpretation**: Review the hexagram name and detailed description
4. **Reset**: Click "Reset" to clear and start a new reading
5. **Help**: Click the "?" button for detailed help documentation
6. **Dark Mode**: Click the toggle switch in the top-right corner

## Technology Stack

- **Frontend**: HTML, CSS, JavaScript (vanilla)
- **Backend**: Rust with Tauri framework
- **Build Tool**: Tauri CLI
- **Package Manager**: npm

## Development Tips

- The app uses Tauri's asset protocol to serve local files
- All hexagram images and help files are bundled with the app
- Dark mode preference is saved in localStorage
- The application is fully self-contained and works offline

## Support

For issues or questions:
- Check the documentation files in this directory
- Visit the Tauri documentation: https://tauri.app/
- Review the project README.md

---

**Ready to begin?** Run `quick-dev.bat` to start developing!
