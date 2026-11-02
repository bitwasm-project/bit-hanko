# Security policy

## Reporting a vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

Use GitHub's private vulnerability reporting on this repository
([Security → Report a vulnerability](https://github.com/bitwasm-project/bit-hanko/security/advisories/new)).
Maintainer's public key, for encrypting a report: https://github.com/habakan.gpg

We aim to acknowledge a report within one week and to publish a fix within 90 days.
If you do not hear back within a week, open a public issue that says only that you are waiting for a response — with no details of the problem.

### What to include

- what the problem is and how it could be exploited
- its impact: for example a key or recovery phrase leaving the phone, the review screen showing something other than what is signed, a saved key opening without authentication, or Signer Lockdown's restrictions being bypassed
- steps, an input (a test PSBT is ideal) or code that reproduces it
- which part it affects: the Android or iPhone app, the web app, Signer Lockdown, the installer page
- the version or build (Settings, or Settings › This build in the web app)

**Never include a real private key, recovery phrase or passphrase.** If a report needs a key, generate a throwaway one and say so.

## Scope

In scope: this repository — the apps, the web app, the browser demo, Signer Lockdown and the installer page.

Problems in what `parser.wasm` or `signer.wasm` decide belong to [bitwasm-signer](https://github.com/bitwasm-project/bitwasm-signer/security/advisories/new).

What each setup can and cannot protect against is in [the guide](https://bitwasm-project.github.io/bit-hanko/docs/#threats) and [docs/security.md](docs/security.md). A limit documented there is not a vulnerability; a concrete way to exploit one still is.

This project has **not been audited**. Do not use it with funds you cannot afford to lose.
