## Summary

* [Learning ressources](#learning-ressources)
* [Settings management](#settings-management)
* [Custom Zenmode](#custom-zenmode)
* [Shortcuts](#shortcuts)

## Learning ressources

* [Official VSCode Documentation](https://code.visualstudio.com/docs)
* [Markdown Guide](https://www.markdownguide.org/)
* [Markdown and VSCode](https://code.visualstudio.com/docs/languages/markdown)

[Back to top](#summary)

## Settings management

All the settings of VSCode are stored in a JSON file. 

You can access it by opening the command palette (Ctrl+Shift+P) and typing `Preferences: Open Settings (JSON)`

### Setting file location:

Depending on your platform, the user settings file is located here:

- **Windows** `AppData\Roaming\Code\User\settings.json`
- **macOS** `$HOME/Library/Application Support/Code/User/settings.json`
- **Linux** `$HOME/.config/Code/User/settings.json`

### Edit settings.json:

To edit the settings, you just need to open the settings.json file and edit the settings you want to change. It had IntelliSense support, so you can see the available settings and their default values as you type.

### Remove settings:

To remove a setting, you can just delete the line from the settings.json file.

### Reset all settings:

To reset all VSCode settings to their default values, you can just delete everything between the curly braces `{}` in the settings.json file.

### Workspace settings:

Workspace settings are specific to a project and can be shared across developers on a project. Workspace settings override user settings.
Workspace settings are stored in the file `.vscode/settings.json` located in the root folder.


[Back to top](#summary)

## Custom Zenmode

First install the following extensions:

- [Settings Cycler](https://marketplace.visualstudio.com/items?itemName=hoovercj.vscode-settings-cycler) 
- [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)

Then add this snippet to your `settings.json`:

```json
{
  // multiCommand
  "multiCommand.commands": [
    {
        "command": "multiCommand.zenOn",
        "sequence": [
        "workbench.action.toggleZenMode",
        "settings.cycle.zenOn",
        ]
    },
    {
      "command": "multiCommand.zenOff",
        "sequence": [
        "workbench.action.toggleZenMode",
        "settings.cycle.zenOff",
        ]
    }
  ],
  // Settings cycle
  "settings.cycle": [
  {
    "id": "zenOn",
    "values": 
    [
            {
              "window.menuBarVisibility": "hidden",
              "breadcrumbs.enabled": false,
              "window.commandCenter": false,
            }
    ],
  },
  {
    "id": "zenOff",
     "values": [
            {
              "window.menuBarVisibility": "visible",
              "breadcrumbs.enabled": true,
              "window.commandCenter": true,
            }
          ]
        }
    ],
    "zenMode.centerLayout": false,
    "zenMode.fullScreen": false,
    "zenMode.hideLineNumbers": false,
    "editor.minimap.enabled": false,
}
```

And this snippet to your `keybindings.json`

```json
[
  {
    "key": "ctrl+k z",
    "command": "extension.multiCommand.execute" ,
    "args": { "command": "multiCommand.zenOn" },
  },
  {
    "key": "ctrl+k y",
    "command": "extension.multiCommand.execute" ,
    "args": { "command": "multiCommand.zenOff" },
  }
]
```

Then everything is set up and you can turn your custom zen mode on and off by pressing `ctrl+k` then `z` and `ctrl+k` then `y`.

[Back to top](#summary)

## Shortcuts

General
- Ctrl+Shift+P, F1: Show Command Palette
- Ctrl+P: Quick Open, Go to File…
- Ctrl+Shift+N: New window/instance
- Ctrl+Shift+W: Close window/instance
- Ctrl+,: User Settings
- Ctrl+K Ctrl+S: Keyboard Shortcuts

Basic editing
- Ctrl+X: Cut line (empty selection)
- Ctrl+C: Copy line (empty selection)
- Alt+ ↑ / ↓: Move line up/down
- Shift+Alt ↓ / ↑: Copy line up/down
- Ctrl+Shift+K: Delete line
- Ctrl+Enter: Insert line below
- Ctrl+Shift+Enter: Insert line above
- Ctrl+Shift+\: Jump to matching bracket
- Ctrl+] / [: Indent/outdent line
- Home / End: Go to beginning/end of line
- Ctrl+Home: Go to beginning of file
- Ctrl+End: Go to end of file
- Ctrl+↑ / ↓: Scroll line up/down
- Alt+PgUp / PgD: Scroll page up/down
- Ctrl+Shift+[: Fold (collapse) region
- Ctrl+Shift+]: Unfold (uncollapse) region
- Ctrl+K Ctrl+[: Fold (collapse) all subregions
- Ctrl+K Ctrl+]: Unfold (uncollapse) all subregions
- Ctrl+K Ctrl+0: Fold (collapse) all regions
- Ctrl+K Ctrl+J: Unfold (uncollapse) all regions
- Ctrl+K Ctrl+C: Add line comment
- Ctrl+K Ctrl+U: Remove comment
- Ctrl+/ : Toggle line comment
- Shift+Alt+A: Toggle block comment
- Alt+Z: Toggle word wrap

Navigation
- Ctrl+T: Show all Symbols
- Ctrl+G: Go to Line...
- Ctrl+P: Go to File...
- Ctrl+Shift+O: Go to Symbol...
- Ctrl+Shift+M: Show Problems panel
- F8: Go to next error or warning
- Shift+F8: Go to previous error or warning
- Ctrl+Shift+Tab: Navigate editor group history
- Alt+ ← / →: Go back / forward
- Ctrl+M: Toggle Tab moves focus

Search and replace
- Ctrl+F: Find
- Ctrl+H: Replace
- F3 / Shift+F3: Find next/previous
- Alt+Enter: Select all occurrences of Find match
- Ctrl+D: Add selection to next Find match
- Ctrl+K Ctrl+D: Move last selection to next Find match
- Alt+C / R / W: Toggle case-sensitive / regex / whole word

Multi-cursor and selection
- AltClick: Insert cursor
- Ctrl+Alt+ ↑ / ↓: Insert cursor above / below
- Ctrl+U: Undo last cursor operation
- Shift+Alt+I: Insert cursor at end of each line selected
- Ctrl+L: Select current line
- Ctrl+Shift+L: Select all occurrences of current selection
- Ctrl+F2: Select all occurrences of current word
- Shift+Alt+→: Expand selection
- Shift+Alt+←: Shrink selection
- Shift+Alt + (drag mouse): Column (box selection
- Ctrl+Shift+Alt + (arrow key): Column (box) selection
- Ctrl+Shift+Alt +PgUp/PgDn: Column (box) selection page up/down

Rich languages editing
- Ctrl+Space, Ctrl+I: Trigger suggestion
- Ctrl+Shift+Space: Trigger parameter hints
- Shift+Alt+F: Format document
- Ctrl+K Ctrl+F: Format selection
- F12: Go to Definition
- Alt+F12: Peek Definition
- Ctrl+K F12: Open Definition to the side- Ctrl+. : Quick Fix
- Shift+F12: Show References
- F2: Rename
- Ctrl+K Ctrl+X: Trim trailing whitespace
- Ctrl+K M: Change file language

Editor management
- Ctrl+F4, Ctrl+W: Close editor
- Ctrl+K F: Close folder
- Ctrl+\: Split editor
- Ctrl+ 1 / 2 / 3: Focus into 1st, 2nd or 3rd editor group
- Ctrl+K Ctrl+ ←/→: Focus into previous/next group
- Ctrl+Shift+PgUp / PgDn: Move editor left/right
- Ctrl+K ← / →: Move active editor group

File management
- Ctrl+N: New File
- Ctrl+O: Open File...
- Ctrl+S: Save
- Ctrl+Shift+S: Save As...
- Ctrl+K S: Save All
- Ctrl+F4: Close
- Ctrl+K Ctrl+W: Close All
- Ctrl+Shift+T: Reopen closed editor
- Ctrl+K Enter: Keep preview mode editor open
- Ctrl+Tab: Open next
- Ctrl+Shift+Tab: Open previous
- Ctrl+K P: Copy path of active file
- Ctrl+K R: Reveal active file in Explorer
- Ctrl+K O: Show active file in new window/instance

Display
- F11: Toggle full screen
- Shift+Alt+0: Toggle editor layout (horizontal/vertical)
- Ctrl+ = / -: Zoom in/out
- Ctrl+B: Toggle Sidebar visibility
- Ctrl+Shift+E: Show Explorer / Toggle focus
- Ctrl++F: Show Search
- Ctrl+Shift+G: Show Source Control
- Ctrl+Shift+D: Show Debug
- Ctrl+Shift+X: Show Extensions
- Ctrl+Shift+H: Replace in files
- Ctrl+Shift+J: Toggle Search details
- Ctrl+Shift+U: Show Output panel
- Ctrl+Shift+V: Open Markdown preview
- Ctrl+K V: Open Markdown preview to the side
- Ctrl+K Z: Zen Mode (Esc Esc to exit)

Debug
- F9: Toggle breakpoint
- F5: Start/Continue
- Shift+F5: Stop
- F11 / Shift+F11: Step into/out
- F10: Step over
- Ctrl+K Ctrl+I: Show hover

Integrated terminal
- Ctrl+`: Show integrated terminal
- Ctrl+Shift+`: Create new terminal
- Ctrl+C: Copy selection
- Ctrl+V: Paste into active terminal
- Ctrl+↑ / ↓: Scroll up/down
- Shift+PgUp / PgDn: Scroll page up/down
- Ctrl+Home / End: Scroll top/bottom

[Back to top](#summary)