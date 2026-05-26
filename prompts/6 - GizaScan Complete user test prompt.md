# 6 — GizaScan: Complete User Test (Hundreds of Personas)
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

Act as 50 different user personas testing the app. For EACH persona, execute ALL applicable scenarios. The app is **"GizaScan"**: interactive 3D pyramid explorer, 7 overlays, 16 scientific entries, tour, FPS, freemium paywall.

---

## 50 USER PERSONAS

### Group 1: Device & Platform (10)
1. **Android low-end** — Snapdragon 425, 2 GB RAM, 5" screen, Chrome via content://
2. **Android mid-range** — Snapdragon 680, 4 GB, 6.5", Chrome
3. **Android flagship** — Snapdragon 8 Gen 3, 12 GB, 6.7", Chrome
4. **iPhone SE** — A15, 4.7" screen, Safari
5. **iPhone 15 Pro Max** — A17 Pro, 6.7", Safari
6. **iPad Pro** — M2, 12.9", Safari landscape
7. **Desktop Windows** — RTX 3060, Chrome, 1920×1080, mouse+keyboard
8. **Desktop Mac** — M2 MacBook Air, Safari, trackpad
9. **Desktop old** — Intel HD 4000, Firefox, 4 GB RAM
10. **Chromebook** — MediaTek, Chrome OS, touch+keyboard

### Group 2: Demographics (10)
11. **Child 6 years** — taps everything, doesn't read, wants colors and movement
12. **Child 10 years** — reads some, interested in Egypt, short attention span
13. **Teenager 14** — wants to find hidden secrets, tries to break things
14. **College student** — archaeology major, skeptical of claims, checks sources
15. **Adult 30 casual** — downloaded because of cool screenshots, 2 min attention span
16. **Adult 40 teacher** — evaluating for classroom use, needs accuracy
17. **Senior 65** — large fingers, reads slowly, confused by too many buttons
18. **Senior 75** — very slow, needs big text, may accidentally tap wrong things
19. **Person with motor disability** — imprecise taps, needs large touch targets
20. **Person with color blindness** — can they distinguish overlay colors?

### Group 3: Expertise (10)
21. **Archaeologist PhD** — knows mainstream Egyptology, hostile to "alternative" claims
22. **Physicist** — checks equations, verifies speed of light claim, tests constants
23. **3D artist** — evaluates visual quality, lighting, geometry accuracy
24. **Game developer** — checks FPS, frame drops, memory usage, WebGL calls
25. **Security researcher** — tries to hack paywall, inject XSS, find vulnerabilities
26. **Mystery enthusiast** — wants ALL secrets, reads every word, shares screenshots
27. **Journalist** — writing a review, tests every feature, notes bugs for article
28. **App store reviewer (Google)** — checks policy compliance, misleading claims, functionality
29. **App store reviewer (Apple)** — checks guidelines, crashes, performance, content
30. **Competitor** — another 3D pyramid app developer, looking for weaknesses

### Group 4: Usage Scenario (10)
31. **First-time user** — opens app, no context, explores 3 minutes
32. **Returning user** — opened before, wants to continue where they left off
33. **Offline user** — airplane mode, no internet, opens saved HTML
34. **Multitasker** — opens app, switches to WhatsApp, returns, switches, returns
35. **Background user** — opens, locks screen 30 min, unlocks, expects it to work
36. **Screenshot hunter** — wants beautiful screenshots for social media
37. **Speed runner** — tries to see all content as fast as possible
38. **Methodical explorer** — reads every entry, toggles every overlay, visits every spot
39. **Buyer** — explores free, decides to buy, expects instant unlock
40. **Refunder** — bought by accident, wants to undo, can't find how

### Group 5: Edge Cases (10)
41. **Battery saver user** — phone on 5%, power saving mode ON
42. **Split-screen user** — app in half screen on Android
43. **Picture-in-picture** — tries to use PiP
44. **Accessibility user** — TalkBack/VoiceOver enabled, screen reader
45. **Large font user** — system font size set to 200%
46. **Dark mode user** — system dark mode ON
47. **VPN user** — slow connection through VPN, CDN loads slowly
48. **Multiple tabs** — opens app in 3 tabs simultaneously
49. **Memory pressure** — 20 other apps open, phone nearly out of RAM
50. **Developer tools** — Chrome DevTools open, throttling CPU 6×

---

## TEST SCENARIOS BY CATEGORY (200 scenarios)

### A. Cold Start & Loading (15 scenarios)
A1. First load, good internet
A2. First load, 3G slow (Three.js takes 10s)
A3. No internet (CDN fails completely)
A4. Portrait orientation
A5. Landscape orientation
A6. Rotation DURING loading
A7. Tap screen during loading (before ready)
A8. Back button during loading (Android)
A9. Swipe down during loading (iOS)
A10. Double-tap on loader
A11. Open via content:// (Android file manager)
A12. Open via file:// (Chrome direct)
A13. Open via https:// (hosted)
A14. CDN loads but fonts fail
A15. CDN fails but cached (service worker)

