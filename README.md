# Vertriebsaufgaben

A lightweight sales todo tool — runs in the browser, stores data directly in OneDrive. No external database, no backend server, no subscriptions.

## Features

- Create, edit, and delete todos
- Priority levels: High / Medium / Low
- Mark todos as completed
- Deadline field — visible and editable directly on every card
- Smart deadline input: enter "in 5 Tagen" to auto-calculate working days (Bavarian public holidays excluded)
- Color-coded deadline status: overdue / due today / due soon / on track
- Filter by status, priority, and **due today**
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

- Microsoft account (Entra ID — lorenzsoft.de)
- Azure App Registration with the following settings:
  - Platform type: Single-page application (SPA)
  - Redirect URI: `https://antonella102.github.io/Vertriebsaufgaben/`
  - Supported account types: Single tenant (lorenzsoft.de)
  - Tenant ID configured in `index.html`

### Deployment

1. Upload `index.html` to this repository
2. Enable GitHub Pages: Settings → Pages → Branch: main
3. Open: `https://antonella102.github.io/Vertriebsaufgaben/`
4. Sign in with your Microsoft account (alorenz@lorenzsoft.de)

## Deadline Logic

Deadlines are calculated in **working days only**, excluding Bavarian public holidays:

- Neujahr, Heilige Drei Könige, Karfreitag, Ostermontag
- Tag der Arbeit, Christi Himmelfahrt, Pfingstmontag, Fronleichnam
- Mariä Himmelfahrt, Tag der Deutschen Einheit, Allerheiligen
- 1. + 2. Weihnachtstag

Color coding on each card:

| Color | Meaning |
|-------|---------|
| Red | Overdue |
| Orange | Due today |
| Blue | Due within 3 days |
| Green | On track |

## Importing Todos from Claude

When working in any Claude chat, say **"todo anlegen"** to trigger a todo entry. Claude will provide two formats:

**Quick paste:**
```
TODO: Follow up with client Müller | Prio: hoch
```

**JSON (multiple todos, with optional deadline):**
```json
[
  {"text": "Send proposal to Kanzlei Müller", "prio": "hoch", "days": 3},
  {"text": "Follow up Muster GmbH", "prio": "mittel", "deadline": "2026-04-01"}
]
```

The `days` field calculates the deadline in working days from today (Bavarian holidays excluded). The `deadline` field accepts an ISO date string (YYYY-MM-DD).

Open the tool → click **Import** → paste → done.

## License

Private use only.
