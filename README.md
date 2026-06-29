# Steadbook — Landing page

The public marketing / "coming soon" landing page for **Steadbook**, the diversified
small-farm logbook for iPhone & iPad.

It's a single self-contained static page — no build step, no dependencies. Just open it.

## Structure

```
index.html        The whole page: markup, inlined CSS (Greenhouse design tokens), and a
                  small vanilla-JS script (theme toggle + screenshot swap + mock signup).
screenshots/      App screenshots, 5 screens × dark/light (referenced as <screen>-<theme>.png).
.nojekyll         Tells GitHub Pages to serve files as-is (no Jekyll processing).
```

## Develop

Open `index.html` directly, or serve the folder so relative paths resolve cleanly:

```sh
python3 -m http.server
# then visit the printed http://localhost:8000
```

Light/dark theme toggles in the nav and is remembered via `localStorage`.

## Deploy (GitHub Pages)

Push to GitHub, then in the repo: **Settings → Pages → Build and deployment →
Source: Deploy from a branch**, branch `main`, folder `/ (root)`. The site publishes at
`https://<user>.github.io/<repo>/`.

## Notes

- The "Notify me" email form is a front-end mock — it shows a success message but does not
  send anything. Wire it to a real endpoint (e.g. a form service) before launch.
- The design comes from the Steadbook Claude Design project; see `CLAUDE.md` for how to
  re-sync if the source design changes.
