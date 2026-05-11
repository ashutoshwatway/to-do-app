# Taskboard — To-Do Manager with Google Drive sync

A clean, professional to-do list app that stores your tasks in your own Google Drive — so they're available on every device you sign into.

## Features

- **Google Sign-In** — tasks live in your Google Drive, not on any third-party server
- **Cross-device sync** — open the app on any device and your tasks are always up to date
- **Add tasks** with title, description, and due date
- **Mark done / Reopen** — close tasks and reopen any closed in error
- **Edit tasks** via an in-page modal
- **Overdue detection** — tasks past their due date are automatically flagged
- **Filter tabs** — All, Open, Overdue, Closed
- **Sort** by due date or creation date
- **Live header stats** — open / overdue / closed counts at a glance
- **Sync indicator** — shows Saving / Synced / Error in real time

---

## Setup (one-time, ~5 minutes)

### 1. Create a Google Cloud project and OAuth Client ID

1. Go to [console.cloud.google.com](https://console.cloud.google.com/)
2. Create a new project (or select an existing one)
3. Go to **APIs & Services → Library** and enable the **Google Drive API**
4. Go to **APIs & Services → Credentials → Create Credentials → OAuth client ID**
5. Choose **Web application**
6. Under **Authorised JavaScript origins** add:
   - Your deployed URL, e.g. `https://yourusername.github.io`
   - `http://localhost` (for local testing)
7. Click **Create** — copy the **Client ID** shown

### 2. Add your Client ID to the app

Open `index.html` and find this line near the bottom:

```javascript
const CLIENT_ID = 'YOUR_GOOGLE_CLIENT_ID';
```

Replace `YOUR_GOOGLE_CLIENT_ID` with the Client ID you just copied.

### 3. Configure the OAuth consent screen (if prompted)

In Google Cloud Console → **OAuth consent screen**:
- Set app name (e.g. "Taskboard")
- Add your email as a test user while in development
- Scopes: the app only requests `drive.file` (access only to files it creates itself)

---

## Deployment

### GitHub Pages (free)

1. Push this repository to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, `/ (root)`
4. Your app is live at `https://<username>.github.io/<repo>`
5. Make sure this URL is in your OAuth client's **Authorised JavaScript origins**

### Netlify (free, instant)

Drag the project folder to [app.netlify.com/drop](https://app.netlify.com/drop).

---

## How data is stored

When you sign in, the app creates a single file called `taskboard_data.json` in your Google Drive. All your tasks are stored there as JSON. The app requests only the `drive.file` scope — it can only see files it created itself, and cannot access any other files in your Drive.

---

## Project structure

```
todo-app/
├── index.html   # Complete app — HTML, CSS, JS in one file
└── README.md
```

## License

MIT
