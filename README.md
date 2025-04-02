# Grok Theme for Gedit

A cosmic, futuristic theme inspired by Grok, the AI from xAI. This customizes Gedit’s entire appearance—editor colors, window UI (title bar, borders), and embedded terminal—into a sleek, dark, space-themed look.

## ✨ Features

* **Editor:** Deep black background (`#1A1A1A`) with off-white text (`#E0E0E0`) and vibrant syntax highlights (neon blue, purple, orange).
* **UI:** Dark gray title bar (`#2A2A2A`), no silver/white borders, and no blue outlines.
* **Terminal:** Matches the dark theme seamlessly.

## 📁 Files

* `grok.xml`: Gedit style scheme for the editor’s text and syntax.
* `gtk.css`: GTK3 theme for the window UI (title bar, buttons, etc.).
* `index.theme`: Metadata for the GTK theme (optional).

## 🛠️ Installation

### Prerequisites

* Gedit installed (`sudo apt install gedit` on Ubuntu, etc.).
* GNOME Tweaks (`sudo apt install gnome-tweaks`) or LXAppearance (`sudo apt install lxappearance`) for theme switching.
* Optional: `gedit-plugins` for the embedded terminal (`sudo apt install gedit-plugins`).
* Optional: `dconf-editor` for terminal tweaks (`sudo apt install dconf-editor`).

### Step 1: Install the Gedit Style Scheme

**File: `grok.xml`**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<style-scheme id="grok" _name="Grok" version="1.0">
  <author>Grok, created by xAI</author>
  <_description>A cosmic, futuristic theme inspired by Grok, the AI from xAI.</_description>
  <style name="text" foreground="#E0E0E0" background="#1A1A1A"/>
  <style name="selection" foreground="#1A1A1A" background="#00D4D4"/>
  <style name="cursor" foreground="#00D4D4"/>
  <style name="current-line" background="#2A2A2A"/>
  <style name="line-numbers" foreground="#808080" background="#1A1A1A"/>
  <style name="def:comment" foreground="#808080" italic="true"/>
  <style name="def:keyword" foreground="#00A8FF" bold="true"/>
  <style name="def:string" foreground="#FF6F00"/>
  <style name="def:number" foreground="#A100FF"/>
  <style name="def:function" foreground="#00D4D4"/>
</style-scheme>
Save the File: Copy the XML above into a file named grok.xml.

Move to Styles Directory:

Bash

mkdir -p ~/.local/share/gedit/styles
mv grok.xml ~/.local/share/gedit/styles/
Apply in Gedit:

Open Gedit: gedit.
Go to Menu > Preferences > Fonts & Colors.
Click +, navigate to ~/.local/share/gedit/styles/, select grok.xml, and apply "Grok".
Step 2: Install the GTK Theme
File: gtk.css

CSS

* {
    background-color: #1A1A1A;
    color: #E0E0E0;
    border-color: #333333;
    outline: none;
}

window {
    background-color: #1A1A1A;
}

headerbar, .titlebar {
    background-color: #2A2A2A;
    color: #E0E0E0;
    border: none;
    box-shadow: none;
}

button {
    background-color: #333333;
    color: #E0E0E0;
    border: none;
    outline: none;
}

button:hover {
    background-color: #555555;
    color: #E0E0E0;
    border: none;
    outline: none;
}

entry {
    background-color: #2A2A2A;
    color: #E0E0E0;
    border: none;
    outline: none;
}

*:focus {
    outline: none;
    box-shadow: none;
}
File: index.theme (optional)

Ini, TOML

[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Grok
Comment=A cosmic theme inspired by Grok from xAI
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Grok
MetacityTheme=Grok
Create Theme Directory:

Bash

mkdir -p ~/.themes/Grok/gtk-3.0
Save Files:

Save the CSS as ~/.themes/Grok/gtk-3.0/gtk.css.
Save the index.theme as ~/.themes/Grok/index.theme (optional).
Apply the Theme:

System-Wide: Open GNOME Tweaks: gnome-tweaks (or LXAppearance: lxappearance).

Go to Appearance > GTK Theme, select "Grok".
Gedit-Only:

Bash

GTK_THEME=Grok gedit
Or add to alias: echo "alias gedit='GTK_THEME=Grok gedit'" >> ~/.bashrc && source ~/.bashrc.
Embedded Terminal Setup
Step 1: Install the Gedit Plugins Package

The "Embedded Terminal" plugin is part of the gedit-plugins package, which might not be installed by default.

Open a Terminal: Use Ctrl+Alt+T or your preferred method to open a system terminal.

Install the Package: Depending on your Linux distribution, run one of these commands:

Ubuntu/Debian:

Bash

sudo apt update
sudo apt install gedit-plugins
Fedora:

Bash

sudo dnf install gedit-plugins
Arch Linux:

Bash

sudo pacman -S gedit-plugins
Verify Installation: After installing, you don’t need to restart your system—just proceed to Gedit.

Step 2: Enable the Embedded Terminal Plugin

Launch Gedit: Open Gedit from your applications menu or via the terminal:

Bash

gedit
If you’re using the custom "Grok" GTK theme, use:

Bash

GTK_THEME=Grok gedit
Access Preferences: Click the menu button (usually a hamburger icon in the top-right corner).

Select Preferences.

Enable the Plugin: In the Preferences window, go to the Plugins tab. Scroll through the list to find "Embedded Terminal" (or just "Terminal"). Check the box next to it to enable it.

Click Close to exit Preferences.

Step 3: Show the Terminal in Gedit

Display the Terminal Pane: Go to the View menu in Gedit’s top bar.
Select Bottom Panel (or Side Panel, depending on your Gedit version). The terminal should appear at the bottom of the Gedit window.
Use the Terminal: Click inside the terminal area to activate it. You can now type and run commands (e.g., ls, cd, python3 script.py) just like in a standalone terminal.
Step 4: Customize the Terminal (Optional)

If you’re using the "Grok" theme and want the terminal to match:

Install dconf-editor:

Bash

sudo apt install dconf-editor # Ubuntu/Debian
Adjust Colors: Open dconf-editor:

Bash

dconf-editor
Navigate to /org/gnome/gedit/plugins/terminal/.

Uncheck use-theme-colors to allow custom colors.

Set:

background-color: #1A1A1A (matches the Grok theme’s background).
foreground-color: #E0E0E0 (matches the text).
Close dconf-editor and restart Gedit to apply.

🛠️ Troubleshooting
Theme Not Showing? Ensure files are in the right paths and restart Gedit.
Blue Outlines Persist? Verify outline: none in gtk.css and reapply the theme.
GTK4? If Gedit uses GTK4 (gedit --version), move gtk.css to ~/.themes/Grok/gtk-4.0/.
No "Embedded Terminal" in Plugins? Ensure gedit-plugins is installed (dpkg -l | grep gedit-plugins on Ubuntu). Reinstall if needed.
Terminal Not Showing? Check View > Bottom Panel again—sometimes it’s hidden until toggled. Restart Gedit after enabling the plugin.
Commands Not Working? The embedded terminal uses your default shell (e.g., Bash). Verify it’s functional by typing echo $SHELL.
📜 Credits
Created by Grok, xAI’s AI assistant, on April 02, 2025.
🚀 How to Use This
Copy the README:
Open a terminal and run:

Bash

gedit README.md
Paste the entire markdown text above and save it as README.md in a folder (e.g., ~/GrokTheme/).

Add the Files: Save grok.xml, gtk.css, and index.theme in the same folder or directly in their respective directories as per the instructions.
Follow the Steps: Use the commands and steps in the README to install everything.
