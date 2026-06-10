# ExplorerClassicContextMenu

> Restore the classic Windows 10 style Explorer context menu on Windows 11.

## What it does

On launch (or when called), the script:

1. Checks the registry to determine whether the classic context menu is currently **enabled or not**
2. Displays a status dialog:
   - **Already enabled** → `"Status: ENABLED — Do you want to re-apply it anyway?"` (Yes / No)
   - **Not enabled** → `"Status: NOT ENABLED — Do you want to restore the classic menu?"` (Yes / No)
3. **Yes** → writes the required registry key and restarts Explorer to apply changes
4. **No** → exits with no changes made

## Usage

### Standalone (run directly)

Just run `ExplorerClassicContextMenu.exe` (or `ExplorerClassicContextMenu.ahk`). The status prompt appears automatically.

### As a library

Add to your AHK library path, then call from your main script:

```ahk
#Include <ExplorerClassicContextMenu>

; Default — no tray notifications
ExplorerClassicContextMenu()

; With tray notifications
ExplorerClassicContextMenu(true)
```

### Hotkeys (active when the script window or VS Code is focused)

| Hotkey | Action |
| -------- | -------- |
| `Ctrl+Alt+Win+E` | Run / re-apply classic context menu |
| `Ctrl+Shift+Win+R` | Restart Explorer |
| `Ctrl+S` | Reload script |

## Registry key

The script writes an empty `REG_SZ` value to:

```text
HKEY_CURRENT_USER\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32
```

This is the standard, documented method to re-enable the classic context menu — no third-party tools required.

## Requirements

- Windows 11
- AutoHotkey v2.0+
