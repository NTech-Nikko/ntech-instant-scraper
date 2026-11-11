# NTech Instant Scraper — Android PWA package

This is a static Progressive Web App (PWA) package for Netlify.

## Files
- `index.html` — NTech dashboard
- `manifest.webmanifest` — installable app metadata
- `sw.js` — offline app-shell cache
- `ntech-icon-192.png`, `ntech-icon-512.png` — Home Screen icons
- `_headers`, `netlify.toml` — correct Netlify headers and publish directory

## Deploy using only an Android tablet

Recommended path: GitHub repository connected to Netlify. This avoids needing a PC or command line.

1. Download and extract `NTech_Instant_Scraper_PWA.zip` using the Android Files app.
2. Create/sign in to GitHub at https://github.com/ and create a new repository named `ntech-instant-scraper`. A private repository is fine if Netlify is authorized to access it.
3. In the repository, choose **Add file → Upload files**. Upload all package files from the extracted folder, including the two PNG icons. Make sure `index.html`, `manifest.webmanifest`, and `sw.js` are at the repository root, not inside an extra nested folder. Commit the upload to the `main` branch.
4. Open https://app.netlify.com/start, choose GitHub, authorize Netlify, and select `ntech-instant-scraper`.
5. For this static site, use publish directory `.` and leave build command blank. Click Deploy.
6. Open the generated `*.netlify.app` address in Chrome on the tablet.
7. In Chrome, tap **⋮ → Install app** or **Add to Home screen**, then confirm. Menu wording varies by Chrome version.

## Connect Google Sheets

1. Open the Google Sheet where leads should be stored.
2. Open Extensions → Apps Script.
3. Paste the supplied `Code.gs` backend code into the Apps Script editor and save.
4. Deploy → New deployment → Web app. Execute as your account; set access to the audience you intend to authorize (the dashboard's JSONP client requires a publicly reachable web-app endpoint; do not put sensitive data in a publicly accessible deployment).
5. Copy the `/exec` URL into the dashboard's Apps Script Web App URL field, enter the sheet tab name (default `Leads`), then Save connection and Test connection.

## Offline behavior and limits
- The app shell is cached by the service worker after the first successful online visit.
- Lead records and endpoint/sheet settings are saved in this browser's local storage.
- Dashboard, saved records, and settings can be reopened offline after the first successful load.
- Website scraping and Google Sheets export require internet.
- Clearing Chrome site data, uninstalling/clearing the app's storage, or using another browser/profile can remove local records. Export important leads to Sheets/CSV regularly.
- The bookmarklet extracts only the currently loaded public page and may be blocked by Chrome or the target website. Sharing/pasting a URL is the more reliable Android workflow.
- PWA is an installable web app, not a native APK.
