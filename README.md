# Leave approval

A small web app for leave requests. Staff apply for leave and the admin approves or rejects it.

- Front end: one static page (`index.html`), hosted on Vercel
- Login, data and file storage: Supabase (tables are prefixed `leave_`)
- Creating accounts, resetting passwords and deactivating people: Supabase Edge Function `leave-admin`

## How it works

- Only the admin creates accounts. There is no public sign-up. A login that has no leave profile gets a "No access yet" screen.
- Leave can be applied for in full days or half days. Weekends and the public holidays listed under Settings are not counted.
- A request can't overlap another pending or approved request, can't go over the person's balance, and can't span two calendar years. These rules are enforced in the database.
- Staff see only their own requests. The admin sees everything.
- Attachments (such as medical certificates) go in a private storage bucket. Only the person and the admin can open them.

## Still to do

- Outlook sync: create an event on the shared team calendar when leave is approved, using Microsoft Graph. `leave_requests.outlook_event_id` is already in place to store the event ID.
