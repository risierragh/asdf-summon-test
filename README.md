# asdf-summon

An [asdf](https://asdf-vm.com/) plugin to install the CyberArk Summon runtime.

This plugin installs the following binaries:
- `summon` (CyberArk Summon)
- `summon-conjur` (Summon provider for Conjur)
- `conjur` (CyberArk Conjur CLI, required for authentication)

---

## Why this plugin exists

This plugin exists to provide a simple and reproducible way to install the CyberArk Summon runtime using asdf.

Summon requires multiple binaries to operate correctly, which makes manual installation error-prone, especially in automated environments. This plugin focuses exclusively on installing the required runtime components and deliberately avoids managing configuration or credentials.

---

## Scope

This plugin installs only the required **runtime binaries**:
- `summon`
- `summon-conjur`
- `conjur`

It does **not** install or manage any configuration or credentials, such as:
- `.conjurrc`
- `.netrc`
- certificates (e.g. `conjur-server.pem`)
- authentication scripts or login helpers

These elements must be provided and managed externally by the user or the execution environment.

---

## Versioning and compatibility

The version installed via `asdf` corresponds to the **Summon version**.

Additional components are installed using fixed, known-compatible versions:
- `summon` → user-selected version (e.g. `0.9.6`)
- `summon-conjur` → `0.7.1`
- `conjur` (Conjur CLI) → `9.1.0`

Compatibility reference:
- https://github.com/cyberark/conjur-oss-suite-release/releases

---

## Supported platforms

- Linux (`amd64`, `arm64`)
- macOS (`amd64`, `arm64`)

All binaries are downloaded exclusively from **official GitHub Releases**:
- https://github.com/cyberark/summon/releases
- https://github.com/cyberark/summon-conjur/releases
- https://github.com/cyberark/conjur-cli-go/releases

---

## Usage

```bash
asdf plugin add summon https://github.com/cicdnube/asdf-summon.git
asdf list-all summon
asdf install summon 0.9.6
asdf global summon 0.9.6

summon --help
