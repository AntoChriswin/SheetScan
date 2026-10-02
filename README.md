# SheetScan

SheetScan is a mobile-first barcode scanning application that reads and updates Google Sheets directly.

## Features

- Google authentication
- Google Sheets integration
- Spreadsheet selection
- Worksheet selection
- Spreadsheet row/column viewing
- Camera barcode scanning
- Barcode image upload
- Exact-cell barcode updates
- History
- Settings
- Mobile-responsive interface

## Tech Stack

- React
- Vite
- Tailwind CSS
- Firebase (Authentication)
- Google Sheets API
- @zxing/library (Barcode Scanning)

## Local Development

```bash
npm install
npm run dev
```

## Production Build

```bash
npm run build
```

## Environment Variables

The application requires the following environment variables (defined in `.env.example`):

- `VITE_FIREBASE_PROJECT_ID`: Firebase Project ID
- `VITE_FIREBASE_APP_ID`: Firebase Application ID
- `VITE_FIREBASE_API_KEY`: Firebase API Key
- `VITE_FIREBASE_AUTH_DOMAIN`: Firebase Auth Domain
- `VITE_FIREBASE_STORAGE_BUCKET`: Firebase Storage Bucket
- `VITE_FIREBASE_MESSAGING_SENDER_ID`: Firebase Messaging Sender ID
- `VITE_FIREBASE_MEASUREMENT_ID`: Firebase Measurement ID
- `VITE_FIREBASE_OAUTH_CLIENT_ID`: Google OAuth Client ID

## Firebase Setup

To prevent `auth/unauthorized-domain` errors in production, you must whitelist your Vercel domain in Firebase:
1. Go to the [Firebase Console](https://console.firebase.google.com/).
2. Select your project (`gen-lang-client-0699091087`).
3. Click on **Authentication** in the left sidebar.
4. Go to the **Settings** tab.
5. Click on **Authorized domains**.
6. Click **Add domain** and enter your Vercel production URL (e.g., `sheetscan-xxx.vercel.app`). Do not include `https://`.

## Google Cloud Setup

To run this application, you must configure a project in the Google Cloud Console with the following:

1. Enable the **Google Sheets API**.
2. Configure the **OAuth Consent Screen**.
3. Create an **OAuth 2.0 Client ID** (Web application).

### Production Setup

In the Google Cloud Console for your OAuth Client ID, you must configure:

**Authorized JavaScript origins:**
- `https://<your-vercel-domain>`

**Authorized redirect URIs:**
- `https://<your-vercel-domain>`

## Vercel Deployment

1. Import GitHub repository into Vercel.
2. Select framework as **Vite**.
3. Configure environment variables (add all `VITE_FIREBASE_*` variables from above).
4. Deploy.
5. Add the generated Vercel production URL to your Google OAuth configuration (Authorized JavaScript origins & Redirect URIs).
6. Redeploy if required.
