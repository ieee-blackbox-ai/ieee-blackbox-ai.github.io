# ieee-blackbox-ai.github.io

Public event site for **BLACKBOX AI 1.0 — Reverse Engineer the Intelligence**
IEEE Student Branch, Geethanjali College of Engineering and Technology (GCET) · 6–7 October 2026

**Live at:** https://ieee-blackbox-ai.github.io

## Enabling GitHub Pages

This repository is named `ieee-blackbox-ai.github.io`, which makes it the **organisation site**
for the `ieee-blackbox-ai` org — it serves from the org root rather than a subpath.

1. Create the repo in the org with this exact name (the name is what makes it the org site).
2. Push this folder to `main`.
3. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch `main`, folder `/ (root)`.
4. The site goes live at `https://ieee-blackbox-ai.github.io` within a minute or two.

The repository **must be public** for Pages to serve on a free organisation account.
Nothing sensitive belongs here — see below.

## Contents

| File | Purpose |
|---|---|
| `index.html` | Event site — premise and demo, the rounds, IEEE Day, prizes, FAQ, about IEEE, registration |
| `leaderboard.html` | Round-wise standings, renders `leaderboard.json` and re-checks it every minute |
| `leaderboard.json` | Publish target, overwritten by an export from the competition server |
| `.nojekyll` | Skips Jekyll processing; the site is plain static HTML |

No build step, no dependencies. Edit the HTML and push.

## Publishing standings

After a round is frozen and published, the organiser presses **Push to public site**
in the admin console. The competition server writes `leaderboard.json` and commits it
here itself, using the organiser laptop's GitHub sign-in:

```json
{
  "event": "BLACKBOX AI 1.0",
  "generated_at": "2026-10-06T20:00:00+05:30",
  "published_round": "R1",
  "rounds": [
    { "code": "R1", "name": "Round 1 — Observe",
      "standings": [
        { "rank": 1, "team": "BB-017", "name": "Kernel Panic", "score": 87.4, "qualified": true }
      ] }
  ]
}
```

Pages rebuilds within a minute or two, and an open standings page picks the new file
up on its own - it checks once a minute. If the laptop has no internet, **Download
leaderboard.json** in the admin console and commit it here by hand from any machine.
The placeholder state stands on its own while the file is empty, so a failed publish
degrades gracefully. Team names are chosen by teams; the page escapes everything it
renders.

## What must never be committed here

This repo is public. Do not add: query budgets before a round opens, challenge families or
instance details, team credentials, server IPs or ports, score component breakdowns, or
anything exported from the competition database beyond the five standings fields above
(rank, team code, team name, score, qualified).

## Related repositories

| Repo | Visibility | Contents |
|---|---|---|
| `blackbox-platform` | private | competition server, admin console, challenge generators |
| `blackbox-ai-participant-template` | private until the event starts, then public | team repo skeleton that teams fork |
| `judging-guide` | private | rubric and marking notes for the judges |

---

Registration: https://forms.gle/jHEKp6DjR2aQTuyM7
