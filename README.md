# Void Apps — Legal & Compliance Site

Static GitHub Pages site reused as the privacy/terms/support URLs for **every**
Void Apps app on Google Play. No build step — plain HTML + one CSS file.

## Pages

| File | Public URL | Use |
|---|---|---|
| `index.html` | `https://cevatakdemir21.github.io/` | Landing |
| `privacy.html` | `https://cevatakdemir21.github.io/privacy.html` | **Play Console → App content → Privacy policy** |
| `terms.html` | `https://cevatakdemir21.github.io/terms.html` | Terms / EULA |
| `support.html` | `https://cevatakdemir21.github.io/support.html` | Store listing support URL + contact |
| `data-deletion.html` | `https://cevatakdemir21.github.io/data-deletion.html` | **Play Console → Data safety → Data deletion URL** |

## One-time setup

1. Create a **public** GitHub repo named exactly `cevatakdemir21.github.io`.
2. Push these files to the `main` branch (root).
3. Repo → **Settings → Pages** → Source = `Deploy from a branch`, Branch = `main` / `/ (root)`.
4. Wait ~1 min, then open `https://cevatakdemir21.github.io/` — HTTPS is automatic.

```bash
cd cevatakdemir21.github.io
git init
git add .
git commit -m "Add Void Apps legal site"
git branch -M main
git remote add origin https://github.com/cevatakdemir21/cevatakdemir21.github.io.git
git push -u origin main
```

## Per-app Play Console checklist

Keep the Data Safety form consistent with `privacy.html`:

1. **Privacy policy URL** → `https://cevatakdemir21.github.io/privacy.html` (same for every app).
2. **Data safety** — declare what the policy lists:
   - Device or other IDs → **Advertising ID** (collected + shared, for advertising). 
   - App activity / app info & performance → analytics (PostHog).
   - **Purchase history** → subscriptions (RevenueCat).
   - Mark all **encrypted in transit**.
   - **Data deletion** → provide `https://cevatakdemir21.github.io/data-deletion.html`.
3. **Ads** → "Contains ads" = **Yes**.
4. **AD_ID permission** → `com.google.android.gms.permission.AD_ID` is auto-added by
   `google_mobile_ads`; declare Advertising ID use (required, Android 13+).
5. **App access** → "All functionality available without special access" (no login).
6. **Content rating** → general audience.
7. **Target audience & content** → 13+/general; not directed to children.
8. **Subscriptions / financial features** → declare in-app subscriptions.
9. **Store listing** → set support email + (optionally) the support URL above.

## In-app requirement (not part of this site)

For global AdMob release, EEA/UK/CH users need a Google-certified consent prompt.
`google_mobile_ads` ships the **UMP SDK** (`UserMessagingPlatform`): configure a
GDPR message + ad-partner list in the AdMob console and request consent **before**
initializing ads. The privacy policy's consent section assumes this is wired up.

## Editing

- All shared styling is in `style.css` (brand blue `#0088FF`, light + dark).
- Update the "Last updated" date in the legal pages when you change them.
- Swap `cevat.akdmrr@gmail.com` everywhere if you create a dedicated support address.
