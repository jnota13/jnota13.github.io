# Taper Planner (personal experiment)

A local-first, installable Progressive Web App for recording alcohol intake, viewing an experimental schedule, and logging daily symptoms. This is a personal software experiment, **not a clinically validated withdrawal-management tool**.

## What's included

- Responsive mobile-first interface with system/light/dark theme selection.
- Local browser storage; no account, analytics, or app-owned server.
- U.S. standard-drink conversion labels and explicit units in schedule tables.
- Daily symptom check-ins and a schedule view.
- JSON export and restore for moving/backing up data.
- Optional best-effort browser notifications while the app is open.
- PWA install metadata, offline cache, install prompt where supported, and service-worker update versioning.
- Emergency guidance and links to NIAAA and ASAM references.

## Use it locally (no GitHub required)

The most straightforward way to try it on a computer is to serve the folder over localhost. From this directory, run:

```bash
python -m http.server 8000
```

Then open `http://localhost:8000` in a modern browser. Service workers and notifications require a secure context; `localhost` is treated as secure by modern browsers. Keep the terminal open while testing. To stop the server, press `Ctrl+C`.

On Android, a static web app generally needs to be served over HTTPS to install and use service workers reliably. You can use a static host such as GitHub Pages, Cloudflare Pages, or Netlify; no backend or build step is required. Upload the *contents* of this repository, preserving the file names and directory structure. Open the HTTPS URL in Chrome and use the browser menu's **Install app** or **Add to Home screen** option if the in-app Install button is not available.

## Notifications: important limitation

The reminder feature asks for notification permission and can show a daily check-in notification when the app is running/open and notices the selected time has passed. It also checks when the page regains focus. **It cannot reliably wake a fully closed or suspended app at a scheduled time.** Reliable closed-app scheduled notifications typically require a push service and a server-side scheduler; this repository intentionally has no server or push subscription backend. Browser/OS battery settings can also delay notifications. The feature is optional; the daily check-in remains available inside the app.

## Privacy and backups

- App data is stored in this browser's `localStorage` on this device/profile.
- Clearing site data, uninstalling, using a different browser/profile, or switching devices may remove or make the data unavailable.
- Use **Safety → App settings & backup → Export backup (.json)** before changing devices or clearing browser data.
- A backup includes sensitive personal information. Treat it like a private health record and do not upload it to a public repository.
- There is no synchronization or recovery service. The developer of this app cannot retrieve local data.

## Medical and safety limitation

Alcohol withdrawal can be life-threatening. The app's pace options, step durations, and automatic risk categories are experimental rules, not a validated clinical protocol. A “low” result does not establish that unsupervised reduction is safe. Do not use generated amounts as a substitute for an individualized assessment by a qualified healthcare professional. For seizures, hallucinations, confusion, severe symptoms, trouble breathing, chest pain, or other emergencies, call emergency services. In the U.S., SAMHSA's National Helpline is **1-800-662-HELP (4357)**.

References:

- NIAAA, standard drink definition: <https://www.niaaa.nih.gov/health-professionals-communities/core-resource-on-alcohol/basics-defining-how-much-alcohol-too-much>
- ASAM, Alcohol Withdrawal Management Clinical Practice Guideline: <https://www.asam.org/quality-care/clinical-guidelines/alcohol-withdrawal-management-guideline>
- MDN, PWA installation: <https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable>
- MDN, Notifications API: <https://developer.mozilla.org/en-US/docs/Web/API/Notifications_API>

## Test checklist

- [ ] Open Setup, change fields, reload, and confirm values persist.
- [ ] Switch System → Light → Dark → System theme.
- [ ] Export a backup, change data, restore the backup, and confirm plan/check-ins return.
- [ ] Allow notifications and use Test reminder on HTTPS or localhost.
- [ ] Enable a reminder for a few minutes ahead and keep the app open to test best-effort delivery.
- [ ] Install the PWA, disconnect network, and verify cached app shell opens.
- [ ] On a test copy only, erase local app data and verify reset behavior.

This is a static app; no package manager or compilation is required.
