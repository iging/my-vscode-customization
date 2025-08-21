# My own visual studio code customization

This guide will help you customize the appearance of Visual Studio Code using the **Custom CSS and JS Loader** extension.

---

**Important Note:** Before proceeding, I recommend reading the short documentation of **"Custom CSS and JS Loader"** for some useful tips for various operating systems to avoid issues where the changes may not take effect.

---

### Extensions:

- [Github Theme](https://marketplace.visualstudio.com/items?itemName=GitHub.github-vscode-theme)
- [JetBrains Icon Theme](https://marketplace.visualstudio.com/items?itemName=chadalen.vscode-jetbrains-icon-theme)
- [Fluent Icons](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons)
- [Custom CSS and JS Loader](https://marketplace.visualstudio.com/items?itemName=be5invis.vscode-custom-css)

---

### Instructions:

1. **Install the Extensions**

   - Install all of the extensions listed above by searching for them in the VS Code Marketplace.

2. **Modify `settings.json`**

   - Add the following configuration to your VS Code `settings.json` file. Before proceeding, it's highly recommended to create a backup of your current settings to prevent any unintended overwrites.

3. **Add the following configuration**:

   ```jsonc
   "vscode_custom_css.imports": [
       // Absolute file paths for your custom CSS/JS files
       // For Mac or Linux:
       // "file:///Users/[your-username]/[path-of-custom-css]/vscode-custom/style.css",
       // "file:///Users/[your-username]/[path-of-custom-css]/vscode-custom/script.js"

       // For Windows:
       // "file:///C:/[path-of-custom-css]/vscode-custom/style.css",
       // "file:///C:/[path-of-custom-css]/vscode-custom/script.js"
   ]
   ```

4. **Enable "Custom CSS and JS Loader"**

   - Open the command palette (`Ctrl+Shift+P or Cmd+Shift+P`) and in the Command Palette, type **"Enable Custom CSS and JS"** to activate the customizations.

5. **Customize the CSS or JS**

   - Modify the CSS or JS files to customize the appearance of Visual Studio Code according to your preferences. Experiment with various aspects of the VS Code interface that you wish to personalize.

6. **Reload the Extension**
   - After modifying your CSS or JS files, reload the extension by selecting **"Reload Custom CSS and JS"** from the command palette.

---

Happy customizing! Make Visual Studio Code truly your own.
