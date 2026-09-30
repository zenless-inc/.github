# Contributing to Zenless

Thanks for helping make Zenless better! This guide applies to every repository in the
[zenless-inc](https://github.com/zenless-inc) organization.

## Ways to help

- **Report a bug.** Open an issue in the repository of the app it affects and use the *Bug report* template.
  Include your Windows version, the app version (Settings → About) and steps to reproduce.
- **Suggest a feature.** Use the *Feature request* template. Explain the problem you want solved, not only the solution.
- **Send a pull request.** Fixes, features, translations, themes and documentation are all welcome.
  For anything bigger than a small fix, open an issue first so we can agree on the approach.

## Repositories

| Repository | Stack | Check before a PR |
|---|---|---|
| [zenless-download-manager](https://github.com/zenless-inc/zenless-download-manager) | Rust, eframe/egui, tokio | `cargo check --all-targets`, `cargo test` |
| [zenless-torrent-client](https://github.com/zenless-inc/zenless-torrent-client) | Rust, eframe/egui, librqbit | `cargo check --all-targets`, `cargo test` |
| [zenless-installer](https://github.com/zenless-inc/zenless-installer) | Rust, eframe/egui | `cargo test --workspace`, `cargo xtask dist` |
| [zenless-chrome-extension](https://github.com/zenless-inc/zenless-chrome-extension) | Manifest V3, plain JS | `npm test`, `node scripts/check.js` |
| [zenless-firefox-extension](https://github.com/zenless-inc/zenless-firefox-extension) | Manifest V3, plain JS | `npm test`, `node scripts/check.js`, `npx web-ext lint` |
| [zenless-website](https://github.com/zenless-inc/zenless-website) | Static HTML/CSS/JS | Open it locally and check desktop and mobile widths |

### Building the Rust apps on Windows

1. Install Rust with [rustup](https://rustup.rs).
2. Install Visual Studio Build Tools with the **Desktop development with C++** workload (linker and Windows SDK).
3. Run `cargo run --release` in the app's folder.

Each app's README has more detail, including debug helpers such as `ZENLESS_DEMO=1`
(sample data) and `ZENLESS_SCREENSHOT=<file.png>` (saves a screenshot and exits).

## Guidelines

- **Keep the apps separate.** Zenless is a suite of independent apps, not an all-in-one. They talk over the documented
  local HTTP API on `127.0.0.1` (Download Manager `6812`, Torrent `6813`).
- **Shared code stays in sync.** `src/shared/theme.rs` and `src/shared/kit.rs` are identical in every Rust app.
  If you change one, change them all in matching PRs.
- **No C dependencies.** Prefer pure-Rust crates (e.g. `native-tls` over `ring`/`aws-lc`) so the apps build with a plain Rust toolchain.
- **Stay private.** No telemetry, analytics or network calls beyond what the user asked for.
- **Match the style.** Run `cargo fmt`, keep `cargo check` free of warnings, and write code that reads like the code around it.
- **Test your change.** Add or update tests for logic changes. For UI changes, include before/after screenshots in the PR.
- **Write clear commits.** Use a short imperative subject line, e.g. "Fix resume after server returns 416".

## Themes

Themes are welcome as PRs. Add the palette to `builtin_themes()` in every copy of `src/shared/theme.rs`, and to the
`themes.js` / `themes.css` files in the extensions and website. Make sure text stays readable, aiming for WCAG AA contrast.

## Code of conduct

Everyone taking part in Zenless spaces is expected to follow our [Code of Conduct](CODE_OF_CONDUCT.md).

## License

By contributing, you agree that your contributions are licensed under the MIT License, like the rest of Zenless.
