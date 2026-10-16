# CSV Table Viewer

A small VS Code extension that opens `.csv` and `.tsv` files in a spreadsheet-like grid. It follows the active VS Code theme and leaves files read-only in the table view.

## Features

- Opens CSV/TSV files in a row-and-column grid by default.
- Row numbers and spreadsheet-style column labels (A, B, …, AA).
- Horizontal and vertical scrolling, sticky header and row-number column.
- Search values across rows.
- Follows VS Code theme colors.
- **Open as Text** button to return to the standard text editor.
- Explorer context-menu command **CSV Table Viewer: Open as Table**.
- Handles quoted fields, escaped quotes, commas/tabs inside quoted fields, and multiline fields.

## Requirements

- VS Code 1.85 or newer
- Node.js 18+ and npm
- `@vscode/vsce` (installed through the project dependencies)

## Build from source

```powershell
# Open this folder in a terminal
npm install
npm run compile
```

To run it from source, open the project folder in VS Code and press **F5**. A new Extension Development Host window will open. Open a CSV file there to test.

## Package as a VSIX

```powershell
npm install
npm run compile
npx vsce package
```

This produces a file similar to `csv-table-viewer-0.1.0.vsix`.

## Install the VSIX

In VS Code:

1. Open Extensions (`Ctrl+Shift+X`).
2. Select the `...` menu in the Extensions view.
3. Choose **Install from VSIX...**.
4. Select the generated `.vsix` file.
5. Reload VS Code if prompted.

Or from PowerShell:

```powershell
code --install-extension .\csv-table-viewer-0.1.0.vsix
```

## Use

- Open a `.csv` or `.tsv` file normally; the grid editor is the default.
- Click **Open as Text** in the table toolbar to reopen the file in the normal editor.
- Right-click a CSV/TSV file in Explorer and select **CSV Table Viewer: Open as Table**.
- Use the search field to filter matching rows.

## Notes / limitations

- This is a read-only visualizer, not a spreadsheet editor. It does not modify the source CSV.
- For very large files, this initial implementation renders all rows into the webview and may use significant memory. A virtualized grid would be the next improvement for huge datasets.
- The header row is treated as the first row of the CSV.
- Delimiter detection supports comma, tab, semicolon, and pipe by checking the first line.
