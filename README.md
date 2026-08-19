# Cookield CMP — Google Consent Mode v2 Template

Official Google Tag Manager template for **[Cookield](https://cookield.io)** Consent Management Platform.

Automatically integrates Google Consent Mode v2 with the Cookield cookie banner, setting default consent states and updating them based on user choices.

## Features

- ✅ Sets all consent signals to `denied` by default
- ✅ Reads stored consent from cookie on subsequent page loads
- ✅ Updates consent state in real-time when user interacts with the banner
- ✅ Supports all required Google Consent Mode v2 signals:
  - `ad_storage`
  - `ad_user_data`
  - `ad_personalization`
  - `analytics_storage`
  - `functionality_storage`
  - `personalization_storage`
  - `security_storage`
- ✅ Optional: Ads data redaction
- ✅ Optional: URL passthrough (gclid/dclid)
- ✅ Loads Cookield banner script via GTM

## Installation

### From the Community Template Gallery

1. In your GTM container, go to **Templates → Tag Templates → Search Gallery**
2. Search for "Cookield"
3. Click **Add to workspace**

### Manual Installation

1. In GTM, go to **Templates → Tag Templates → New**
2. Click the three-dot menu → **Import**
3. Select the `template.tpl` file from this repository
4. Save the template

## Configuration

### 1. Create a new tag

1. Go to **Tags → New**
2. Select **Cookield CMP - Consent Mode v2** as the tag type

### 2. Configure the tag

| Field | Description | Required |
|-------|-------------|----------|
| **Banner ID** | Your Cookield banner ID (found in Dashboard → Banners → Snippet) | Yes |
| **API URL** | Leave empty for default (`https://cdn.cookield.io`) | No |
| **Redact Ads Data** | Enable to redact ad click identifiers when `ad_storage` is denied | No |
| **URL Passthrough** | Enable to pass ad click info through URL parameters | No |

### 3. Set the trigger

Assign the trigger: **Consent Initialization - All Pages**

This ensures the template fires before any other tags.

## How It Works

1. **On page load:** Sets all consent signals to `denied` (default state)
2. **Cookie check:** If the user has previously given consent (stored in `cookield_consent` cookie), updates consent state immediately
3. **User interaction:** When the user interacts with the Cookield banner, consent state is updated in real-time via `updateConsentState`
4. **Google tags react:** GA4, Google Ads, and other Google tags automatically adjust their behavior based on consent state

## Consent Category Mapping

| Cookield Category | Google Consent Signals |
|---|---|
| Marketing | `ad_storage`, `ad_user_data`, `ad_personalization` |
| Statistics | `analytics_storage` |
| Functional | `functionality_storage`, `personalization_storage` |
| — | `security_storage` (always granted) |

## Requirements

- A Cookield account ([cookield.io](https://cookield.io))
- A published banner with at least one domain configured
- Google Tag Manager web container

## Support

- Documentation: [cookield.io/docs](https://cookield.io/docs)
- Email: suporte@cookield.io
- Website: [cookield.io](https://cookield.io)

## About

**Cookield** is a Consent Management Platform by [A9 Tecnologia](https://a9tech.com.br) that helps websites comply with 40+ privacy regulations (LGPD, GDPR, CCPA, and more) with an intelligent cookie banner and automatic Google Consent Mode v2 integration.

## License

Copyright © 2026 A9 Tecnologia. All rights reserved.
