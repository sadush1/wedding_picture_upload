# Wedding Photo Upload — Setup Guide

Two pieces: a Google Apps Script backend (saves photos to your Drive) and a
GitHub Pages front end (the page guests see when they scan the QR code).

## 1. Create your Drive folder

1. In Google Drive, create a folder, e.g. "Wedding Photos".
2. Open it and copy the ID from the URL:
   `https://drive.google.com/drive/folders/`**`THIS_PART`**

## 2. Deploy the backend (Code.gs)

1. Go to [script.google.com](https://script.google.com) → **New project**.
2. Delete the placeholder code and paste in `Code.gs`.
3. Replace `YOUR_FOLDER_ID_HERE` with the folder ID from step 1.
4. Click **Deploy → New deployment → Web app**.
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Authorize when prompted, then copy the **Web app URL** it gives you.

## 3. Connect the front end (index.html)

1. Open `index.html`, find `YOUR_APPS_SCRIPT_WEB_APP_URL_HERE`, and paste in
   the Web app URL from step 2.
2. Optionally edit:
   - The monogram (`A & B`) and date near the top of the `<body>`.
   - The invitation text.

## 4. Host it on GitHub Pages

1. Create a new GitHub repo (e.g. `wedding-photos`).
2. Upload `index.html` to it (no need to include `Code.gs` — that one lives
   only in Apps Script).
3. Go to **Settings → Pages**, set source to the `main` branch, root folder.
4. GitHub gives you a URL like:
   `https://yourusername.github.io/wedding-photos/`

## 5. Generate the QR code

Paste your GitHub Pages URL into any QR generator (e.g.
qr-code-generator.com) and download the image — that's what you print or
put on table cards.

## 6. Test before the big day

- Scan the QR code with your own phone on mobile data (not the same wifi
  you're deploying from).
- Upload a couple of test photos and confirm they land in your Drive folder,
  named like `GuestName_20260920_143012_photo.jpg`.
- Delete the test photos afterward.

## Notes

- There's no file-count or storage limit built into the page beyond your own
  Google Drive storage.
- All uploads run through your own Apps Script under your own Google
  account — nobody needs to sign in to upload.
- If you want photos automatically organized into per-guest subfolders
  instead of one flat folder, let me know — it's a small change to `Code.gs`.
