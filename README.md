# BugNotes

<p align="center">
  <img alt="BugNotes logo" src="https://img.shields.io/badge/BugNotes-field%20notes%20for%20bug%20hunters-2f6b52?style=for-the-badge&logo=github&logoColor=white" />
</p>

<p align="center">
  <a href="https://unrealsrabon.github.io/bugnotes">Live demo</a> ·
  <a href="#features">Features</a> ·
  <a href="#github-sync">GitHub sync</a> ·
  <a href="#setup">Setup</a>
</p>

<div align="center">
  <table>
    <tr>
      <td align="center" width="33%">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <path d="M4 6h16M4 12h10M4 18h16" stroke="#3f6b52" stroke-width="2" stroke-linecap="round"/>
        </svg>
        <br />
        Recon-first notes
      </td>
      <td align="center" width="33%">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <path d="M12 3v18M3 12h18" stroke="#a97c2f" stroke-width="2" stroke-linecap="round"/>
        </svg>
        <br />
        Fast capture workflow
      </td>
      <td align="center" width="33%">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden="true">
          <path d="M7 12l3 3 7-7" stroke="#a8493c" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
        <br />
        Local and GitHub sync
      </td>
    </tr>
  </table>
</div>

## Overview

BugNotes is a browser-based markdown notebook built for bug hunters, security researchers, and anyone who needs to move quickly from recon to findings without losing context. It gives you a focused workspace for writing notes, tracking endpoints, recording payloads, and keeping evidence in one place. The app runs entirely in the browser and can optionally sync notes to a private GitHub repository.

The project is deployed here:

- Live site: [unrealsrabon.github.io/bugnotes](https://unrealsrabon.github.io/bugnotes)

## What It Is For

Bug hunting work is messy by nature. You collect URLs, requests, parameters, screenshots, payloads, and small observations that later become a report. BugNotes is designed to keep that flow lightweight:

- Capture findings while you are still in recon mode.
- Keep notes in markdown so they stay portable and easy to read.
- Search quickly when you need to find a host, endpoint, or payload.
- Sync to GitHub when you want durable storage and an audit trail.

## Features

### Note workspace

- Markdown editor with line numbers, wrapping, active line highlighting, and a clean writing surface.
- Note titles are derived from the content or the title field, then converted into slug-style markdown filenames.
- One-click note creation, deletion, and selection from a sidebar list.
- Unsaved changes are clearly marked in the UI.
- Keyboard save support with `Ctrl/Cmd + S`.

### Storage and persistence

- Notes save locally in the browser using `localStorage`.
- Local-only notes remain available after refresh.
- Unload protection warns you if you are about to leave with unsaved work.

### GitHub sync

- Connect to a private or public GitHub repository through the GitHub REST API.
- Sync notes stored under a `notes/` folder in the repo.
- Load existing note files from GitHub and merge them with local-only notes.
- Create, update, rename, and delete note files through GitHub once connected.
- Sync status is shown directly in the header so you always know whether you are local-only or online.

### Interface details

- Collapsible sidebar for a tighter focus mode.
- Dedicated GitHub connection panel with username, repository, branch, and token fields.
- Inline status messages for connection, save, delete, and sync events.
- SVG icon-based buttons throughout the interface.

## How It Works

BugNotes keeps a simple mental model:

1. A note exists as a markdown file name plus content.
2. If GitHub sync is not configured, the note lives locally in the browser.
3. If GitHub sync is configured, the app reads and writes the note inside the configured repository.
4. The sidebar is the source of truth for navigating between notes.

This makes the app easy to use during active research, where you want fewer screens and less ceremony.

## GitHub Sync

To enable syncing, provide:

- GitHub username
- Repository name
- Branch name, usually `main`
- Personal access token

Notes are stored in the browser only for this session and are not sent anywhere else unless you connect GitHub. The token is stored in `localStorage` inside your browser so the app can reconnect automatically later.

### Required token access

- For private repositories, the token needs `repo` scope.
- For public repositories, use a token that can read and write contents as needed.

### GitHub folder structure

BugNotes expects note files in:

```text
notes/*.md
```

If the folder does not exist yet, the app will create files there when you save.

## Recommended Workflow

1. Create a new note while you are collecting scope and targets.
2. Use the editor to document requests, parameters, interesting responses, and proof.
3. Save early and often with `Ctrl/Cmd + S`.
4. Rename the note by changing the title content and saving again.
5. Connect GitHub when you want the notes mirrored to a repo.
6. Keep your findings organized by target, endpoint, or issue type.


## Browser Behavior

- Notes, settings, and sidebar state are remembered in `localStorage`.
- The editor uses CodeMirror for the markdown writing experience.
- Markdown preview is handled in the app shell through the existing editor workflow.
- The app warns before closing a tab if there are unsaved changes.

## Best Fit Use Cases

- Bug bounty recon notes
- Vulnerability writeups
- Target scope tracking
- Payload experimentation
- Request/response observations
- Report drafting

## Short Version

BugNotes is a focused, browser-first markdown notebook for bug hunters. It keeps recon notes, findings, and GitHub sync in one place, with a fast interface that stays out of the way while you work.
