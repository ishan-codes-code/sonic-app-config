# Sonic App Configuration

This repository hosts the remote configuration for the Sonic Music App. It is used to manage app updates, force requirements, and system messages without needing a backend deployment or app store resubmission.

## 🚀 CDN Access

The configuration is served via [jsDelivr](https://www.jsdelivr.com/) for low latency and high availability.

**URL Template:**
`https://cdn.jsdelivr.net/gh/<username>/sonic-app-config/app-config.json`

## 📄 Configuration Structure

```json
{
  "latestVersion": "1.0.0",
  "minRequiredVersion": "1.0.0",
  "forceUpdate": false,
  "updateUrl": "https://your-apk-link.com/app.apk",
  "message": "Welcome to the latest version 🚀"
}
```

### Field Definitions:
- `latestVersion`: The newest version available for download.
- `minRequiredVersion`: The minimum version allowed to run. If the user's version is lower, they must update.
- `forceUpdate`: Boolean flag to trigger a mandatory update UI in the app.
- `updateUrl`: Direct link to the latest APK or store page.
- `message`: A custom message to display to users (e.g., "Critical performance fixes").

## 🔄 Update Workflow

1. Modify `app-config.json` with new values.
2. Commit and push the changes to GitHub.
3. The changes will be available via the CDN immediately (or after a short cache delay).

## ⚡ Cache Busting

When fetching this configuration in your app, append a timestamp to bypass CDN or browser caching:

```javascript
const response = await fetch(`https://cdn.jsdelivr.net/gh/<username>/sonic-app-config/app-config.json?t=${Date.now()}`);
```
