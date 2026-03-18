# Vertriebsaufgaben

A lightweight sales todo tool — runs in the browser, stores data directly in OneDrive. No external database, no backend server, no subscriptions.

## Features

- Create, edit, and delete todos
- Priority levels: High / Medium / Low
- Mark todos as completed
- Filter by status and priority
- Import todos from Claude chat (quick paste or JSON)
- Automatic sync to OneDrive after every change
- Mobile-friendly responsive design
- Automatic dark mode

## Tech Stack

- Plain HTML / CSS / JavaScript — no framework, no build process
- [MSAL Browser](https://github.com/AzureAD/microsoft-authentication-library-for-js) for Microsoft login
- Microsoft Graph API for OneDrive read/write
- Hosted via GitHub Pages

## Data Storage

Todos are stored as `Vertrieb-Todos.json` in the root of your personal OneDrive. Data never leaves Microsoft infrastructure.

## Setup

### Prerequisites

- Microsoft account (Entra ID or personal)
- Azure App Registration with the following settings:
  - Platform type: Single-page application (SPA)
  - Redirect URI: `https://antonella102.github.io/Vertriebsaufgaben/`
  - Supported account types: Single tenant

### Deployment

1. Upload `index.html` to this repository
2. Enable GitHub Pages: Settings → Pages → Branch: main
3. Open: `https://antonella102.github.io/Vertriebsaufgaben/`
4. Sign in with your Microsoft account

## Importing Todos from Claude

When working in any Claude chat, say **"todo anlegen"** to trigger a todo entry. Claude will provide two formats:

**Quick paste:**
```
TODO: Follow up with client Müller | Prio: hoch
```

**JSON (multiple todos at once):**
```json
[
  {"text": "Send proposal to Kanzlei Müller", "prio": "hoch"},
  {"text": "Follow up Muster GmbH", "prio": "mittel"}
]
```

Open the tool → click **Import** → paste → done.

## License

Private use only.
