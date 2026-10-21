<div align="center">

<img src="docs/assets/aixplain-mark.svg" alt="aixplain" width="64" height="64">

# Koder

**Safe to explore. Free to build.**

Koder is aixplain's AI coding agent for your desktop and terminal. It reads your project, makes changes you can review line by line, runs your tests, and asks before it touches anything you have not cleared it to. Use aixplain's models, the Claude, ChatGPT or Cursor plan you already pay for, or a local model. Omni, the personal assistant in the same app, handles the work around the code.

[![Latest release](https://img.shields.io/github/v/release/aixplain/koder?color=fe6b6f&label=latest&sort=semver)](https://github.com/aixplain/koder/releases/latest)
[![Copyright aixplain](https://img.shields.io/badge/copyright-aixplain-fe6b6f)](#copyright-and-licenses)

<p align="center">
  <a href="https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-mac-arm64.dmg"><img src="docs/assets/download-macos-icon.svg" alt="Download Koder for macOS — Apple silicon" width="240" height="80"></a>
  <a href="https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-win-x64.exe"><img src="docs/assets/download-windows-icon.svg" alt="Download Koder for Windows — x64" width="240" height="80"></a>
  <a href="https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-x86_64.AppImage"><img src="docs/assets/download-linux-icon.svg" alt="Download Koder for Linux — x64 AppImage" width="240" height="80"></a>
</p>

[Intel Mac](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-mac-x64.dmg) · [Linux DEB](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-amd64.deb) · [Linux RPM](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-x86_64.rpm) · [All downloads](https://koder.aixplain.com/#download)

[Features](#what-koder-does) · [Your plans](#use-the-plans-you-already-pay-for) · [Install](#install) · [Get started](#get-started) · [Commands](#commands) · [Safety and privacy](#safety-and-privacy) · [Get help](#get-help)

</div>

![Koder desktop: a session that fixed a SQL injection and ran the tests, with the two-file diff open in the Review panel](docs/assets/desktop-large-logo.png)

## What Koder does

### Works in your project, and shows its work

Describe the outcome you want. Koder reads the relevant files, edits them, runs your commands, and reads the results before it decides the next step. Every step stays in the conversation: what it read, what it changed, and what it ran. The Review panel collects the session's changes into one diff you can read, unified or split, and commit when you are satisfied.

Start in plain language or with a starter task (explain this project, find and fix a bug, add a feature, write tests, review my changes, start from a pull request). Plan first with the planning agent, then let it build. Bring your own project instructions in `AGENTS.md`, plus skills, MCP servers and plugins.

### You decide what it may do on its own

![Koder asking before a shell command reads the .env file, with Deny and Allow buttons](docs/assets/desktop-permissions.png)

Pick an access mode in the chat box:

- **Ask first:** asks before running commands or changing files.
- **Auto:** follows your permission rules and asks only where they say to.
- **Full access:** works without asking, except before spending money, deleting folders, force-deleting files, pushing, or reading secret files. It goes back to Auto when the app restarts.

Secret files such as `.env` always ask before they are read, in every mode, including when the read happens inside a shell command like `cat`, `grep` or `source`. The approval names the exact file, and "Always allow" covers only that file. Changes to the folders that define agents, modes and commands always ask too.

<details>
<summary>See the access modes</summary>

![The Permissions menu in the chat box: Ask first, Auto and Full access, each with a one-line description](docs/assets/desktop-access-modes.png)

</details>

The terminal app offers the same idea with five levels through `/auto`: `ask`, `rules`, `read-only`, `auto` and `full`.

### Finds likely security bugs with Scan

![Koder Scan listing six likely issues by severity, with one SQL injection finding open beside the list](docs/assets/scan.png)

Scan reads a repository for security bugs and lists what it finds, worst first. Each finding explains what is wrong, traces how an attacker's input reaches the bug step by step, and can come with a proposed fix. Open **Security** from a project in the sidebar or from the command palette, or run `koder scan` in the terminal.

Scan reads the code but does not run it yet, so every finding is marked as a likely issue, not a proven one. Review each one before you act on it. `koder scan` can write a SARIF report and exits with an error when it finds something at or above the severity you set with `--fail-on`, so it can gate a CI job.

### Keeps every session in one place

![The sessions sidebar: sessions waiting for you and running at the top, earlier sessions from two projects grouped under Today](docs/assets/sessions.png)

The sidebar holds the sessions from all your projects. Anything running or waiting on you sits at the top with a short status such as "waiting for you". The rest can be grouped by date or by project, or narrowed to one project. Sessions are saved on your machine, so you can come back to any of them.

### Omni, your personal assistant

![Omni home with a greeting, the chat box and the conversations to pick up](docs/assets/omni.png)

Switch to **Omni** in the desktop app, or run `koder omni`. Omni takes on the work around the code: drafting, planning, making sense of documents and numbers, building agents, and working in the apps you connect.

![Omni after writing an onboarding checklist: the steps folded into one line, the answer, and the document it saved](docs/assets/omni-cards.png)

- **The answer comes first.** A finished turn folds its steps into one line, with the answer and any files it made right below.
- **Works in your accounts.** Connect email, calendar, chat and project tools in **Omni settings → Connect your apps**. Anything that sends, creates, changes or deletes something is shown to you and approved one call at a time.
- **Builds and runs agents.** Browse ready-made aixplain agents and your workspace's own on the Agents page, which shows how each one is built: its model, tools, skills, instructions and limits. Omni can also build a new agent with you.
- **Picks up where you left off.** Omni home lists the chats stopped at an approval or a question, scheduled runs that failed, and the conversations you were last in.

Connections are aixplain team assets. Verification and actions may use credits.

### A terminal app that keeps up

![The Koder terminal app after fixing a shell injection: tool steps, the passing test run, the summary, and the context, throughput and tools panels](docs/assets/terminal.png)

The terminal app has the same agent, permissions and sessions, with keyboard and mouse control, a side panel for context, spend and tool use, and syntax highlighting that works offline. Use `koder run` for scripts and automation.

The desktop app speaks 17 languages, including Arabic with a right-to-left layout.

## Use the plans you already pay for

Already pay for Claude, ChatGPT or Cursor? Use that plan in Koder. Koder runs each vendor's own CLI with the sign-in you already have, so there are no new keys to manage.

| Plan | What you need | How it runs |
| --- | --- | --- |
| **Claude** (Pro, Max, Team) | [Claude Code](https://claude.ai/download), signed in | A full Claude Code agent. Its tool use goes through Koder's permissions |
| **ChatGPT** (Plus, Pro, Business) | [Codex CLI](https://github.com/openai/codex), signed in with `codex login` | Codex with the models your plan offers |
| **Cursor** (paid plan) | Cursor's `cursor-agent`, signed in with `cursor-agent login` | Cursor's agent over ACP |

Koder finds installed CLIs automatically, including ones behind version managers. Check where each one stands in **Settings → Providers → Your subscriptions**, or run `koder providers subs`. Each shows Ready, Not signed in or Not installed, the account and plan, and the one command that fixes it. Usage counts against your plan's limits.

## Install

### Desktop app

| Your computer | Installer |
| --- | --- |
| macOS · Apple silicon | [Download DMG](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-mac-arm64.dmg) |
| macOS · Intel | [Download DMG](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-mac-x64.dmg) |
| Windows · x64 | [Download EXE](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-win-x64.exe) |
| Linux · x64 | [DEB](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-amd64.deb) · [AppImage](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-x86_64.AppImage) · [RPM](https://github.com/aixplain/koder/releases/latest/download/aixplain-code-desktop-linux-x86_64.rpm) |

The desktop app installs as **aixplain**, with Koder, Design and Omni inside it. The macOS app is signed with aixplain's Developer ID and notarized by Apple, and the Windows installer is signed by aixplain. Every release includes `SHA256SUMS` for checksum verification.

### Command line

**macOS and Linux**

```sh
curl -fsSL https://github.com/aixplain/koder/releases/latest/download/install | bash
```

**Windows (PowerShell)**

```powershell
irm https://github.com/aixplain/koder/releases/latest/download/install.ps1 | iex
```

The installer places `koder` in `~/.koder/bin` and adds it to your user PATH. Open a new terminal after installation. CLI builds are available for macOS arm64/x64, Linux arm64/x64 and Windows x64. To read the installer before running it, download [`install`](https://github.com/aixplain/koder/releases/latest/download/install) or [`install.ps1`](https://github.com/aixplain/koder/releases/latest/download/install.ps1). For archives and previous versions, see [all releases](https://github.com/aixplain/koder/releases).

## Get started

1. **Open a project.** Choose a folder in the desktop app, or run `koder` in your project directory.
2. **Connect a model.** Sign in to aixplain, connect a plan you already have, or configure another provider. An aixplain API key also gives model access; billing needs a signed-in account.
3. **Give it a concrete task.** Say what done looks like and any constraints, then follow the steps, answer its questions and review the diff.

```sh
cd your-project
koder
```

Try a task like:

> Find why this test fails, explain the cause, make the smallest fix, and run the relevant tests.

To use your aixplain account from the CLI:

```sh
koder login
koder whoami
koder models
```

## Commands

| Command | What it does |
| --- | --- |
| `koder` | Open the terminal app in the current project. |
| `koder run "Explain this project"` | Run a prompt from the shell. Add `--agent plan` to plan first, or `--model <provider/model>` to pick a model. |
| `koder scan` | Scan the project for likely security bugs. Add `--sarif <file>` for a report and `--fail-on <severity>` to gate CI. |
| `koder omni` | Open Omni in the terminal. |
| `koder providers subs` | Check your Claude, ChatGPT and Cursor plans. |
| `koder models --zdr` | List models the catalog reports as zero data retention. |
| `koder session list` | List saved sessions. |
| `koder import` | Import sessions from a share file or another coding agent. |
| `koder mcp` | Manage MCP servers. |
| `koder inspect` | Show the effective permission policy and which layer set each value. |
| `koder stats` | Show token usage and cost. |
| `koder billing` | View credits, top up, or add a card. |
| `koder doctor` | Check the install, config, storage, providers and recent logs. |
| `koder serve` | Start a headless server for clients and integrations. |
| `koder web` | Open the browser interface. |

Run `koder --help` or `koder <command> --help` for every command and option in your installed version.

## Safety and privacy

- **Permission checks.** Tool actions follow your access mode and permission rules. Run `koder inspect` to see the effective policy before connecting tools or opening an unfamiliar project, and use workspace trust to decide which projects' own configuration is honored.
- **Limits that hold in every mode.** Even Full access asks before pushing, deleting folders, force-deleting files, spending money and reading secrets. Scheduled runs refuse these and record why.
- **Reviewable changes.** Follow each step, read the diff and check test results before you accept the outcome. You can stop a run at any time.
- **Local storage.** Sessions and configuration stay on your machine. Protect that profile as you would your project files.
- **Clear data boundaries.** Hosted providers receive the inputs sent to them. A local model keeps inference on your machine; connected tools may still send data to their services. The scan key and the local server password are kept out of the shells and tools Koder starts.
- **Zero data retention filter.** Pick **ZDR only** in the model picker, or run `koder models --zdr`, to list only models the catalog reports as zero retention.
- **Crash reports only if you want them.** They are off until you turn them on in **Settings → General → Privacy**, or set `"crashReports": true` in your global config. A report says what kind of error happened and where in Koder's code, never your messages, files, folder names or keys.

## Team credits and billing

Open **Settings → Account** in the desktop app, use `/billing` in the terminal app, or run:

```sh
koder billing
koder billing top-up --amount 10
koder billing add-card
```

Koder shows the selected team before opening checkout, and payment details and final confirmation stay on the hosted payment page. Refresh the wallet in Koder afterwards to see the new balance. Managing billing needs an eligible signed-in team role; an inference API key alone does not grant billing access.

## Configuration and updates

Put project instructions in `AGENTS.md` in your repository. Global configuration lives in `~/.config/koder/koder.json` or `koder.jsonc`, and sessions and other local state live under `~/.local/share/koder`. XDG environment settings can change these paths.

Update the CLI and check its version:

```sh
koder upgrade
koder --version
```

The desktop app checks for updates itself, or you can download the current installer. Upgrading keeps your sessions, saved permissions, schedules and theme. The `aixplain-code` command remains available as a compatibility alias.

## Get help

- [Report a bug](https://github.com/aixplain/koder/issues/new/choose) with your version, operating system, steps to reproduce and the result you expected. `koder report` saves a bug report with the session, recent logs and version.
- Read the [release notes](https://github.com/aixplain/koder/releases) for fixes and known limitations.
- For security reports, email **help@aixplain.com**. Remove credentials and private project data before sharing logs or screenshots.

This repository hosts Koder's public downloads and issue tracker. Koder is developed by [aixplain](https://aixplain.com).

## Copyright and licenses

**© 2026 aixplain Inc. All rights reserved.**

This notice applies to aixplain-owned branding and original material, subject to any express license grants. Third-party and upstream components retain their respective licenses, copyright notices, and permissions. See [LICENSE](LICENSE) and the notices included with each distribution.
