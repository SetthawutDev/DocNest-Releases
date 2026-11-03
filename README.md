# DocNest

**Sync your Notion workspace to local Markdown files.**

DocNest is a macOS desktop application that mirrors Notion pages and their assets to your local filesystem, making your documentation easier to access, organize, and use with development tools and AI workflows.

Keep writing in Notion while DocNest maintains a local, read-only copy of your documentation.

[**Download DocNest v1.0.2**](https://github.com/SetthawutDev/DocNest-Releases/releases/tag/v1.0.2)

## Features

- **Notion to Markdown** — Synchronize Notion pages into locally stored Markdown files and assets.
- **Automatic Synchronization** — Keep your local documentation updated on a schedule.
- **Three Synchronization Modes** — Incremental, Refresh Hierarchy, and Full Sync.
- **Multiple Projects** — Manage and synchronize several Notion projects independently.
- **Background Operation** — Continue synchronization while the application runs in the background.
- **Update Checking** — Check official GitHub releases from Settings. Download and install updates manually.
- **Local Documentation Access** — Browse synchronized files using Finder, editors, and other local applications.

## V1.0.2 Performance

Measured using the 161-page AutoStone QA project:

| Sync mode | V1.0.1 | V1.0.2 |
|---|---|---|
| Full | 37 min | 16.5 min |
| Refresh Hierarchy | 10 min | 9 min |
| Incremental | 125 sec | 79 sec |

V1.0.2 reduces repeated filesystem recovery and Notion API requests, with faster storage operations and preserved synchronization correctness and data safety. These are rounded observations from separate QA runs; timing varies with project history, network conditions, and Notion response times. Incremental values are averages of three runs per version.

## Synchronization Modes

DocNest provides three synchronization modes. When Automatic Sync is enabled, their default intervals are:

| Mode | What it does | Default automatic interval |
|---|---|---|
| **Incremental** | Checks synchronized pages for changes and updates changed content and assets. New child pages found in changed pages are also synchronized. | Every **5 minutes** |
| **Refresh Hierarchy** | Rediscovers the Notion page hierarchy, updates the local folder structure, and synchronizes new or changed pages. | Every **15 minutes** |
| **Full Sync** | Performs a complete synchronization of the project hierarchy, page content, and assets to reconcile the local copy with Notion. | Every **24 hours** |

You can also run each mode manually.

## How It Works

1. Connect DocNest to Notion using an integration token.
2. Add the Notion pages or projects you want to synchronize.
3. Choose a local storage location.
4. Run Manual Sync or enable Automatic Sync.
5. Access the generated Markdown documentation on your Mac.

**Notion remains the source of truth.** DocNest mirrors Notion content locally rather than replacing Notion as your editing environment.

## Download

### DocNest v1.0.2

| Requirement | Support |
|---|---|
| Operating system | macOS 15.0 or later |
| Processor | Apple Silicon (ARM64) |
| Distribution | DMG installer |
| Code signing | Ad-hoc signed; not Apple notarized |
| Update checks | In-app GitHub checks; installation remains manual |

[**Download for macOS (Apple Silicon)**](https://github.com/SetthawutDev/DocNest-Releases/releases/download/v1.0.2/DocNest-1.0.2-arm64-local.dmg)

[View all releases](https://github.com/SetthawutDev/DocNest-Releases/releases) · Previous releases: [v1.0.1](https://github.com/SetthawutDev/DocNest-Releases/releases/tag/v1.0.1), [v1.0.0](https://github.com/SetthawutDev/DocNest-Releases/releases/tag/v1.0.0)

## Installation

1. Download the ARM64 DMG and `SHA256SUMS.txt` from the same release, then [verify the checksum](#verify-your-download).
2. If upgrading, quit DocNest normally and allow synchronization to stop. Back up important settings and mirrors.
3. Open the downloaded DMG and drag **DocNest.app** into **Applications**, replacing the older app when prompted.
4. Eject the DMG and open DocNest from Applications. Follow the security approval steps below if macOS blocks it.
5. Confirm Settings shows **1.0.2**. Existing users should keep their settings, mirrors, and Keychain items and confirm their projects before resuming synchronization. New users can connect Notion and select a storage location.

**V1.0.0 users must manually install V1.0.2 to gain update checking, introduced in V1.0.1.** Later updates also require manual installation; DocNest does not automatically download or replace the application.

### Important: macOS Security Notice

DocNest v1.0.2 is **ad-hoc signed and not notarized by Apple**. It has no Developer ID signature. Ad-hoc signing provides bundle integrity without Apple developer trust.

macOS Gatekeeper may prevent the application from opening automatically.

If you trust the downloaded application and have verified its checksum:

1. Attempt to open DocNest normally.
2. Open **System Settings → Privacy & Security**.
3. Find the blocked application notice.
4. If offered, select **Open Anyway** and follow the macOS confirmation prompts.

If Open Anyway is unavailable or the application still cannot open, report the issue with your macOS version. A clean-account, quarantined browser-download installation has not yet been verified.

Do not disable Gatekeeper globally.

## Connect to Notion

DocNest requires a Notion integration token to synchronize your pages.

1. Open **Notion → Settings → Connections**.
2. Enable **Developer Mode** and open **Personal access tokens** from the developer section in your sidebar.
3. Select **New connection**, give it a name, and choose your workspace.
4. Copy the integration token from the connection's **•••** menu and paste it into DocNest.
5. Open the Notion page you want to sync. Select **••• → More → Connections → Add connections** and choose your integration.

**Important:** Keep your integration token private. Make sure the connection has permission to access the pages you want to synchronize.

**Official Notion documentation:**

- [Create a Notion API connection](https://www.notion.com/help/create-integrations-with-the-notion-api)
- [Manage connections and page access](https://www.notion.com/help/add-and-manage-connections-with-the-api)

## Verify Your Download

The published ARM64 installer has the following SHA-256 checksum:

```text
1d4f3e9c4c70cd69acee94a330688ad9a3ddfc3bc7f6052eefc84f01820b95b6
```

Verify it using Terminal:

```bash
shasum -a 256 ~/Downloads/DocNest-1.0.2-arm64-local.dmg
```

The computed checksum must match the value above. If you downloaded both release assets into Downloads, you can also verify the checksum file:

```bash
cd ~/Downloads
shasum -a 256 -c SHA256SUMS.txt
```

Require `DocNest-1.0.2-arm64-local.dmg: OK` before installing.

[Download checksum file](https://github.com/SetthawutDev/DocNest-Releases/releases/download/v1.0.2/SHA256SUMS.txt)

## Known Limitations

- Intel-based Macs are not supported by the current release.
- Update checking is available in Settings; new versions must be downloaded and installed manually.
- Public GitHub API limits and offline conditions can prevent a check without blocking synchronization.
- DocNest requires a valid Notion connection to retrieve remote content.

## Feedback and Issues

Found a problem or have a suggestion?

[Report an issue](https://github.com/SetthawutDev/DocNest-Releases/issues)

When reporting bugs, include your macOS version, DocNest version, and steps to reproduce the problem. Do not include Notion tokens or private documentation.

## About This Repository

This repository hosts the official **DocNest macOS release binaries** and public release information.

The main application source code is maintained in a separate private repository.

---

**DocNest v1.0.2 — Faster synchronization with preserved data safety**
