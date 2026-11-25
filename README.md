# SwanDesk WorkPilot

The partner-edition WorkPilot for SwanDesk AI: a tool for companies that **purchase and resell** SwanDesk AI to
their own business customers. It is not for those end businesses (they get their own client dashboard on
SwanDesk AI itself) and it carries no WebSwan-internal branding or links -- no Voice Studio, no WebSwan admin.

Sign-in is a swan icon, not a labeled "Admin" button -- clicking it asks for the partner's own email (Google
sign-in). Only emails registered as a partner's admins (set up in SwanDesk AI's own admin, under B2B partners)
can see anything here; each partner sees only their own resold customers, never WebSwan's own clients or another
partner's.

Five sections, each scoped to the customer selected on the left:
1. **Call Tracking** -- calls logged by hand today (color-coded: yellow = spoke with the caller, blue = hung up
   without a conversation, green = booked an appointment), with a summary and an optional recording link. Once
   SwanDesk's own live calling (Jennifer, via Cartesia) is connected, the same shape can be filled in
   automatically instead of by hand.
2. **Appointments** -- bookings and scheduling, with status (scheduled / completed / canceled / rescheduled).
3. **Agent Assignments** -- assign a task straight to one of the customer's licensed SwanDesk agents, with
   instructions, tracked pending / in progress / done.
4. **Follow-ups** -- pending callbacks, emails and reminders, with a due date and a done checkbox.
5. **Customer Management** -- the customer's profile, agent licensing on/off, account on/off, a color tag, and a
   free-text note with interaction history (up to 5,000 characters).

- Page: this repo, served via GitHub Pages at `https://taniad2169.github.io/WS-Work-Pilot/`.
- Backend: `sd-workpilot.mjs` in the `Swan-Desk-AI` repo (deployed at `swandesk-ai.netlify.app`), which scopes
  every read and write to the signed-in partner's own customers -- the same scoping the partner portal
  (`/partner/`) already enforces. Agent-licensing and account on/off write to the real customer record (same
  audit log as `/admin/` and `/partner/`); everything else (calls, appointments, assignments, follow-ups, the
  profile note) is WorkPilot's own data and never touches that record.
- Sign-in: Google, same Firebase project as SwanDesk AI's own pages (`webswan-gigoia-task`) --
  `taniad2169.github.io` is already an authorized domain for that project, so no extra Firebase Console setup
  was needed.
