# red

`red` is a limited, but relatively small and fast text editor.

For a more feature complete editor that is also written in Go, check out [micro](https://github.com/zyedidia/micro).

## Screenshot

![screenshot](img/screenshot.png)

## Installation

You can install `red` with ie. Go 1.12 or later:

    go get -u github.com/xyproto/red

## Features and limitations

* Has syntax highlighting for Go code.
* Never asks before saving or quitting. Be careful.
* Only outputs text with VT100 terminal codes.
* Keys like `Home` and `End` are not even registered by the key handler (but `ctrl-a` and `ctrl-e` works).
* Will strip trailing whitespace.
* Can format Go code using `gofmt`.
* Can be used for drawing "ASCII graphics".
* Must be given a filename at start.
* `esc` can be used to toggle "writing mode" where the cursor is limited to the end of lines and "ASCII graphics mode".
* Can handle text that contains the tab character (`\t`).
* Expects utilities like `gofmt` to be in `/usr/bin`.
* The editor is always in "overwrite mode". Characters are only inserted with `return` or `ctrl-j`.
* There is no undo!
* Does not handle terminal resizing, yet.

## Known bugs

* Lines longer than the terminal width may not be handled correctly.
* Characters may appear on the screen when keys are pressed. Clear them with `ctrl-l`.
* Unicode characters may not be displayed correctly when loading a file.
* Inserting new lines with `return` is broken.
* Inserting blank characters is broken.
* The undo feature is broken.

## Hotkeys

* `ctrl-q` to quit
* `ctrl-s` to save
* `ctrl-h` to toggle syntax highlighting for Go code.
* `ctrl-f` to format the current file with `go fmt` (but not save the result).
* `ctrl-a` go to start of line
* `ctrl-e` go to end of line
* `ctrl-p` scroll up 10 lines
* `ctrl-n` scroll down 10 lines
* `ctrl-l` to redraw the screen
* `ctrl-k` to delete characters to the end of the line, then delete the line
* `ctrl-g` to show cursor positions, current letter and word count
* `ctrl-d` to delete a single character
* `ctrl-j` to insert a blank character
* `ctrl-z` to undo.
* `esc` to toggle "text edit mode" and "ASCII graphics mode"

## Size

The `red` executable is **409k** if built with GCC 9.1 (for 64-bit Linux):

    go build -gccgoflags '-Os -s'

For comparison, it's **2.8M** when building with Go 1.13 and no particular build flags are given.

## General info

* Version: 1.1.0
* License: MIT
* Author: Alexander F. Rødseth &lt;xyproto@archlinux.org&gt;
