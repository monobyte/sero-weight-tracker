# @sero-ai/plugin-weight-tracker

Weight tracker app for Sero — track your progress, visualise trends, and stay
motivated with gentle encouragement.

## Sero Plugin Install

Install in **Sero → Admin → Plugins** with:

```text
git:https://github.com/monobyte/sero-weight-tracker.git
```

Sero clones the source repo, installs its dependencies locally, builds the UI,
and then hot-loads the plugin into the sidebar.

## Pi CLI Usage

Install as a Pi package:

```bash
pi install git:https://github.com/monobyte/sero-weight-tracker.git
```

The agent gains a `weight` tool (log, list, remove, goal, status, clear) and a
`/weight` command. State is stored in `.sero/apps/weight-tracker/state.json`
relative to the workspace root (or `~/.sero-ui/apps/weight-tracker/state.json`
when running inside Sero, since this is a global-scoped app).

## Sero Usage

When loaded in Sero, the web UI mounts in the main app area and watches
the same state file. Changes from the agent or the UI are reflected
instantly in both directions.

Features:
- **Log entries** — record weight with optional date and notes
- **Trend chart** — SVG line chart with gradient fill
- **Stats** — current weight, weekly change, total change, goal progress
- **Goal tracking** — set a target and see your progress bar fill up
- **Encouragement** — motivational messages based on your recent trends

## State File

This is a **global-scoped** app — in Sero, state lives at:

```
~/.sero-ui/apps/weight-tracker/state.json
```

In Pi CLI (no Sero), it falls back to workspace-relative:

```
workspace-root/.sero/apps/weight-tracker/state.json
```

```json
{
  "entries": [
    {
      "id": 1,
      "weight": 80.5,
      "date": "2025-01-01",
      "note": "Starting fresh!",
      "createdAt": "2025-01-01T09:00:00.000Z"
    }
  ],
  "nextId": 2,
  "unit": "kg",
  "goal": null
}
```

## Development

```bash
npm install
npm run dev          # Start Vite dev server (port 5176)
npm run build        # Build for production
npm run typecheck    # Typecheck UI sources
```
