# Neurotype-Website
Website for Neurotype App

## OAuth Redirect Service

This repository contains an OAuth redirect service for the Neurotype mobile app. The service handles OAuth callbacks from authentication providers (like Google) and redirects them to the mobile app via a deep link.

### OAuth Redirect URL

When configuring OAuth providers (e.g., Google Cloud Console), use the following redirect URI:

```
https://neurotypeapp.com/oauth-redirect
```

This URL will:
1. Extract the `id_token` from the OAuth callback (from query parameters or hash fragment)
2. Redirect to the Neurotype mobile app using the deep link: `neurotype://oauth-callback?id_token=TOKEN`
3. Handle errors gracefully if the token is missing or the app cannot be opened

### Deployment

This site is deployed on Vercel at `neurotypeapp.com`. The routing is configured via `vercel.json` to properly serve the OAuth redirect page.