### B. Orbit Navigation (15 scenarios)
B1. 1-finger drag (rotation)
B2. Pinch zoom in/out
B3. Pinch with 3+ fingers
B4. Double-tap
B5. Zoom to minimum distance (minD=60)
B6. Zoom to maximum distance (maxD=700)
B7. Auto-rotate observed for 60s
B8. Pan with right-click (desktop)
B9. Scroll wheel spam (100 events in 2s)
B10. Fast rotation → sudden stop
B11. Touch+mouse simultaneous (tablets with keyboard)
B12. Orbit while panel is open
B13. Orbit during tour
B14. Orbit with all overlays ON
B15. Orbit → immediately enter another mode

### C. View Modes (20 scenarios)
C1. Orbit → X-Ray (pyramid transparent, interior visible?)
C2. X-Ray → Cross-Section
C3. Cross-Section → FPS (PRO gate works?)
C4. FPS → Escape → Orbit
C5. Spam: Orbit→XRay→Cut→FPS→Orbit 10× in 5s
C6. X-Ray with 7 overlays simultaneously
C7. FPS: WASD movement + mouse look
C8. FPS: teleport T → list → select → confirm position
C9. FPS: try to walk through walls
C10. FPS: exit pointer lock (Escape)
C11. FPS: mobile joystick (move + look)
C12. FPS: joystick finger leaves screen mid-drag
C13. FPS: 2 fingers on same joystick
C14. FPS: joystick + tap scene simultaneously
C15. X-Ray: tap on mesh → showInfo opens correct entry?
C16. Change mode during aCam camera transition
C17. Enter FPS → immediately open teleport → teleport → exit FPS
C18. Cut mode → zoom to minimum → zoom to maximum
C19. X-Ray → toggle all overlays → return to Orbit → overlays persist?
C20. FPS movement near world boundaries (far from pyramid)

### D. Overlays (25 scenarios)
D1-D7. Toggle EACH overlay individually (em, ac, th, st, ge, math, nrg)
D8. All 7 ON simultaneously
D9. Toggle same overlay ON/OFF 20× in 3s
D10. Overlay ON → change mode → overlay persists?
D11. Overlay ON → change overlay → first turns off?
D12. FREE overlays (em/ac/th) → work without paywall
D13. PRO overlays (st/ge/math/nrg) → paywall modal appears
D14. Buy PRO → PRO overlay now works
D15. EM: pulsing spheres visible and animated?
D16. Acoustics: waveform canvas renders? 432 Hz ring visible?
D17. Thermal: heatmap on east face?
D18. Stars: Orion Belt + precession circle + Leo + Milky Way?
D19. Geology: tunnels glowing + Osiris Shaft + water table ripples?
D20. Math: Platonic solids orbiting KC? DNA helix? Fibonacci?
D21. Energy: Tesla bolts + charge particles rising? Crystal lattice?
D22. Legend updates correctly with active overlays?
D23. Live data panel shows when em/ac/th active?
D24. Overlay + night mode simultaneously
D25. Overlay + construction simultaneously

### E. Tour (15 scenarios)
E1. Start tour → all 15 stops play sequentially
E2. Tour FREE → stops at stop 7 → PRO modal
E3. Tour PRO → completes all 15 stops
E4. Stop tour mid-way (toggle button)
E5. Start tour → manually change mode → tour cancels?
E6. Tour → resize window → continues?
E7. Tour → lock screen → return → continues?
E8. Tour → switch tab → return → continues?
E9. Tour → toggle overlay during tour
E10. Tour → panel open → info changes at each stop?
E11. Tour speed → timing between stops feels natural?
E12. Tour complete → returns to orbit mode?
E13. Tour → spam start/stop 10×
E14. Tour → enter FPS during tour (should it work?)
E15. Tour → close panel → reopen → correct info?

### F. Content Panel (20 scenarios)
F1. Tap hotspot → panel opens → correct content?
F2. Scroll long content in panel
F3. × button closes panel
F4. Tap on 3D scene → panel closes
F5. Panel FREE entries (overview, em, ac, th, kings) → full content visible
F6. Panel PRO entries → blur + unlock banner visible
F7. Unlock banner → tap → PRO modal opens
F8. ◂▸ arrows → scroll button bar
F9. Resize with panel open
F10. Panel + overlay + mode change simultaneously
F11. Each SCI entry has: tag, color, title, desc, stats, src?
F12. Stats render as table rows?
F13. Equations render as pre-formatted?
F14. Sources cited at end?
F15. 100+ secret terms present (Serapeum, Dendera, Tesla, CIA, DMT, Göbekli, etc.)?
F16. Tap different hotspots rapidly (5 in 2s) → panel updates correctly?
F17. Panel open → tour starts → panel content changes per stop?
F18. Panel scroll position resets when new entry opens?
F19. Panel with very long desc text → doesn't overflow?
F20. Panel × button accessible while scrolled down?

