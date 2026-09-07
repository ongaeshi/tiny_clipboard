# tiny_clipboard

A single-file, zero-dependency clipboard library for Ruby.

Perfect for vendoring, mimicking a C++ header-only library. You don't need to install any gems, just copy the file into your project!

## Features

*   **Single File:** Everything is contained within `tiny_clipboard.rb`.
*   **Zero Dependencies:** Relies only on Ruby's standard library (like `Fiddle` for Windows) and standard system commands.
*   **Cross-Platform:**
    *   Windows
    *   macOS (`pbcopy`, `pbpaste`)
    *   Linux / BSD (`wl-copy`/`wl-paste` for Wayland, `xclip` or `xsel` for X11)

## Installation

Since it's a single-file library, there is no need to use `gem install` or add it to a `Gemfile`. 

Simply download [tiny_clipboard.rb](tiny_clipboard.rb) and place it anywhere in your project directory.

```bash
curl -O https://raw.githubusercontent.com/ongaeshi/tiny_clipboard/main/tiny_clipboard.rb
```
*(Note: update the URL to your actual repository URL if different)*

## Usage

Require the file and use `TinyClipboard.copy` and `TinyClipboard.paste`.

```ruby
require_relative 'tiny_clipboard'

# Copy text to clipboard
TinyClipboard.copy("Hello, clipboard!")

# Paste text from clipboard
text = TinyClipboard.paste
puts text # => "Hello, clipboard!"
```

## How it works

- **Windows:** Uses `Fiddle` to directly call Win32 API functions (`OpenClipboard`, `SetClipboardData`, etc.).
- **macOS:** Uses the built-in `pbcopy` and `pbpaste` commands.
- **Linux / BSD:** Detects and uses `wl-copy`/`wl-paste` (Wayland), `xclip`, or `xsel` (X11).

## License

MIT License. See the header of `tiny_clipboard.rb` for details. This implementation references logic from the excellent `clipboard` gem.
