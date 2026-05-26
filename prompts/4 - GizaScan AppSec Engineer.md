# 4 — GizaScan: AppSec Engineer / Red Team
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

Act as a Senior AppSec (Application Security) Engineer and Red Team Leader. Your mission: find ANY attack vector, data leak, or privacy violation in this app.

You will receive the complete code of **"GizaScan"**: a standalone 3D app (single HTML, ~130 KB, ~1200 lines). Three.js r128 via CDN, Web Audio API, Canvas 2D, paywall with Capacitor IAP, zero backend.

---

## PHASE 1: Attack Surface — OWASP Checklist

### 1.1 Injection (XSS/HTML)
- Find EVERY `innerHTML`, `outerHTML`, `insertAdjacentHTML`, `document.write`
- Is the source HARDCODED (const SCI) or from user input?
- Template literals with `${}` — does any interpolate external input?
- `.textContent` vs `.innerHTML` — all correct?

### 1.2 Eval & Code Injection
- `eval()`, `new Function()`, `setTimeout(string)`, `setInterval(string)`?
- Dynamic import? `import()`?
- `javascript:` URLs?

### 1.3 Data Exfiltration
- `fetch()`, `XMLHttpRequest`, `WebSocket`, `navigator.sendBeacon()`?
- `postMessage()` sending data?
- Any data leaving the app to ANY destination?

### 1.4 Storage & Privacy
- `localStorage`, `sessionStorage`, `IndexedDB`, `document.cookie`?
- `navigator.geolocation`, `navigator.mediaDevices`?
- Any API accessing personal data?
- GDPR/LGPD/CCPA compliance?

### 1.5 CDN & Supply Chain
- CDN URLs: have `integrity` (SRI hash)?
- `crossorigin` attribute present?
- What happens if CDN is compromised?
- Google Fonts: privacy implications?

### 1.6 API Keys & Credentials
- Find ANY string that looks like a key/token/secret
- Regex: `/[A-Za-z0-9_-]{20,}/` in suspicious context
- URLs with authentication parameters?

## PHASE 2: Data Flow Analysis

For EACH piece of data entering or leaving the app:
```
INPUT → PROCESSING → OUTPUT
[source]  [transform]  [destination]
```

Map: user input (touch/keyboard/pointer/slider), CDN data, external image URLs, Web Audio nodes, Capacitor IAP responses, postMessage listeners, URL parameters.

## PHASE 3: Threat Modeling (STRIDE)

| Threat | Vector | Impact | Mitigation |
|--------|--------|--------|------------|
| Spoofing | ? | ? | ? |
| Tampering | ? | ? | ? |
| Repudiation | ? | ? | ? |
| Info Disclosure | ? | ? | ? |
| DoS | ? | ? | ? |
| Elevation | ? | ? | ? |

## PHASE 4: Content Security

1. Medical claims (DMT, pineal, frequencies)? Framed as theory?
2. Accusatory language against living people/institutions?
3. Copyrighted images?
4. Play Store / App Store content policy compliance?

## PHASE 5: Penetration Test Simulation

Try EACH attack:
1. Console: `isPro=true` — bypasses paywall?
2. Console: `SCI.overview.desc='<img src=x onerror=alert(1)>'` — XSS?
3. Modify `purchasePro()` to skip payment
4. Intercept Capacitor IAP callback
5. Man-in-the-middle on CDN (no SRI)
6. Inject script via URL fragment
7. Prototype pollution via `Object.assign`
8. Touch event injection to manipulate 3D state

Format:
```
ROUND N — [X vulnerabilities]
VULN: [CRITICAL/HIGH/MEDIUM/LOW/INFO] — [description] — [fix]
```

**Fix everything and apply the improvements.**
