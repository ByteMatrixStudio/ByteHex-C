Simple Hex Editor (WIP)

*A lightweight SDL2 + OpenGL + MicroUI based hex editor.
Currently the project opens an SDL window with MicroUI integrated.
With an example MicroUI box inside the window. 
This document outlines the development roadmap.*

**Project Goals**

- Cross-platform C hex editor

- Simple but fast UI (MicroUI)

- Clean architecture

- Easy to contribute to (shared project)

- Minimal dependencies

TODO / Roadmap

**1. Project Setup & Build System**

- set up build system: Make File and or Zekiro's custom build system

- Project folder structure

- Verify working build on all contributors' machines

**2. Core Architecture**

- Create clean separation:

- hex_core.c / hex_core.h

- Define HexFile (buffer pointer, size, filename)

*Implement:*

- hex_load_file(const char* path, HexFile* out)

- hex_unload_file(HexFile*)

- hex_get_byte(HexFile*, size_t index)

- hex_ui.c / hex_ui.h

- UI drawing functions for the hex viewer

- Handle scrolling

- Handle byte selection

- Draw layout (address, hex bytes, ASCII)

**3. File Loading**

- Basic file loading

- Test with hardcoded path

- Use fopen, fseek, ftell, fread, fclose

- Support large files (simple full-buffer load for now)

- Error handling

- MicroUI popup on failure

**4. Hex Display Layout**

- 16 bytes per row

- Columns:

- Address: 00000000:

- Hex bytes: 4F 20 53 50 ...

- ASCII: O SP...

- Tasks

- Draw a single row

- void hex_ui_draw_row(mu_Context* ctx, HexFile* file, size_t row_index);
 
- Add scrolling

- Track size_t first_visible_row

- Add selection

- Track size_t selected_index

- Highlight active cell

- Show detailed status (offset, hex value, ASCII)

**5. MicroUI Layout**

- Main application window

- Top bar

- "Open File" button

- Current filename

- Scrollable hex view in center

- Bottom status bar

- Keyboard navigation

- Arrow keys

- PageUp / PageDown

- Home / End

**6. File Picker (Open Dialog)
Stage 1: Minimal Dialog**

- Simple MicroUI modal

- Textbox for path

- Open / Cancel buttons

Stage 2: Directory Browser

- List files in directory (opendir/readdir)

- Click to select

- Double-click to open

- Remember last directory

**7. Editing (Future Stage)**

- Edit single bytes in hex

- Edit ASCII representation

- Mark file as modified

- Save / Save As

- Undo / redo stack

8. Quality of Life

- Display file size

- Display current offset and percentage

- Replace non-printable ASCII with '.'

- Keyboard shortcuts

- Ctrl+O = open file

- Ctrl+Q = quit

- Config options

- Font size

- Theme (light/dark)

- Bytes per row

**9. Future Enhancements**

- Search (byte pattern or ASCII string)

- Jump to offset

- Bookmarks

- Hex diff between two files

- Data inspector (interpret bytes as int/float/etc.)

- Endianness toggle

- Maybe wildcards
