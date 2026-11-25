# PitWall Fuel Burn Calculator

A lightweight, mobile-first Progressive Web App (PWA) built for pit-lane fuelers and race engineers to calculate post-session fuel consumption (**Liters/lap**, **kg/lap**, and **lbs/lap**) from pump-in and pump-out measurements.

Pre-configured for **VP E100** (`0.790` base SG @ 60°F) and major North American road courses, with live thermal expansion adjustment and offline support.

---

## Features

* **Track Database + Custom Tracks:** Preloaded with 12 IMSA/North American road courses (Daytona, Sebring, Road Atlanta, Watkins Glen, Road America, VIR, Laguna Seca, etc.) plus a custom track length option.
* **4-Way Measurement Switcher:** Enter fuel put in and pumped out in **Liters (`L`)**, **US Gallons (`gal`)**, **Kilograms (`kg`)**, or **Pounds (`lbs`)**.
* **Temperature-Adjusted Specific Gravity:** Automatically corrects fuel density using thermal expansion coefficients ($\beta = 0.00060/^\circ\text{F}$ for VP E100) relative to the $60^\circ\text{F}$ ($15.56^\circ\text{C}$) reference standard. Supports instant `°F` / `°C` toggling.
* **Stint & Efficiency Metrics:** Calculates net fuel burned, **Liters/km**, and estimated **Max Laps per Tank** when tank capacity is entered.
* **Offline-Ready PWA:** Includes a `manifest.json` and Service Worker (`sw.js`) so the app can be installed to an iOS or Android home screen and run 100% offline in garages or paddocks with poor cell reception.

---

## Project Files

```text
├── index.html      # Complete single-file application (UI, styles, and calculation logic)
├── manifest.json   # PWA metadata for "Add to Home Screen" installation
├── sw.js           # Service worker for offline caching
└── README.md       # Project documentation
```

---

## Quick Deployment

### Option 1: Netlify Drop (Fastest — No Account Needed)
1. Place `index.html`, `manifest.json`, and `sw.js` in a single folder.
2. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
3. Drag and drop the folder onto the browser window to get an instant HTTPS URL.

### Option 2: GitHub Pages / Vercel / Cloudflare Pages
1. Push all files to the root of a GitHub repository.
2. Enable **GitHub Pages** (Settings → Pages → Deploy from `main` branch) or import the repo into Vercel/Cloudflare Pages.

### Installing on iPhone / Android (Pit Lane Use)
1. Open the deployed HTTPS URL in **Safari** (iOS) or **Chrome** (Android).
2. Tap **Share → Add to Home Screen** (iOS) or **Menu → Install App** (Android).
3. Open it once while online so the service worker caches the files for offline paddock use.

---

## Calculation Reference

1. **Temperature-Adjusted Specific Gravity:**
   $$\text{SG}_{\text{adj}} = \text{SG}_{60^\circ\text{F}} - \left[\beta \times (T_{^\circ\text{F}} - 60)\right]$$

2. **Weight-to-Volume Conversion:**
   $$\text{Liters} = \frac{\text{Weight (kg)}}{\text{SG}_{\text{adj}}}$$

3. **Estimated Fuel Used per Lap:**
   $$\text{Liters/Lap} = \frac{\text{Fuel Put In (L)} - \text{Fuel Pumped Out (L)}}{\text{Laps Completed}}$$