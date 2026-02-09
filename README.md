# Stremio Service (Horizon fork)

[![Upstream](https://img.shields.io/badge/upstream-Stremio%2Fstremio--service-blue)](https://github.com/Stremio/stremio-service)

Fork of [stremio-service](https://github.com/Stremio/stremio-service) used by [Stremio Horizon App](https://github.com/Aqu1tain/stremio-horizon-app). Stremio Horizon is not a replacement for [Stremio](https://www.stremio.com) — go star the original!

## What changed

- **NO_CORS**: Always passes `NO_CORS=1` to `server.js`, allowing the Tauri-based desktop app to communicate with the service from a localhost origin.
- **No auto-updater**: Disables the built-in update mechanism so the fork stays on its own version and doesn't silently revert to upstream.

Everything else is identical to upstream.

## Build

```sh
git clone --recurse-submodules https://github.com/Aqu1tain/stremio-service
cd stremio-service
cargo build --release --features bundled
```

The `build.rs` script automatically downloads companion binaries (`server.js`) during compilation.

Platform-specific companions (`stremio-runtime`, `ffmpeg`, `ffprobe`) are expected in `resources/bin/{os}/`.

### Requirements

| Platform | Dependencies |
|----------|-------------|
| Linux | `build-essential pkg-config libgtk-3-dev libssl-dev libayatana-appindicator3-dev` |
| macOS | Xcode command-line tools |
| Windows | [Inno Setup](https://jrsoftware.org/isdl.php) |

## Related repos

- [Stremio Horizon](https://github.com/Aqu1tain/stremio-horizon) — frontend
- [Stremio Horizon App](https://github.com/Aqu1tain/stremio-horizon-app) — desktop app

## License

GPL-2.0 — see [LICENSE.md](LICENSE.md).
