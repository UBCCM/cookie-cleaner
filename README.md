# UBC.ca Cookie Cleaner

The **UBC.ca Cookie Cleaner** is a lightweight web utility designed to help restore normal access to UBC websites affected by oversized or conflicting cookies. Some analytics and tracking tools across UBC subdomains have been configured inconsistently, occasionally causing browsers to return **“Request Header Fields Too Large.”**

This tool provides an easy, temporary way to **remove UBC-related cookies** until a unified governance model for analytics and cookie management is in place.

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
3. Visit the page in your browser (e.g., `https://brand.ubc.ca/ubc-cookie-cleaner.html`).
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

## 🧠 Best Practice for Future Setup

To prevent similar issues in the future:

* **Always configure analytics tools for their specific subdomain**, not for the entire `ubc.ca` domain.

  * ✅ Example: `brand.ubc.ca`, `science.ubc.ca`, `events.ubc.ca`
  * ❌ Avoid: setting cookies at `ubc.ca`

This keeps data scoped appropriately, improves site performance, and avoids cross-domain cookie conflicts.

---

**Author:** UBC Communications
**Copyright:** © 2025 The University of British Columbia
**More Info:** [https://brand.ubc.ca/clf](https://brand.ubc.ca/clf)
