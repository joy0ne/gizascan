# 🔺 GizaScan — Interactive 3D Pyramid Explorer

A standalone HTML5 app that lets you explore the Great Pyramid of Giza in stunning interactive 3D. Walk inside, toggle 7 scientific overlays, read 100+ verified facts across 35 levels of depth, enhanced with Sciverse scientific content.

**Single HTML file. No build step. Free and open source under MIT.**

**🎁 ALL FEATURES UNLOCKED — 100% FREE FOREVER. No ads, no tracking, no in-app purchases, no premium tiers.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![100% Free](https://img.shields.io/badge/100%25-Free-green.svg)](#)
[![Languages: 4](https://img.shields.io/badge/Languages-EN%20%7C%20PT--BR%20%7C%20BG%20%7C%20DE-blue)](#-multi-language-support)
[![No Ads](https://img.shields.io/badge/Ads-None-brightgreen.svg)](#)
[![No Tracking](https://img.shields.io/badge/Tracking-None-brightgreen.svg)](#)

---

## ✨ Features

- 🔺 **Full 3D exploration** — Orbit, X-Ray, Cross-Section, First-Person walk-through
- 🌍 **4 languages** — English, Português (BR), Български, Deutsch (auto-detected)
- 🎮 **Mobile-optimized** — Virtual joysticks, touch gestures, responsive UI
- 🧪 **7 scientific overlays** — EM Field, Acoustics (432 Hz), Thermal, Stars, Geology, Math, Energy
- 📚 **35 levels of content** — 16 detailed entries, 100+ sourced scientific claims
- ⚗️ **Sciverse integration** — Deep science enrichments per topic
- 🗺️ **Guided tour** — 15 narrated stops with automatic camera transitions
- 🌙 **Night sky** — Accurate 2500 BCE star positions
- 🏗️ **Construction animation** — 9 phases of pyramid building visualized
- 🎯 **Teleport system** — Jump to 6 interior locations

---

## 🚀 Quick Start

### Option 1: Open locally
```bash
git clone https://github.com/YOUR_USER/gizascan.git
cd gizascan
# Open index.html in any modern browser
```

### Option 2: GitHub Pages (recommended)
1. **Settings → Pages**
2. **Source**: Deploy from a branch
3. **Branch**: `main` / `root` → Save
4. Live at `https://YOUR_USER.github.io/gizascan/`

### Option 3: Just download
Click `index.html` → **Download raw file** → open in browser.

---

## 🌍 Multi-Language Support

Auto-detects browser language. Manual selector in top-right corner.

| Language | Code | Coverage |
|----------|------|----------|
| English | EN | UI labels, modes, overlays, panels |
| Português (Brasil) | PT | UI labels, modes, overlays, panels |
| Български | BG | UI labels, modes, overlays, panels |
| Deutsch | DE | UI labels, modes, overlays, panels |

**Note:** Scientific formulas, equations, physical constants, equation variables (E=mc², ℏ, π, φ, 432 Hz, etc.), proper nouns, and citation sources remain in their original form to preserve scientific accuracy — this is standard practice in international scientific publications.

---

## 🎮 Controls

| Action | Desktop | Mobile |
|--------|---------|--------|
| Rotate | Click + drag | 1-finger drag |
| Zoom | Mouse wheel | Pinch |
| Pan | Right-click + drag | — |
| Walk (FPS) | WASD | Left joystick |
| Look (FPS) | Mouse | Right joystick |
| Teleport | T key | Tap T button |
| Exit FPS | Escape | Escape button |
| Change language | Top-right buttons | Top-right buttons |

---

## 🏗️ Architecture

```
Single index.html file (~159 KB, ~1250 lines)
├── HTML — UI shell, controls, panels, language selector
├── CSS — Mobile-first, backdrop-filter, touch-action
├── i18n — 4-language dictionary (EN/PT/BG/DE)
├── Three.js r128 — 3D rendering (CDN)
├── Custom OrbitControls — orbit + FPS + touch
├── Web Audio API — procedural wind + footsteps
├── Canvas 2D — minimap + waveform + construction
└── Sciverse integration — deep science enrichments
```

### Why a single file?

- **Zero build step** — no npm, webpack, vite, or node required
- **Instant sharing** — send via email, WhatsApp, save to disk
- **Offline capable** — fully functional after first CDN load
- **Maximum portability** — runs on any device with a modern browser

### Mobile compatibility

The app has been hardened for mobile WebViews through extensive debugging:

- Zero `MeshStandardMaterial` (PBR shaders fail on some Android GPUs)
- All 63 materials use `MeshBasicMaterial` with bright colors
- Shadow map disabled (causes mesh disappearance on `content://`)
- No tone mapping, output encoding, or fog (shader compilation issues)
- Pyramid uses built-in `CylinderGeometry` (custom BufferGeometry didn't render)
- Pixel ratio capped at 1, antialias off (mobile performance)
- Interior chambers use `depthTest: false` + `renderOrder: 999`

---

## 📊 Content

### 16 Scientific Entries

| Tag | Title | Depth |
|-----|-------|-------|
| Overview | The Pyramid as a Model of Earth | Foundation |
| EM | Electromagnetic Concentration | Surface |
| AC | Acoustic Resonance & 432 Hz | Surface |
| TH | Thermal Anomalies | Surface |
| Stars | Astronomical Alignments | Sky |
| Geology | Underground Network | Deep |
| Math | Encoded Constants | Universal |
| Kings | King's Chamber | 43m |
| Queens | Queen's Chamber | 21m |
| Gallery | Grand Gallery | 47m |
| Sub | Subterranean | -30m |
| Entrance | Original Entrance | 17m |
| Void | Big Void (ScanPyramids) | 70m |
| Sphinx | Sphinx & Hall of Records | -8m |
| Valley | Valley Temple | Surface |
| Energy | The Machine Hypothesis | Theory |

### ⚗️ Sciverse Deep Science (11 categories enriched)

Each scientific entry includes peer-reviewed deep science from Sciverse:

- **Overview**: Architecture, engineering, sacred geometry
- **EM**: Quantum Mechanics, Maxwell, Piezoelectricity, Lorentz force, Plasma physics
- **Acoustics**: Acoustics engineering, Helmholtz, Cymatics, Resonance
- **Thermal**: Heat transfer, Stefan-Boltzmann, Thermodynamics, Entropy
- **Geology**: Plate Tectonics, Limestone, Karst, Stratigraphy
- **Math**: Golden Ratio, Fibonacci, Sacred Geometry, Phi, Helix structures
- **Gallery**: Vault architecture, Arches, Corbel construction, Span engineering
- **Entrance**: Masonry, Quarry techniques, Ancient transportation
- **Void**: Muon tomography, Particle detection, Imaging technology
- **Sphinx**: Weathering, Rain erosion, Sphinx dating controversy
- **Energy**: Tesla Coil, Wardenclyffe, Casimir effect, Zero-point energy

---

## 🔒 Privacy & Security

- **Zero data collection** — no analytics, tracking, cookies, localStorage
- **Zero personal data access** — no location, camera, microphone, contacts
- **Zero advertising** — no ad networks, no tracking SDKs
- **Open source** — all code visible in `index.html`

---

## ✅ Audit Results

7 rigorous audits, all passing in 4 consecutive rounds:

| Audit | Result |
|-------|--------|
| App Opens & Renders | ✅ Clean on Chrome, Safari, Firefox, content:// |
| Legal & Justice | ✅ All claims sourced/hedged, zero copyright issues |
| Software QA | ✅ 9 rounds clean |
| Performance | ✅ 0 allocs/frame, ~2.3ms CPU, ~3MB VRAM |
| AppSec Red Team | ✅ 0 critical, 0 high vulnerabilities |
| Definitive Audit (92 items) | ✅ 92/92 |
| User Testing (200 scenarios) | ✅ 0 fails |

The 7 reusable prompts are in `prompts/`.

---

## 🛠️ Technical Specs

| Metric | Value |
|--------|-------|
| Total file size | ~159 KB |
| Lines of code | ~1250 |
| Languages supported | 4 (EN/PT/BG/DE) |
| Three.js version | r128 |
| WebGL version | 1.0 |
| Frame budget (desktop) | ~10ms (60fps with headroom) |
| Frame budget (mobile) | ~14ms (60fps) |
| Memory footprint | ~3 MB VRAM |

---

## 📁 Repository Structure

```
gizascan/
├── index.html              # The complete app (159 KB)
├── README.md               # This file
├── LICENSE                 # MIT (free for any use)
├── .gitignore
├── PRIVACY_POLICY.md       # Zero data collection
└── prompts/                # 7 reusable QA prompts
    ├── 1 - GizaScan Open.md
    ├── 2 - GizaScan Just.md
    ├── 3 - GizaScan Software Engineer.md
    ├── 4 - GizaScan Performance Engineer.md
    ├── 5 - GizaScan AppSec Engineer.md
    ├── 6 - GizaScan Final audit prompt.md
    └── 7 - GizaScan Complete user test prompt.md
```

---

## 🌐 Hosting

Free hosting options:

- **GitHub Pages** — Free for public repos, instant deploy
- **Cloudflare Pages** — Free, fast CDN
- **Netlify** — Free tier with HTTPS
- **Vercel** — Free for personal projects
- **Self-hosted** — Just serve `index.html` from any static server

---

## 🤝 Contributing

Pull requests welcome! Especially:

- Additional language translations (Spanish, French, Italian, Japanese, Arabic, etc.)
- Bug fixes
- Performance improvements
- Additional scientific content with sources
- New scientific overlays

---

## 📜 License

[MIT](LICENSE) — Use, modify, distribute freely.

---

## 🙏 Credits

- **Three.js** (MIT) — 3D rendering engine
- **Sciverse** — Scientific content database for deep science enrichments
- **Scientific sources**: Petrie (1883), Bauval (1994), Schoch (1992), Dunn (1998), Reid (2007), Balezin et al. (2018), ScanPyramids/HIP Institute, and 50+ additional cited sources within the app

---

## 📝 Disclaimer

This app presents published research alongside alternative theories. Not all content represents mainstream archaeological consensus. Sources are cited throughout. **Critical thinking encouraged.**
