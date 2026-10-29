# APK Forge — Android Game Publishing Platform

A complete, full-stack Android APK game publishing platform built with React, TypeScript, Express, Three.js, and Firebase / Google Workspace Gmail integration.

## Primary Navigation Sections

1. **Panel** (`/panel`) — Password-protected administration area (`ADMIN_PANEL_PASSWORD`).
   - Locks immediately whenever the administrator navigates away from Panel, uses browser Back/Forward, refreshes the browser, opens a new tab, or backgrounds the page.
   - **Publish Game**: Publish validated `.apk` games directly to the public catalog, manage published/unpublished games (edit metadata, replace APK binaries safely, unpublish/republish, delete), and inspect the administrator audit log.
   - **Game Approvals**: Inspect user submissions, download submitted `.apk` packages for testing, approve submissions into `Apps`, reject submissions with optional explanations, or send custom correction requests (`Needs Changes`).
2. **Apps** (`/apps`) — Public Android game library.
   - Starts completely empty (`"No games published yet."`) with zero fake or placeholder games.
   - Displays deterministic generated application icons, version numbers, file sizes, publication dates, title search, and an interactive **3D Android APK Package Studio** built with Three.js.
   - Enforces verified user email authentication before downloading any `.apk` package, automatically resuming the intended download after sign-in.
3. **Add Apps** (`/add-apps`) — Developer APK submission form.
   - Requires a signed-in, email-verified user account.
   - Accepts only valid `.apk` archives (verifying ZIP `PK\x03\x04` header and `AndroidManifest.xml` presence on the server while rejecting `.zip`, `.exe`, `.msi`, `.aab`, `.ipa`, `.html`, etc.).
   - Saves uploaded APKs to private storage with `Pending` review status and supports replacing the APK when marked `Needs Changes`.

## Development & Testing

```bash
# Install dependencies
npm install

# Run unit and integration tests
npm test

# Start full-stack Express + Vite development server on port 3000
npm run dev

# Build for production
npm run build
```

## Security & Configuration

- Copy `.env.example` to `.env` and configure `ADMIN_PANEL_PASSWORD` (defaults to `arsam27` on the server as specified).
- Database and storage security rules for Firebase deployments are provided in `firestore.rules` and `storage.rules`.
