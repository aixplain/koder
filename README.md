# Koder

Koder is aiXplain's agentic coding environment. It runs in your terminal, reads and
edits the project you point it at, runs your tools, and works against the models in
your aiXplain account.

![Koder running in a terminal](docs/koder.png)

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
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash -s -- --version 0.2.3
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash -s -- --no-modify-path
```

## First run

Koder asks for an aiXplain API key the first time it starts. Create one at
[studio.aixplain.com/settings/keys](https://studio.aixplain.com/settings/keys) and paste
it in — that single key unlocks the model catalogue on your account. The key is stored
under `~/.koder`, never in your project.

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
| `koder models` | list the models available to your account |
| `koder stats` | token usage and spend so far |

Other commands: `koder agent` manages agents, `koder mcp` manages MCP servers,
`koder serve` starts a headless server, and `koder web` opens the browser interface.
Run `koder --help` for the full list.

## Upgrading and removing

```sh
koder upgrade       # move to the newest release
koder upgrade 0.2.3 # or a specific one
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

Nothing is written inside your project.

## Help

- Documentation: [aixplain.com/docs](https://aixplain.com/docs)
- Questions and bug reports: [open an issue](https://github.com/aixplain/koder/issues)

## License

MIT. See [LICENSE](LICENSE).
