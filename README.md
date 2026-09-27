# Multi-File Text Viewer, Editor & Compiler

A single-file, browser-based workspace for importing, editing, previewing, organizing, and compiling multiple text-oriented files without requiring a backend.

## Concept

The app is designed as a lightweight local workspace for developers, designers, writers, and anyone who needs to work with several structured or plain-text files at the same time.

Everything runs in the browser. The application provides a three-area workspace:

- **File & Category Manager** — organizes imported files into categories and provides format filters, search, selection, and file actions.
- **Editor / Preview Area** — edits the active file and switches between editing and rendered/structured preview depending on the file format.
- **Inspector** — shows file information, validation/status details, statistics, and format-specific writing guidance.

The application is delivered as a **single HTML file**, with its CSS and JavaScript contained inside the same document.

## Main Features

### Multi-file workspace

- Import multiple files at once.
- Import an entire folder.
- Create a new file directly inside the workspace.
- Rename files inline.
- Duplicate files.
- Delete files individually.
- Organize files into custom categories.
- Drag and drop files/categories for workspace organization.

### Supported formats

The workspace is built around common text and data formats:

- TXT
- TEXT
- Markdown (`.md`, `.markdown`)
- CSV
- JSON
- JSONL / NDJSON
- YAML / YML

The editor detects the appropriate format and provides format-aware handling and guidance.

### Editing and preview

- Monospaced code/text editor.
- Line-number gutter.
- Optional word wrapping.
- Syntax-style formatting for supported structured data.
- Markdown rendered preview.
- JSON / JSONL / CSV / YAML validation-oriented preview.
- File statistics and status information.
- Format-specific writing guide with ready-to-insert examples.

### Merge / Compile engine

The app can combine workspace files into a new output.

Supported merge controls include:

- All files.
- Checked files.
- Active file only.
- Files by category.
- Files by format.
- Output as Markdown, TXT, JSON, JSONL, CSV, or YAML.
- Lossless merge.
- Structured merge.
- Automatic mode based on the output format.
- Source ordering.
- File headers, Markdown headings, comment blocks, or plain-text dividers.
- Collection/array/deep-merge/multi-document strategies where applicable.
- CSV column strategies.
- Optional metadata.
- Compact output.
- Explicit duplicate removal.
- Preview before saving/downloading.

Merge results can be copied, downloaded, or saved back into the workspace as a new file.

### Search, filtering, and selection

- Search files by name.
- Filter the workspace by file format.
- Check all visible files.
- Clear selections.
- Merge selected files.
- Remove selected files.

### Save, export, and session persistence

The application uses browser storage to preserve the workspace between page refreshes.

- Autosave keeps workspace/file state persisted locally.
- Editing changes can be saved when leaving the editor, switching files, or using `Ctrl+S` / `Cmd+S`.
- Export the active file to disk.
- Save merge results as new workspace files.

#### Session lifecycle

The workspace uses a session-oriented persistence model:

- Imported/new files belong to the current active workspace session.
- A normal browser refresh restores the active session.
- A confirmed file removal permanently removes that file's stored session data and it must not be restored by refresh or undo.
- Confirmed **Remove All**, **Clear All**, or **Reset Workspace** clears the stored workspace/session state.
- After a reset or a fully cleared workspace, newly imported/created files belong to a new active session and can persist normally on subsequent refreshes.
- Storage writes are guarded so older pending autosave operations cannot restore data that the user has already removed.

This separation prevents deleted files from unexpectedly reappearing after refresh.

### Undo / Redo

- Undo and redo support normal editing/workspace actions.
- Keyboard shortcuts:
  - `Ctrl+Z` / `Cmd+Z` — Undo
  - `Ctrl+Y` / `Cmd+Y` — Redo
- Destructive confirmed deletions are treated as permanent session operations and are not allowed to resurrect deleted files.

### Workspace controls

- New file.
- Import files.
- Import folder.
- Save As.
- Export.
- Merge.
- Merge Selected.
- Undo / Redo.
- Remove Selected.
- Remove All.
- Clear All Files.
- Reset Workspace.
- Rescan files.
- New category.
- Theme switcher.
- Online/offline connection status.

### Theme and accessibility

- Dark and light themes.
- High-contrast UI color system.
- Visible focus states for keyboard navigation.
- Responsive layout for desktop and smaller screens.
- Semantic labels and status announcements are used throughout the interface.

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl+N` / `Cmd+N` | Create new file |
| `Ctrl+S` / `Cmd+S` | Save dirty files |
| `Ctrl+M` / `Cmd+M` | Open Merge / Compile |
| `Ctrl+Z` / `Cmd+Z` | Undo |
| `Ctrl+Y` / `Cmd+Y` | Redo |
| `Ctrl+F` / `Cmd+F` | Focus file search |
| `F2` | Rename selected file |
| `Ctrl+Shift+D` / `Cmd+Shift+D` | Duplicate active file |

## Storage and privacy model

The application is intended to work locally in the browser.

There is no required application server for normal editing, previewing, compiling, or exporting. Workspace state is stored using browser-side persistence so that a refresh can restore the active session.

Imported files are not modified on the user's computer merely by importing them into the workspace. Export is an explicit action.

## Project Structure

The core application is intentionally distributed as one file:

```text
Markdown Editor.html
```

That single HTML file contains:

```text
HTML
├── UI markup
├── Internal CSS
└── Internal JavaScript
```

The project therefore does not require a build step for basic use.

## Running the application

Open the HTML file in a modern browser.

For development or browser-security-sensitive scenarios, serve the file through a local HTTP server instead of relying on a `file://` URL.

## Browser capabilities

The application relies on standard browser capabilities such as:

- File System / file input APIs for importing files.
- IndexedDB for local workspace persistence.
- Local browser storage for session initialization state.
- Clipboard API where available.
- Download APIs for exporting generated files.

Browser support can vary by feature and browser security policy.

## Credits

**Multi-File Text Viewer, Editor & Compiler**

A client-side single-file utility for multi-format text editing, organization, preview, and compilation.
