# Kate Editor — macOS Edition

[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/donate?business=6QXS8MBPKBTTN&item_name=Kate+macOS+Edition&currency_code=USD)

A custom macOS build of [KDE Kate](https://kate-editor.org/) — a powerful, multi-document text editor — enhanced with additional tools, plugins, and macOS-specific fixes. Signed and notarized for direct installation with no Gatekeeper warnings.

Download the latest DMG from [Releases](../../releases).

---

## What's Different

### macOS Fixes

**LSP Server Discovery**
Language Server Protocol servers bundled inside the application (e.g. `clangd`, `pylsp`) are automatically found without manual configuration. Kate searches its own `Contents/MacOS/` directory in addition to the system `PATH`.

**Foreground Process Model**
Kate stays in the foreground as expected on macOS. The upstream daemon-mode fork is disabled to prevent conflicts with the macOS window server.

**Build Output Font**
The Build Output panel uses **Monaco 8pt** on macOS for a crisp, readable look on Retina displays.

**Open File with Cursor Position**
Kate supports opening files with a pre-positioned cursor via URL query parameters (`?line=14&column=5`). Useful when invoked from scripts, terminal aliases, or external tools.

---

### File Browser

**Reload Button**
A **Reload** button has been added to the File Browser toolbar for quick directory refresh.

**Move to Trash Fix**
The *Move to Trash* action now correctly refreshes the directory listing immediately after a file is trashed. In the upstream build, the view would not update until manually refreshed.

---

### Build Plugin

**Improved Error Detection**
The error pattern parser handles Clang's extended diagnostic format, which appends source-range annotations after the column number (e.g. `main.cpp:14:18:{14:4-14:15}: error: …`). Errors and warnings are correctly parsed and highlighted.

---

### External Tools

**Grouped Toolbar Categories**
External tools appear as grouped category sub-menus in the toolbar, consistent with the menu bar.

**Built-in Tools**
The following tools are bundled inside the application — no separate installation required:

| Tool | Description |
|------|-------------|
| **Diagon** | Renders selected text as ASCII diagrams (sequence, flowchart, tree, and more) |
| **asciiFlow** | ASCII flow diagram editor — draw and edit diagrams directly in Kate |
| **CuteRest** | Lightweight HTTP REST client for testing API calls |
| **boxes** | Decorates selected text with ASCII art boxes and banners |
| **kdiff3** | Three-way file diff and merge tool |

---

## New Plugins

### REST Inspector

A full-featured REST API inspector embedded as a panel inside Kate:

- HTTP request builder supporting GET, POST, PUT, DELETE, PATCH, and more
- JSON and XML response viewer with syntax highlighting
- Request history and collections
- CBOR serialization support

### Docker & SSH Inspector *(Preview)*

A new panel providing virtual filesystem access to Docker containers and remote SSH environments directly from Kate's file browser:

**Docker integration:**
- Lists running and available Docker containers
- Browses the container filesystem via the `katedocker://` virtual scheme
- Reads and writes files inside containers using `docker exec` — no volume mounts required

**SSH integration:**
- Stores named SSH connection profiles (host, user, port, identity file)
- Opens remote filesystems via built-in SFTP support
- Connection profiles are saved in Kate's configuration

### Hex Editor

A compact hex dump viewer for binary files, embedded as a panel inside Kate:

- **Load options** — open the currently active Kate document with one click, or pick any file via a file dialog
- **File watching** — detects changes to the loaded file on disk and offers an instant reload; shows a warning if the file is deleted
- Hex dump with offset, hex, and ASCII columns — adapts column count dynamically to panel width
- Forward and backward **byte search** (e.g. `FF 00 AB`)
- **Go to offset** — jump directly to any position in the file (hex input)
- Read-only by default with an optional write mode toggle
- Handles large files efficiently via streaming I/O (no full load into memory)

---

## Links

- Report an issue: [GitHub Issues](../../issues)

## License

Copyright © 2025–2026 KomSoft Oprogramowanie. All rights reserved.

Kate Editor is © KDE contributors, licensed under LGPL/GPL. See [kate-editor.org](https://kate-editor.org/).

## Support

If you find this useful, please consider supporting development:

[![Donate](img/donate.png)](https://www.paypal.com/donate?business=6QXS8MBPKBTTN&item_name=Kate+macOS+Edition&currency_code=USD)
