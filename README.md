# VS Code Setup

A Visual Studio Code setup built on the Catppuccin Mocha theme, Fluent product icons, Fira Code, and a small set of CSS and JavaScript tweaks. Follow this guide to copy the setup to your own machine and adjust it to your taste.

## Overview

VS Code does not expose every part of its interface through `settings.json`. This repository combines two layers:

- `settings.json` holds the theme, fonts, editor, and terminal options.
- `vscode-custom/` holds a stylesheet and a script that the Custom CSS and JS Loader extension injects into VS Code.

Read the [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css) documentation before you start. It lists operating system specific steps that decide whether your changes load.

## Features

- Theme: Catppuccin Mocha
- Icons: Catppuccin file icons and Fluent product icons
- Fonts: Fira Code for the editor, MesloLGS NF for the terminal, SF Mono for interface text
- Editor: no minimap, single tab, file path breadcrumbs only, underline cursor with smooth caret animation
- Saving: auto save after a delay, format on save and on paste with Prettier
- Privacy: telemetry off
- Interface: restyled title bar, activity bar, sidebar, command palette, find widget, notifications, and terminal
- Command palette: blurs the editor area while the palette is open
- Empty editor: shows a custom illustration in place of the VS Code logo and hides the shortcut list

## Prerequisites

Install these extensions from the VS Code Marketplace:

- [Catppuccin Theme](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc)
- [Catppuccin Icons](https://marketplace.visualstudio.com/items?itemName=Catppuccin.catppuccin-vsc-icons)
- [Fluent Icons](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons)
- [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css)
- [Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

The `fonts/` directory contains the fonts this setup uses:

- Fira Code: editor font with ligatures
- Hack Nerd Font: editor fallback font with icons
- MesloLGS NF: terminal font and interface font
- SF Mono: interface fallback font

## Installation

### 1. Install the fonts

Windows:

1. Open the `fonts/` folder.
2. Select all `.ttf` and `.otf` files, right-click, and choose Install.

macOS:

1. Open Font Book.
2. Drag all files from the `fonts/` folder into Font Book.

Linux:

```bash
mkdir -p ~/.local/share/fonts
cp -r fonts/* ~/.local/share/fonts/
fc-cache -f -v
```

### 2. Install the extensions

Install every extension listed under Prerequisites.

### 3. Copy the custom files

Copy the `vscode-custom` folder into the `.vscode` folder in your home directory.

Windows (PowerShell):

```powershell
Copy-Item -Recurse vscode-custom "$env:USERPROFILE\.vscode\vscode-custom"
```

macOS and Linux:

```bash
cp -r vscode-custom ~/.vscode/
```

### 4. Apply the settings

Choose one option.

Option A, replace your settings:

1. Back up your current `settings.json`.
2. Copy the `settings.json` from this repository over it.

Option B, merge your settings:

1. Open the Command Palette with `Ctrl+Shift+P` (`Cmd+Shift+P` on macOS).
2. Run Preferences: Open User Settings (JSON).
3. Copy the entries you want from this repository's `settings.json`.

### 5. Set your username in the import paths

The `vscode_custom_css.imports` setting points to the files from step 3. Replace `YOUR_USERNAME` with your operating system username.

Windows:

```jsonc
"vscode_custom_css.imports": [
  "file:///C:/Users/YOUR_USERNAME/.vscode/vscode-custom/style.css",
  "file:///C:/Users/YOUR_USERNAME/.vscode/vscode-custom/script.js"
]
```

macOS:

```jsonc
"vscode_custom_css.imports": [
  "file:///Users/YOUR_USERNAME/.vscode/vscode-custom/style.css",
  "file:///Users/YOUR_USERNAME/.vscode/vscode-custom/script.js"
]
```

Linux:

```jsonc
"vscode_custom_css.imports": [
  "file:///home/YOUR_USERNAME/.vscode/vscode-custom/style.css",
  "file:///home/YOUR_USERNAME/.vscode/vscode-custom/script.js"
]
```

### 6. Enable the custom CSS and JS

1. Open the Command Palette.
2. Run Enable Custom CSS and JS.
3. Restart VS Code when prompted.

## Usage

Edit `style.css` or `script.js` to change the look of VS Code. After each edit:

1. Open the Command Palette.
2. Run Reload Custom CSS and JS.
3. Restart VS Code.

### Edit the files from a Git clone

VS Code reads the copy in `~/.vscode/vscode-custom`, not the files in your clone. If you keep this repository cloned and edit it there, link the two folders so you do not copy files after every edit.

Windows (PowerShell). Rename or delete the existing `vscode-custom` folder in `.vscode` first:

```powershell
New-Item -ItemType Junction `
  -Path "$env:USERPROFILE\.vscode\vscode-custom" `
  -Target "C:\path\to\this\repository\vscode-custom"
```

macOS and Linux:

```bash
ln -s /path/to/this/repository/vscode-custom ~/.vscode/vscode-custom
```

## Project Structure

```text
.
fonts/               Font files used by the settings and the stylesheet
images/              Image assets
vscode-custom/
  style.css          Interface styles injected into VS Code
  script.js          Adds the blur layer behind the command palette
settings.json        VS Code user settings
README.md
```

`style.css` is split into sections by interface area: title bar, command center, activity bar, sidebar, command palette, welcome screen, editor, find widget, notifications, and terminal. Search for the section comment to find the rules you want to change.

## Troubleshooting

Custom CSS does not load:

- Use absolute paths in `vscode_custom_css.imports`.
- On Windows, use forward slashes, as in `file:///C:/Users/...`.
- Confirm that the username in the paths matches your account.
- Run Enable Custom CSS and JS, then restart VS Code completely.
- Run Reload Custom CSS and JS after every VS Code update.

Your edits have no effect:

- Check that VS Code reads the folder you are editing. See Edit the files from a Git clone above.

The empty editor shows no illustration:

- Close all editor tabs. VS Code shows the watermark only when no editor is open.
- VS Code changes its internal element structure between versions. If the selectors in the Welcome Screen section of `style.css` stop matching, open Developer: Toggle Developer Tools, inspect the empty editor, and update the selectors.

Fonts do not appear:

- Confirm that the fonts are installed for your whole system.
- Restart VS Code after you install them.
- Compare the font names in `settings.json` with the installed names.

Permission errors on macOS or Linux:

- VS Code needs write access to its own installation files. See the Custom CSS and JS Loader documentation for the steps for your system.