### G. Night Mode (10 scenarios)
G1. Night ON → sky darkens, lights change (PRO gate works?)
G2. Night ON → TIME slider disabled?
G3. Night OFF → slider position restored?
G4. Night ON/OFF spam 10×
G5. Night + every overlay ON
G6. Night + tour
G7. Night + FPS (visible enough to navigate?)
G8. Night → tab switch → return → state correct?
G9. Night → resize → correct?
G10. Night ON → change modes → night persists?

### H. Construction (10 scenarios)
H1. Toggle ON → canvas animation starts (PRO gate?)
H2. Toggle OFF → animation stops
H3. ON/OFF spam 20×
H4. Construction + resize
H5. Construction + mode change
H6. 9 phases of construction visible?
H7. Workers animated?
H8. Ramp appears/disappears with progress?
H9. Construction + night mode
H10. Construction + overlay ON

### I. Audio (10 scenarios)
I1. Toggle ON → wind sound
I2. Toggle OFF → silence
I3. Toggle spam 50× in 2s
I4. FPS with audio → footstep sounds on movement?
I5. Audio + tab switch → continues?
I6. Audio + lock screen → pauses?
I7. Only one AudioContext created (no duplicates)?
I8. Volume changes between FPS and orbit?
I9. Audio + night mode
I10. Audio + tour

### J. Paywall (15 scenarios)
J1. Locked button → tap → PRO modal appears
J2. Modal: correct price (R$9.99 / $1.99 / €1.99)?
J3. Modal: × closes
J4. Modal: "Maybe later" closes
J5. Modal: "UNLOCK PRO" → Capacitor IAP or web fallback
J6. Web fallback: isPro=true → everything unlocks
J7. After unlock: locked buttons → normal appearance
J8. After unlock: blurred content → visible
J9. After unlock: tour completes all 15 stops
J10. After unlock: all 7 overlays work
J11. After unlock: FPS, night, construction, teleport, scale, casing all work
J12. Restore purchase (reinstall simulation)
J13. Console: isPro=true → bypass (acceptable risk?)
J14. Multiple taps on buy button
J15. Modal open → rotate device → modal still visible?

### K. Resize & Responsiveness (12 scenarios)
K1. Portrait → landscape → portrait
K2. Resize window (desktop drag)
K3. Split-screen Android
K4. Picture-in-picture attempt
K5. Keyboard opens (mobile — should not happen, no inputs)
K6. Notch/safe area/Dynamic Island
K7. Browser zoom (Ctrl +/-)
K8. System font size 200%
K9. System display size "largest"
K10. Foldable phone (fold/unfold)
K11. External monitor connected (desktop)
K12. Window minimize → restore → correct render?

### L. Edge Cases & Crash Resistance (18 scenarios)
L1. Low memory (many apps open)
L2. Battery saver mode ON
L3. System dark mode ON
L4. Screen reader (TalkBack/VoiceOver)
L5. System font size 200%
L6. Developer tools throttle CPU 6×
L7. Console: cam.position.set(NaN,NaN,NaN)
L8. Console: mode='INVALID'
L9. Console: overlays.em='string'
L10. Console: tourI=-999
L11. Console: fc.y=Infinity
L12. Very fast CPU (gaming PC, 240Hz) → timing issues?
L13. Very slow CPU (throttled) → frame drops graceful?
L14. WebGL context lost → recovery?
L15. Three.js CDN returns 404 mid-session
L16. Rapid orientation change (10× in 5s)
L17. Touch with gloves (imprecise)
L18. Stylus input

### M. Minimap, Compass, Scale, Casing (15 scenarios)
M1. Minimap renders in all modes?
M2. Minimap camera dot updates with movement?
M3. Minimap direction arrow correct?
M4. Compass N indicator rotates with camera?
M5. Compass correct in FPS mode?
M6. Scale comparison toggle (PRO gate?)
M7. Scale shows comparison structures?
M8. Casing toggle (PRO gate?)
M9. Casing shows white limestone?
M10. Casing + night mode
M11. Casing + overlay
M12. Scale + casing simultaneously
M13. Fullscreen toggle works?
M14. Fullscreen + FPS
M15. Fullscreen → exit → layout correct?

---

## FORMAT PER SCENARIO

```
[ID] [PASS/FAIL/WARN] — [Description of result] — [Fix if FAIL]
```

## FINAL SUMMARY
```
TOTAL: X/200 PASS | Y FAIL | Z WARN
CRITICAL FAILS: [list]
PASS RATE: X%
```

**Fix everything and apply the improvements.**
