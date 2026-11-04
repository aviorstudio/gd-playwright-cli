<!-- Generated from private documentation source. Do not edit directly. Source SHA256: a15a95a16e263af4357e5af41854fbef6c8cc96450a0b48e224102f6f8c44622 -->

# gdpw

Open-source Rust companion to [gd-playwright](https://github.com/aviorstudio/gd-playwright).

## Install

Linux and macOS, x86_64 or arm64:

```sh
curl -fsSL https://raw.githubusercontent.com/aviorstudio/gd-playwright-cli/main/scripts/install.sh | sh
```

The installer selects this repository's published `cli-v` releases, verifies archive checksums and installs `gdpw` into `~/.local/bin`. Use `sh -s -- --version X.Y.Z --install-dir /absolute/path` to select a release or destination. Windows x86_64 and arm64 ZIPs are available from GitHub Releases. Rust is only required to build from source.

## Usage

```sh
gdpw --json status
gdpw list --visible
gdpw get start_button
gdpw wait route_loaded --timeout 10000
gdpw --json script click start_button
```

`gdpw` reads Godot web-game elements, events and state through Chrome DevTools Protocol. It generates Playwright action scripts for another tool to execute. Install the gd-playwright addon separately and open a diagnostic web export in a browser exposing CDP.

Select an owned browser with `--cdp URL`, `--port PORT`, `GDPW_CDP` or `GDPW_PORT`. Finite commands support `--json`; `watch` retains its event stream. WSS uses system trust roots. Use `gdpw --help` for command flags.

## Development

`mise.toml` pins contributor tools. Run `mise run check` for formatting, static checks, native behavioral tests, TLS trust tests, installer checks and the executable build. `cargo build --release --locked` builds a standalone release executable. `mise run clean` removes declared generated outputs.

## License and provenance

MIT. `SOURCE.json` records the original public source revision and file hashes.
