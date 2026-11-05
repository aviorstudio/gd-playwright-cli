<!-- Generated from private documentation source. Do not edit directly. Source SHA256: 64a4b0ade0424f81e55e3ce80b4595b3f28dd1fa06572498a099345c96757b74 -->

# gd-playwright-cli

Open-source Rust companion to [gd-playwright](https://github.com/aviorstudio/gd-playwright).

## Install

Linux and macOS, x86_64 or arm64:

```sh
curl -fsSL https://raw.githubusercontent.com/aviorstudio/gd-playwright-cli/main/scripts/install.sh | sh
```

The installer selects this repository's published `cli-v` releases, verifies archive checksums and installs `gd-playwright-cli` into `~/.local/bin`. Use `sh -s -- --version X.Y.Z --install-dir /absolute/path` to select a release or destination. Windows x86_64 and arm64 ZIPs are available from GitHub Releases. Rust is only required to build from source.

## Usage

```sh
gd-playwright-cli --json status
gd-playwright-cli list --visible
gd-playwright-cli get start_button
gd-playwright-cli wait route_loaded --timeout 10000
gd-playwright-cli --json script click start_button
```

`gd-playwright-cli` reads Godot web-game elements, events and state through Chrome DevTools Protocol. It generates Playwright action scripts for another tool to execute. Install the gd-playwright addon separately and open a diagnostic web export in a browser exposing CDP.

Select an owned browser with `--cdp URL`, `--port PORT`, `GDPW_CDP` or `GDPW_PORT`. Finite commands support `--json`; `watch` retains its event stream. WSS uses system trust roots. Use `gd-playwright-cli --help` for command flags.

## Development

`mise.toml` pins contributor SDKs. The generated root Makefile selects an immutable revision of the shared cookbook and binds it to `cookbook.toml`.

```sh
make help
make setup
make build
make test
```

`make help` works offline before setup. `make setup` explicitly prepares the pinned SDKs, locked dependencies and declared fixtures. `make build` compiles the executable, packages the native archive and verifies its source and output identity. `make test` runs lint, deterministic native unit tests, security checks and the declared integration journeys against those verified artifacts. Run build again after changing source; tests do not install tools or build missing shipping artifacts.

Use `make fmt` to apply formatting, `make test:lint`, `make test:unit`, `make test:security` or `make test:integration` to select a group, and `make clean` to remove the declared generated outputs. Build and test evidence is recorded in `.artifacts/verification`.

CI retains Linux, macOS and Windows builds for x86_64 and arm64. The integration group preserves installer and TLS trust checks. Published installers continue to use checksummed release archives.

## License and provenance

MIT. `SOURCE.json` records the original public source revision and file hashes.
