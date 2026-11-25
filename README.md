# WS-Work-Pilot

SwanDesk AI's own WorkPilot: a board of SwanDesk's real clients (agent licensing, account on/off, a per-client
note and color tag) plus a general to-do list, built the same way The WebSwan's own WorkPilot (`daily-task`)
links to Voice Studio -- a static GitHub Pages page talking to a live Netlify backend.

- Page: this repo, served via GitHub Pages at `https://taniad2169.github.io/WS-Work-Pilot/`.
- Backend: `sd-workpilot.mjs` in the `Swan-Desk-AI` repo (deployed at `swandesk-ai.netlify.app`), which reuses
  the same client records and owner-only Google sign-in as SwanDesk's own `/admin/` page. A WorkPilot note/color
  is stored separately and never touches the real client record; the account on/off and agent-licensing switches
  write to the same real record `/admin/` does, with the same audit log.
- Sign-in: Google, same Firebase project as SwanDesk AI and the original WorkPilot (`webswan-gigoia-task`) --
  `taniad2169.github.io` is already an authorized domain for that project, so no extra Firebase Console setup
  was needed.

The previous `index.html` here was a stray save of the Codex/ChatGPT web app itself (its own auth config and
task history), not an application -- replaced outright rather than "cleaned up", since there was no real app in
it to clean.
