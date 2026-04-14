# Ultimate Firefox Hardening Guide

> "Privacy is not a crime. It's a right."
> Welcome to the ultimate guide to hardening Mozilla Firefox. Out of the box, Firefox is better than most, but it still compromises your privacy to keep the modern web "convenient." This project takes the gloves off. We are trading convenience for maximum security, anonymity, and tracker-blocking.

### Important Warning: The Cost of Privacy
Before you begin, you must understand that **hardening your browser will change how the web behaves**. By aggressively blocking trackers, isolating cookies, and resisting fingerprinting, you will inevitably encounter broken websites. 
* Images or videos might not load.
* Login buttons or forms might fail.
* You may face more CAPTCHAs than usual.
* Browser-based video calls (like Discord Web, Google Meet, or Zoom web clients) may stop working entirely depending on the settings you choose.

If you are okay with troubleshooting the occasional broken site in exchange for top-tier privacy, proceed.

---

## Table of Contents
1. [Level 1: Built-in UI Settings (Beginner)](#level-1-built-in-ui-settings)
2. [Level 2: The Holy Trinity of Extensions (Intermediate)](#level-2-the-holy-trinity-of-extensions)
3. [Level 3: Under the Hood - about:config (Advanced)](#level-3-under-the-hood)
4. [Level 4: Automated Scripts & Forks (Expert)](#level-4-automated-scripts--forks)

---

## Level 1: Built-in UI Settings
This is the baseline. You can do this quickly without delving into hidden menus.

### 1. Navigating to Privacy Settings
First, open your Firefox settings and navigate to the **Privacy & Security** panel. This is where the foundation of our hardening begins.

![Navigating to Privacy and Security](img/Hardened_Firefox1.png)

### 2. Enhanced Tracking Protection
Change Enhanced Tracking Protection from Standard to **Strict**. 
This setting automatically blocks cross-site cookies in all windows, social media trackers, cryptominers, and known fingerprinters. It is the most impactful change you can make in the standard UI.

![Enhanced Tracking Protection set to Strict](img/Hardened_Firefox2.png)

### 3. Kill the Telemetry
Mozilla generally respects privacy, but no browser needs to phone home with your usage data. Scroll down to the **Firefox Data Collection and Use** section.
Uncheck every single box. You do not need to send technical data, participate in studies, or send crash reports.

![Firefox Data Collection and Use settings](img/Hardened_Firefox3.png)

### 4. Ditch Google
A secure browser means nothing if your search engine tracks your every query. Go to the **Search** tab in your settings and change your Default Search Engine to a privacy-respecting alternative like DuckDuckGo or Startpage.

![Default Search Engine set to DuckDuckGo](img/Hardened_Firefox4.png)

---

## Level 2: The Holy Trinity of Extensions
Do not clutter your browser with dozens of extensions; doing so actually makes your browser more unique and easier to fingerprint. Stick to these three absolute essentials.

### 1. uBlock Origin
The undisputed king of content blockers. It kills ads, trackers, and malicious scripts with incredibly low CPU and memory overhead. Ensure you are installing *uBlock Origin*, not the older, unrelated "uBlock".

![uBlock Origin Extension](img/Hardened_Firefox5.png)

### 2. CanvasBlocker
Websites use JavaScript APIs (like the HTML5 Canvas) to render invisible elements that uniquely identify your machine's hardware and graphics rendering. CanvasBlocker spoofs this data, preventing canvas fingerprinting.

![CanvasBlocker Extension](img/Hardened_Firefox6.png)

### 3. ClearURLs
Many links contain hidden tracking parameters (e.g., those annoying `?utm_source=...` strings). ClearURLs automatically strips this tracking garbage from URLs before the page even loads, ensuring your navigation remains private.

![ClearURLs Extension](img/Hardened_Firefox7.png)

---

## Level 3: Under the Hood (`about:config`)
Time to get your hands dirty. Firefox hides its most powerful, uncompromising privacy features in a hidden configuration menu.

**How to access it:**
1. Type `about:config` in your URL bar and hit Enter.
2. Accept the "Proceed with Caution" warning.
3. Use the search bar to find the following preferences and double-click them to change their values.

### 1. Resist Fingerprinting
Search for `privacy.resistFingerprinting` and set it to **true**.
This is the holy grail of anti-fingerprinting. It spoofs your timezone, limits available system fonts, and resists window size tracking by spoofing your screen resolution. 

![privacy.resistFingerprinting set to true](img/Hardened_Firefox8.png)

### 2. First-Party Isolation
Search for `privacy.firstparty.isolate` and set it to **true**.
This enforces strict isolation. Trackers and cookies are trapped within the domain that created them and cannot follow you across the web.

![privacy.firstparty.isolate set to true](img/Hardened_Firefox9.png)

### 3. Disable WebRTC (Prevent IP Leaks)
Search for `media.peerconnection.enabled` and set it to **false**.
WebRTC can leak your real, physical IP address even if you are using a VPN. Setting this to false plugs that leak. 
*Note: This will definitively break browser-based voice and video calls.*

![media.peerconnection.enabled set to false](img/Hardened_Firefox10.png)

---

## Level 4: Automated Scripts & Forks
If you do not want to configure everything manually after every fresh install, or if you want an even stricter setup, check out these community-driven solutions.

* **Arkenfox user.js**: A highly restrictive, security-first configuration template. You drop this `user.js` file into your profile folder, and it automatically applies hundreds of privacy tweaks upon startup. It requires reading their documentation to understand what it breaks.
* **Betterfox**: Similar to Arkenfox, but heavily optimized for speed and a smoother daily-driving experience with fewer broken sites.
* **LibreWolf**: Don't want to tweak at all? LibreWolf is a custom fork of Firefox that comes completely hardened out-of-the-box. It has uBlock Origin pre-installed, telemetry completely ripped out of the source code, and Arkenfox-like settings enabled by default.

Stay safe, stay anonymous.
