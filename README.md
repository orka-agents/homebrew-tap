# Orka Homebrew tap

Homebrew formula for the [Orka](https://github.com/orka-agents/orka) CLI.

```bash
brew install orka-agents/tap/orka
orka version
```

Use the fully qualified name: `brew install orka` resolves to an unrelated cask.
The formula tracks the latest stable Orka release; keep the CLI at the version of
your installed controller, and use the
[release archives](https://github.com/orka-agents/orka/releases) for any other version.

## How the formula is updated

`Formula/orka.rb` is generated; do not edit it by hand.
[`update-formula.yml`](.github/workflows/update-formula.yml) runs when Orka's release
workflow dispatches `orka-release`, every six hours, or on demand. It runs
[`scripts/update-formula.sh`](scripts/update-formula.sh), which verifies the release's
keyless Cosign signature on `orka_<version>_checksums.txt` against Orka's
`release.yml` on the matching `release-X.Y` branch and tagged commit, then writes
the formula from those checksums. The workflow installs and tests the formula
before committing it to `main`.

To regenerate locally (needs `gh`, `cosign`, and `curl`):

```bash
scripts/update-formula.sh v0.3.0
```
