## What this changes, and why

<!-- One or two sentences. The diff says what; say why. -->

## Evidence

<!-- Tick what you actually ran. Delete rows that do not apply. -->

- [ ] `pnpm build` and `pnpm build:web`
- [ ] `cargo test --manifest-path src-tauri/plugins/signer/Cargo.toml`
- [ ] `pnpm tokens` leaves no diff (if you touched the design tokens)
- [ ] `pnpm build:docs` (if you touched docs/)

Tested on:

- [ ] Android phone (say which Android version)
- [ ] iPhone (native or web app; say which iOS version)
- [ ] browser demo or simulator/emulator only

## If this changes a `.wasm`

- [ ] its SHA-256 is updated everywhere it is pinned (`grep -r` the old hash: README en/ja, `wasmi_host.rs`, `SignerEngine.kt`, `src/views.ts`, `wasmi-host-poc`), and the new module comes from a tagged bitwasm-signer build

## If this changes a screen

<!-- Attach a screenshot in both English and Japanese. -->

## For anything near signing, the review screen or key storage

- [ ] I added a test, and checked it catches the bug by breaking the code on purpose
- [ ] Nothing new reaches the WebView: mnemonics, SeedQRs, raw seeds and passphrases stay native
