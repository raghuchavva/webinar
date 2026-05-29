# Webinar Registration Form

A simple form that collects **Parent Name, Parent Number, Student Name, Student Number**,
saves them to a **Google Sheet**, and then redirects the user to your **Google Meet** webinar.

The Meet link is stored in a sheet cell, so **anyone (non-coder) can change it** anytime.

---

## Files
- `index.html` — the form the user fills in
- `Code.gs` — the Google Apps Script backend (saves data + returns the Meet link)

---

## One-time setup (≈10 minutes)

### 1. Create the Google Sheet
1. Go to https://sheets.google.com and create a new blank spreadsheet.
2. Name it e.g. **Webinar Registrations**.

### 2. Add the script
1. In the sheet menu, click **Extensions → Apps Script**.
2. Delete any sample code, then paste in the entire contents of `Code.gs`.
3. Click the **Save** (💾) icon.

### 3. Deploy as a Web App
1. In the Apps Script editor, click **Deploy → New deployment**.
2. Click the gear icon ⚙ next to "Select type" → choose **Web app**.
3. Set:
   - **Description:** Webinar form
   - **Execute as:** *Me*
   - **Who has access:** *Anyone*   ← important
4. Click **Deploy**, authorize when prompted (choose your account → Advanced → Allow).
5. Copy the **Web app URL** (ends in `/exec`).

### 4. Connect the form
1. Open `index.html`.
2. Find this line near the bottom:
   ```js
   const SCRIPT_URL = "PASTE_YOUR_WEB_APP_URL_HERE";
   ```
3. Replace the placeholder with the Web app URL you copied. Save.

### 5. Set the Meet link
1. Run the form once (or just open the Web app URL in a browser). This auto-creates
   two tabs in your sheet: **Registrations** and **Config**.
2. Open the **Config** tab. In cell **B1** you'll see a placeholder Meet link.
3. Paste your real Google Meet link there. Done.

---

## How a non-coder updates the Meet link later
Just open the Google Sheet → **Config** tab → change cell **B1** to the new link.
No code, no redeploy. The form picks it up automatically.

---

## How to run / share the form
- **Test locally:** double-click `index.html` to open it in a browser.
- **Share with others:** host `index.html` anywhere free — e.g.
  Google Sites, Netlify Drop (drag-and-drop), GitHub Pages, or your own site.

---

## Data captured
Each submission adds a row to the **Registrations** tab:

| Timestamp | Parent Name | Parent Number | Student Name | Student Number |
|-----------|-------------|---------------|--------------|----------------|

> **Note:** If you ever change `Code.gs`, you must redeploy:
> **Deploy → Manage deployments → ✏ Edit → Version: New version → Deploy.**
> (Updating only the Meet link in the sheet does **not** require this.)
