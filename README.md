# SettDoc

**Sync your Notion workspace to local Markdown files.**

SettDoc is a macOS application that synchronizes Notion pages to local Markdown files for offline access, documentation management, and AI-powered developer workflows.

Keep writing in Notion while SettDoc maintains a local, read-only copy of your documentation.

Version **2.0.0** marks the official major rebranding milestone. This is a version-only update from v1.0.3, with unchanged application behavior, bundle identifier, profile directory, Keychain service and local mirror paths. No migration is required. All historical releases remain available.

[**Download SettDoc v2.0.0**](https://github.com/SetthawutDev/SettDoc-Releases/releases/tag/v2.0.0)

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

SettDoc provides three synchronization modes. When Automatic Sync is enabled, their default intervals are:

| Mode | What it does | Default automatic interval |
|---|---|---|
| **Incremental** | Checks synchronized pages for changes and updates changed content and assets. New child pages found in changed pages are also synchronized. | Every **5 minutes** |
| **Refresh Hierarchy** | Rediscovers the Notion page hierarchy, updates the local folder structure, and synchronizes new or changed pages. | Every **15 minutes** |
| **Full Sync** | Performs a complete synchronization of the project hierarchy, page content, and assets to reconcile the local copy with Notion. | Every **24 hours** |

You can also run each mode manually.

## How It Works

1. Connect SettDoc to Notion using an integration token.
2. Add the Notion pages or projects you want to synchronize.
3. Choose a local storage location.
4. Run Manual Sync or enable Automatic Sync.
5. Access the generated Markdown documentation on your Mac.

**Notion remains the source of truth.** SettDoc mirrors Notion content locally rather than replacing Notion as your editing environment.

## Download

### SettDoc v2.0.0

| Requirement | Support |
|---|---|
| Operating system | macOS 15.0 or later |
| Processor | Apple Silicon (ARM64) and Intel (x64) |
| Distribution | DMG installer |
| Code signing | Ad-hoc signed; not Apple notarized |
| Update checks | In-app GitHub checks; installation remains manual |

[**Download for macOS (Apple Silicon)**](https://github.com/SetthawutDev/SettDoc-Releases/releases/download/v2.0.0/SettDoc-2.0.0-arm64-local.dmg)

[**Download for macOS (Intel)**](https://github.com/SetthawutDev/SettDoc-Releases/releases/download/v2.0.0/SettDoc-2.0.0-x64-local.dmg)

[View all releases](https://github.com/SetthawutDev/SettDoc-Releases/releases) · Previous releases: [v1.0.3](https://github.com/SetthawutDev/SettDoc-Releases/releases/tag/v1.0.3), [v1.0.2](https://github.com/SetthawutDev/SettDoc-Releases/releases/tag/v1.0.2), [v1.0.1](https://github.com/SetthawutDev/SettDoc-Releases/releases/tag/v1.0.1), [v1.0.0](https://github.com/SetthawutDev/SettDoc-Releases/releases/tag/v1.0.0)

## Installation

1. Download the DMG matching your processor (ARM64 for Apple Silicon, x64 for Intel) and `SHA256SUMS.txt` from the same release, then [verify the checksum](#verify-your-download).
2. If upgrading, quit SettDoc normally and allow synchronization to stop. Back up important settings and mirrors.
3. Open the downloaded DMG and drag **SettDoc.app** into **Applications**, replacing the older app when prompted.
4. Eject the DMG and open SettDoc from Applications. Follow the security approval steps below if macOS blocks it.
5. Confirm Settings shows **2.0.0**. Existing users should keep their settings, mirrors, and Keychain items and confirm their projects before resuming synchronization. New users can connect Notion and select a storage location.

Updates require manual installation; SettDoc does not automatically download or replace the application.

### Important: macOS Security Notice

SettDoc v2.0.0 is **ad-hoc signed and not notarized by Apple**. It has no Developer ID signature. Ad-hoc signing provides bundle integrity without Apple developer trust.

macOS Gatekeeper may prevent the application from opening automatically.

If you trust the downloaded application and have verified its checksum:

1. Attempt to open SettDoc normally.
2. Open **System Settings → Privacy & Security**.
3. Find the blocked application notice.
4. If offered, select **Open Anyway** and follow the macOS confirmation prompts.

If Open Anyway is unavailable or the application still cannot open, report the issue with your macOS version. A clean-account, quarantined browser-download installation has not yet been verified.

Do not disable Gatekeeper globally.

## Connect to Notion

SettDoc requires a Notion integration token to synchronize your pages.

1. Open **Notion → Settings → Connections**.
2. Enable **Developer Mode** and open **Personal access tokens** from the developer section in your sidebar.
3. Select **New connection**, give it a name, and choose your workspace.
4. Copy the integration token from the connection's **•••** menu and paste it into SettDoc.
5. Open the Notion page you want to sync. Select **••• → More → Connections → Add connections** and choose your integration.

**Important:** Keep your integration token private. Make sure the connection has permission to access the pages you want to synchronize.

**Official Notion documentation:**

- [Create a Notion API connection](https://www.notion.com/help/create-integrations-with-the-notion-api)
- [Manage connections and page access](https://www.notion.com/help/add-and-manage-connections-with-the-api)

## Verify Your Download

Download `SHA256SUMS.txt` alongside the installer matching your processor. From that directory, run:

```bash
shasum -a 256 -c SHA256SUMS.txt --ignore-missing
```

Require your selected installer to report `OK`. The published installer checksums are:

```text
e4c62cf4c982849403353f17a0db2d17be071440b50973f6e66376d246926d39  SettDoc-2.0.0-arm64-local.dmg
b9305c10227d6c46568cee9ee39919cb6103591ea62185bafa60f7ee8aaaa29f  SettDoc-2.0.0-x64-local.dmg
```

[Download checksum file](https://github.com/SetthawutDev/SettDoc-Releases/releases/download/v2.0.0/SHA256SUMS.txt)

## Known Limitations

- Update checking is available in Settings; new versions must be downloaded and installed manually.
- On Intel Macs, new versions are detected; use the release page to download the Intel installer. The existing in-app download action supports Apple Silicon only.
- Public GitHub API limits and offline conditions can prevent a check without blocking synchronization.
- SettDoc requires a valid Notion connection to retrieve remote content.

## Feedback and Issues

Found a problem or have a suggestion?

[Report an issue](https://github.com/SetthawutDev/SettDoc-Releases/issues)

When reporting bugs, include your macOS version, SettDoc version, and steps to reproduce the problem. Do not include Notion tokens or private documentation.

## About This Repository

This repository hosts the official **SettDoc macOS release binaries** and public release information.

The main application source code is maintained in a separate private repository.

---

**SettDoc v2.0.0 — Official major rebranding milestone; unchanged v1.0.3 behavior and data**
