<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/assets/koder-mark-dark-theme.svg">
  <img alt="Koder" src="docs/assets/koder-mark.svg" width="96" height="96">
</picture>

# Koder

**aiXplain's agentic coding environment — your terminal, your tools, your models.**

[![Release](https://img.shields.io/github/v/release/aixplain/koder?color=ec5b2b&label=release&sort=semver)](https://github.com/aixplain/koder/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/aixplain/koder/total?color=ec5b2b&label=downloads)](https://github.com/aixplain/koder/releases)
[![Platforms](https://img.shields.io/badge/platforms-macOS%20·%20Linux%20·%20Windows-ec5b2b)](#platform-support)
[![License](https://img.shields.io/github/license/aixplain/koder?color=ec5b2b)](LICENSE)

[Install](#install) · [First run](#first-run) · [Using it](#using-it) · [Upgrading](#upgrading-and-removing) · [Platforms](#platform-support) · [Configuration](#configuration)

</div>

Koder runs in your terminal, reads and edits the project you point it at, runs your
tools, and works against the models in your aiXplain account.

![Koder running in a terminal](docs/koder.png)

## Highlights

|   |   |
|---|---|
| **🧠 Agentic by default** | Describe what you want in plain language. Koder reads the files it needs, proposes edits, and runs commands — with your approval. |
| **🔌 Your aiXplain models** | One API key unlocks the model catalogue on your account. Prefer another provider? Bring your own. |
| **💻 Terminal-native** | A fast, keyboard-driven TUI — plus a headless server (`koder serve`) and a browser interface (`koder web`). |
| **🧩 MCP & multi-agent** | Connect MCP servers, run subagents, and switch agents with a keypress. |
| **📥 Bring your history** | Import past sessions from opencode, Claude Code, and Cursor with `koder import`. |
| **🔐 Signed & notarized** | macOS builds carry aiXplain's Developer ID signature and Apple notarization. Single binary, no root. |

## Install

```sh
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash
```

Open a new terminal afterwards, then run `koder` from inside a project:

```sh
cd ~/your-project
koder
```

The installer drops a single binary in `~/.koder/bin` and adds that directory to your
shell's PATH. It does not need root, and it touches nothing else.

To install a specific version, or to skip the PATH edit:

```sh
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash -s -- --version 0.2.4
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash -s -- --no-modify-path
```

## First run

Koder asks for an aiXplain API key the first time it starts.

Sign in at [app.aixplain.com](https://app.aixplain.com/), open **Integrations → API
keys**, create a key and paste it in. That single key unlocks the model catalogue on
your account. It is stored under your home directory, never in your project.

If you would rather use a different provider, choose **Use a different provider** on the
same screen, or run `koder providers` later.

## Using it

Start Koder in a project and describe what you want in plain language. It reads the
files it needs, proposes edits, and runs commands when you let it.

A few things worth knowing early:

| | |
|---|---|
| `tab` | switch agents |
| `ctrl+p` | command palette |
| `koder run "…"` | one-shot: answer and exit, useful in scripts |
| `koder import` | bring sessions over from opencode, Claude Code, or Cursor |
| `koder models` | list the models available to your account |
| `koder stats` | token usage and spend so far |

Other commands: `koder agent` manages agents, `koder mcp` manages MCP servers,
`koder serve` starts a headless server, and `koder web` opens the browser interface.
Run `koder --help` for the full list.

## Upgrading and removing

```sh
koder upgrade       # move to the newest release
koder upgrade 0.2.4 # or a specific one
koder uninstall     # remove the binary and everything under ~/.koder
```

`koder upgrade` re-runs the installer for the version you asked for, so it follows the
same path as a fresh install.

## Platform support

| Platform | Architectures |
|---|---|
| macOS | Apple Silicon (arm64), Intel (x64) |
| Linux | x64, arm64 |
| Windows | x64 |

macOS 12 or later. On Windows, download `koder-windows-x64.tar.gz` from the
[releases page](https://github.com/aixplain/koder/releases/latest) and put `koder.exe`
somewhere on your PATH; the shell installer above is for macOS and Linux.

## Verifying a download

macOS builds are signed with aiXplain's Developer ID certificate and notarized by Apple,
so they run without a Gatekeeper prompt. You can confirm that yourself:

```sh
spctl --assess --type install -vv ~/.koder/bin/koder
# koder: accepted
# source=Notarized Developer ID
# origin=Developer ID Application: aiXplain, Inc. (U6RQVYMH8L)
```

To check an archive against the checksum on its release:

```sh
shasum -a 256 koder-darwin-arm64.tar.gz
```

## If you used `aixplain-code`

The command was renamed to `koder`. The old names — `aixplain-code`, `aixplain` and
`aiXplain` — still work and point at the same binary, so existing scripts and muscle
memory keep working. Release archives are published under both names for the same
reason.

## Configuration

| | |
|---|---|
| `~/.koder/bin` | the binary and its command aliases |
| `~/.config/koder/koder.json` | configuration |
| `~/.local/share/koder` | logs, credentials and local state |
| `~/.cache/koder` | downloaded tooling |
| `KODER_RELEASE_REPO` | install and upgrade from a different repository |
| `KODER_DIST_URL` | install and upgrade from a mirror instead of GitHub |

---

<div align="center">
<sub>Built by <a href="https://aixplain.com">aiXplain</a> · <a href="https://github.com/aixplain/koder/releases">Releases</a> · <a href="LICENSE">MIT License</a></sub>
</div>
