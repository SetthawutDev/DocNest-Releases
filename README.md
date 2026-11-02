# DocNest

**Sync your Notion workspace to local Markdown files.**

DocNest is a macOS desktop application that mirrors Notion pages and their assets to your local filesystem, making your documentation easier to access, organize, and use with development tools and AI workflows.

Keep writing in Notion while DocNest maintains a local, read-only copy of your documentation.

[**Download DocNest v1.0.0**](https://github.com/SetthawutDev/DocNest-Releases/releases/tag/v1.0.0)

## Features

- **Notion to Markdown** — Synchronize Notion pages into locally stored Markdown files and assets.
- **Automatic Synchronization** — Keep your local documentation updated on a schedule.
- **Three Synchronization Modes** — Incremental, Refresh Hierarchy, and Full Sync.
- **Multiple Projects** — Manage and synchronize several Notion projects independently.
- **Background Operation** — Continue synchronization while the application runs in the background.
- **Local Documentation Access** — Browse synchronized files using Finder, editors, and other local applications.

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

### DocNest v1.0.0

| Requirement | Support |
|---|---|
| Operating system | macOS 15.0 or later |
| Processor | Apple Silicon (ARM64) |
| Distribution | DMG installer |
| Code signing | Unsigned |
| Automatic updates | Not available in v1.0.0 |

[**Download for macOS (Apple Silicon)**](https://github.com/SetthawutDev/DocNest-Releases/releases/download/v1.0.0/DocNest-1.0.0-arm64-local.dmg)

[View all releases](https://github.com/SetthawutDev/DocNest-Releases/releases)

## Installation

1. Download the DMG installer.
2. Open the downloaded DMG.
3. Drag **DocNest.app** into the **Applications** folder.
4. Open DocNest from Applications.
5. Connect your Notion integration and configure your local storage location.

### Important: macOS Security Notice

DocNest v1.0.0 is currently **unsigned and not notarized by Apple**.

macOS Gatekeeper may prevent the application from opening automatically.

If you trust the downloaded application and have verified its checksum:

1. Attempt to open DocNest normally.
2. Open **System Settings → Privacy & Security**.
3. Find the blocked application notice.
4. Select **Open Anyway** and follow the macOS confirmation prompts.

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
933d3dc4b8bb8e36cc50bc5d6e790a3854382c4b196ff2e225fe1bfc63dec7f3
```

Verify it using Terminal:

```bash
shasum -a 256 ~/Downloads/DocNest-1.0.0-arm64-local.dmg
```

The computed checksum must match the value above.

[Download checksum file](https://github.com/SetthawutDev/DocNest-Releases/releases/download/v1.0.0/SHA256SUMS.txt)

## Known Limitations

- Intel-based Macs are not supported by the current release.
- Automatic application updates are not yet available.
- New versions must be installed manually.
- DocNest requires a valid Notion connection to retrieve remote content.

## Feedback and Issues

Found a problem or have a suggestion?

[Report an issue](https://github.com/SetthawutDev/DocNest-Releases/issues)

When reporting bugs, include your macOS version, DocNest version, and steps to reproduce the problem. Do not include Notion tokens or private documentation.

## About This Repository

This repository hosts the official **DocNest macOS release binaries** and public release information.

The main application source code is maintained in a separate private repository.

---

**DocNest v1.0.0 — First macOS Release**
