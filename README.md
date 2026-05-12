# My Visual Studio Code Customization

This guide will help you customize the appearance of Visual Studio Code with a beautiful setup featuring the Catppuccin theme, custom fonts, and personalized CSS/JS modifications.

---

**Important Note:** Before proceeding, I recommend reading the short documentation of **"Custom CSS and JS Loader"** for some useful tips for various operating systems to avoid issues where the changes may not take effect.

---

## Prerequisites

### Required Extensions:

- [Catppuccin Theme](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc)
- [Catppuccin Icons](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc-icons)
- [Fluent Icons](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons)
- [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

### Required Fonts:

This setup uses the following fonts (all included in the `fonts/` directory):

- **Fira Code** - Main editor font with ligatures support
- **Hack Nerd Font** - Fallback font with icon support
- **MesloLGS NF** - Terminal font with powerline symbols

---

## Installation Instructions

### 1. Install Fonts

Install all fonts from the `fonts/` directory:

**Windows:**

- Navigate to the `fonts/` folder
- Right-click each `.ttf` or `.otf` file and select "Install" or "Install for all users"

**macOS:**

- Open Font Book
- Drag and drop all font files from the `fonts/` folder

**Linux:**

- Copy font files to `~/.local/share/fonts/` or `/usr/share/fonts/`
- Run `fc-cache -f -v` to refresh font cache

### 2. Install Extensions

Install all required extensions listed above from the VS Code Marketplace.

### 3. Set Up Custom CSS/JS Files

Copy the `vscode-custom` folder to your home directory:

**Windows:**

```bash
# Copy to C:\Users\[YourUsername]\.vscode\
xcopy /E /I vscode-custom C:\Users\%USERNAME%\.vscode\vscode-custom
```

**macOS/Linux:**

```bash
# Copy to ~/.vscode/
cp -r vscode-custom ~/.vscode/
```

### 4. Apply Settings

**Option A: Full Settings (Recommended)**

- Backup your current `settings.json` file
- Copy the entire `settings.json` from this repository to your VS Code settings
- Update the `vscode_custom_css.imports` paths to match your system

**Option B: Merge Settings**

- Open your VS Code `settings.json` (Ctrl+Shift+P → "Preferences: Open Settings (JSON)")
- Manually merge the settings from this repository with your existing configuration

**Important:** Update the custom CSS paths in `settings.json` to match your system:

```jsonc
"vscode_custom_css.imports": [
  // Windows:
  "file:///C:/Users/[YourUsername]/.vscode/vscode-custom/style.css",
  "file:///C:/Users/[YourUsername]/.vscode/vscode-custom/script.js",

  // macOS/Linux:
  // "file:///Users/[YourUsername]/.vscode/vscode-custom/style.css",
  // "file:///Users/[YourUsername]/.vscode/vscode-custom/script.js"
]
```

### 5. Enable Custom CSS and JS

- Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`)
- Type and select **"Enable Custom CSS and JS"**
- Restart VS Code when prompted

### 6. Customize (Optional)

Feel free to modify the CSS or JS files in the `vscode-custom` folder to personalize your setup further. After making changes:

- Open Command Palette
- Select **"Reload Custom CSS and JS"**
- Restart VS Code

---

## Features

✨ **Theme:** Catppuccin Mocha - A soothing pastel theme  
🎨 **Icons:** Catppuccin Icons + Fluent Product Icons  
🔤 **Fonts:** Fira Code with ligatures, Hack Nerd Font, MesloLGS NF  
⚡ **Performance:** Optimized settings for smooth editing experience  
🎯 **UI:** Minimal distractions - no minimap, single tab, hidden breadcrumbs  
🖱️ **Cursor:** Smooth underline cursor with phase blinking animation  
💾 **Auto-save:** Enabled with delay  
🔒 **Privacy:** Telemetry disabled

---

## Troubleshooting

**Custom CSS not loading?**

- Make sure file paths in `settings.json` use absolute paths
- On Windows, use forward slashes: `file:///C:/Users/...`
- Run "Enable Custom CSS and JS" from Command Palette
- Restart VS Code completely

**Fonts not showing?**

- Verify fonts are installed system-wide
- Restart VS Code after installing fonts
- Check font names match exactly in settings

**Permission issues on macOS/Linux?**

- You may need to grant VS Code permission to modify itself
- See Custom CSS and JS Loader documentation for details

---

Happy customizing! Make Visual Studio Code truly your own. 🚀
