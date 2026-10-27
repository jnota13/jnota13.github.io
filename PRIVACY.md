# Privacy notes

The app does not intentionally transmit app state to a server. State is stored in browser `localStorage`; reminder preferences are stored there separately. Browser extensions, device access, shared profiles, browser backups, or exported JSON files can expose data. Do not commit a personal backup file to a repository.

Notifications are generated locally when the page is active and permission is granted. There is no remote push server or push subscription in this version.
