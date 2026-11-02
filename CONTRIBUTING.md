# Contributing

## Before you start

Read [README.md](README.md) for what this is, [the guide](https://bitwasm-project.github.io/bit-hanko/docs/) for how it is used, [docs/security.md](docs/security.md) for what is protected where, and [docs/roadmap.md](docs/roadmap.md) for what is planned.

**Security problems do not go in issues.** See [SECURITY.md](SECURITY.md).

The signing modules (`parser.wasm`, `signer.wasm`) are built in [bitwasm-signer](https://github.com/bitwasm-project/bitwasm-signer). A bug in what they decide belongs there; this repository is the apps, the web app, Signer Lockdown, the installer page and the docs.

Issues labelled [good first issue](https://github.com/bitwasm-project/bit-hanko/labels/good%20first%20issue) are small and self-contained.

## Language

- **Issues, pull requests, code review, commit messages and source-code comments: English.**
- `README.md` and `docs/` are English, with Japanese in `docs/ja/`. A change to one should change the other; if you cannot write one of them, say so in the PR and the maintainer will add it.

## Workflow

1. **Branch.** Prefix with `fix/`, `feat/`, `refactor/` or `docs/`.
2. **Commit.** A subject line plus at most one body line. The body says *why*, not *what*. Stage the files you changed; do not `git add .`.
3. **Test.** Run what covers your change (below).
4. **Open a pull request** against `main` with the template filled in.

Never commit a keystore, `keystore.properties`, an Apple team ID (`DEVELOPMENT_TEAM` in the Xcode project is filled in by `APPLE_DEVELOPMENT_TEAM` at build time), or a real recovery phrase. Use the public test words (`abandon` ×11, `about`) on testnet.

## Testing

```sh
pnpm install
pnpm build                 # type-check and build the app's web side
pnpm build:web             # the browser demo, including the wasm32 engine
cargo test --manifest-path src-tauri/plugins/signer/Cargo.toml
pnpm build:docs            # after pnpm build:web, if you touched docs/
```

CI runs the same, plus an Android build. Build steps for Android, iOS and the web app are in [README.md](README.md#build).

Say in the PR what you tested on: an Android phone, an iPhone, or the browser demo / simulator only. Changes near signing should be tried on testnet with a wallet app, and say which one.

## Conventions

- **Comments: at most two lines per block.** Keep only what you cannot get from reading the code — why a value is what it is, what breaks otherwise.
- **Simple over clever.** Extract a helper when the same thing appears three times, not before.
- Match the surrounding code's style rather than introducing your own.
- **Secrets stay native.** Mnemonics, SeedQRs, raw seeds and passphrases are never returned to the WebView.
- New tests must be checked by breaking the thing on purpose and confirming the test fails.

## AI assistance

Parts of this repository were written with AI assistance. The rule is the same one Bitcoin Core states: **there has to be a human author in the loop who understands the work and is responsible for it.** If you used a tool, you still own the patch — be ready to explain any line of it, and do not open a PR you have not read.
