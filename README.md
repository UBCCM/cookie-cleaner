# UBC.ca Cookie Cleaner

The **UBC.ca Cookie Cleaner** is a lightweight web utility designed to help restore normal access to UBC websites affected by oversized or conflicting cookies. Some analytics and tracking tools across UBC subdomains have been configured inconsistently, occasionally causing browsers to return **“Request Header Fields Too Large.”**

👉 **Try it here:** [https://clf.ubc.ca/cookie-cleaner.html](https://clf.ubc.ca/cookie-cleaner.html)

This tool provides an easy, temporary way to **remove UBC-related cookies** until a unified governance model for analytics and cookie management is in place.

---

## 🛑 CRITICAL: Prevention (Action Required for Site Owners)

To prevent your site from crashing other UBC websites, you must ensure your tracking cookies are **scoped only to your subdomain**. Following these steps stops the accumulation of headers at the root level.

### 1. Google Tag Manager (GTM) Setup
If you use GTM to deploy GA4, you must override the default "auto" cookie domain:
1. Open your **GA4 Configuration Tag**.
2. Under **Fields to Set**, add a new row:
   - **Field Name:** `cookie_domain`
   - **Value:** Your specific subdomain (e.g., `science.ubc.ca`) 
3. **Do not** leave this blank or set to `auto`.

### 2. Google Analytics 4 (gtag.js) Setup
If you hardcode your tracking script, update your configuration line:
```javascript
// ✅ CORRECT: Scoped to your specific site
gtag('config', 'G-XXXXXXXXXX', {
  'cookie_domain': 'your-subdomain.ubc.ca'
});

// ❌ INCORRECT: Causes "Cookie Bloat" across ubc.ca
gtag('config', 'G-XXXXXXXXXX'); 
```
👉 **Official Documentation:** [https://developers.google.com/tag-platform/security/guides/customize-cookies](https://developers.google.com/tag-platform/security/guides/customize-cookies)

---

## 🌟 Purpose

When tracking cookies (e.g., Google Analytics, Meta Pixel, TikTok Pixel, Hotjar, or Clarity) are set at the root `ubc.ca` domain rather than at their specific subdomain, they are shared across multiple UBC sites. This leads to:

* Oversized HTTP request headers
* Browser errors and failed requests
* Slower performance or inconsistent user sessions

The cleaner helps reset these cookies so affected pages can load normally again.

---

## 🧩 What It Does

* Lists cookies associated with `ubc.ca` and its subdomains
* Explains the common tracking cookies and their function
* Allows users to:

  * Delete individual cookies
  * Delete all UBC-related cookies at once

The script specifically targets:

* `.ubc.ca`

---

## 🚀 How to Use

You can use the cookie cleaner in one of two ways, depending on your site setup.

### Option 1 — Upload and Run as a Webpage

1. Download the provided [`cleaner.html`](https://github.com/UBCCM/cookie-cleaner/blob/main/src/cleaner.html) file.
2. Upload it to any website that has a `*.ubc.ca` domain (for example, `brand.ubc.ca` or `events.ubc.ca`).
3. Visit the page in your browser (e.g., `https://brand.ubc.ca/cleaner.html`).
4. Click **“Delete All UBC Cookies”** or remove specific cookies individually.
5. Refresh the affected UBC site to confirm the issue is resolved.

### Option 2 — Integrate the JavaScript

If you prefer not to host a separate page:

1. Copy the JavaScript from the `<script>` section in [`cleaner.html`](https://github.com/UBCCM/cookie-cleaner/blob/main/src/cleaner.html).
2. Add it to a temporary utility page or admin-only area within your UBC-hosted site (`*.ubc.ca`).
3. Ensure it runs in a browser context under a UBC domain so it can access the relevant cookies.

You should see:

```
There is no cookie 🍪 left.
```

---

## 🚨 If You Are Already Seeing a 431 “Request Header Fields Too Large” Error

In some cases, the cookie cleaner page may not load because the browser is already sending too many cookies with the request header. When this happens, you can try using a minimal cookie reset script that removes UBC-related cookies before loading the full tool.

You can access the reset script in two ways:
- [Sample on clf.ubc.ca](https://clf.ubc.ca/cookie-reset.html)
- [Source code in `reset.html`](https://github.com/UBCCM/cookie-cleaner/blob/main/src/reset.html)

The reset script attempts to remove cookies associated with:

`.ubc.ca`

After running the reset script:

1. Try accessing the affected UBC site again.
2. If the site loads successfully, you can then use the **UBC Cookie Cleaner** to review or remove any remaining cookies.

### Last Resort

If the error persists and the reset script cannot run, you may need to **manually clear cookies for `ubc.ca` in your browser settings**.

This should only be necessary in rare cases where the browser refuses requests before any page content or scripts can load.

---

**Author:** UBC Communications
**Copyright:** © 2025 The University of British Columbia
**More Info:** [https://brand.ubc.ca/clf](https://brand.ubc.ca/clf)
