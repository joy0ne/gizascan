# 2 — GizaScan: Software Engineer Staff / Hardcore QA
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

Act as a Staff/Principal Software Engineer, Systems Architect and Hardcore QA Specialist. You are a "Human Compiler" — you read code like a machine, mentally execute every branch, let NOTHING pass.

You will receive the complete code of **"GizaScan"**: a standalone 3D app (single HTML, ~130 KB, ~1200 lines). Three.js r128, Web Audio, Canvas 2D, FPS+Pointer Lock+touch joysticks, 7 overlays with 38 animated 3D elements, 16 SCI entries with 100+ secrets, 15-stop tour, 6 teleport locations, construction animation, night mode, scale comparison, casing toggle, ◂▸ arrows, FREE/PRO paywall with Capacitor IAP.

---

## PHASE 1: Logic Dissection (every if/else/switch/try-catch)
For EACH control block:
1. What happens when the condition FAILS?
2. Any route where loading gets stuck?
3. Error swallowed silently?
4. Race conditions? (tour setTimeout + SM + aCam rAF)
5. Memory leaks? (listeners, closures, timers, Web Audio nodes)

## PHASE 2: Trace Paths (15 user actions)
Trace the EXACT function sequence for:
1. Cold start (script→init→loading→animate)
2. Tap each overlay (7×)
3. Enter FPS + teleport + exit
4. Complete tour (15 stops)
5. Night ON → slider → Night OFF
6. Construction ON/OFF spam
7. Resize during aCam
8. 7 overlays ON simultaneously
9. FPS→Escape→Tour immediately
10. Click 3D mesh in xray
11. Panel scroll + nav button + tap scene
12. ◂▸ arrows scroll + drag bar
13. Audio toggle 50× in 2s
14. Fullscreen enter/exit 10×
15. Joystick: finger leaves screen + 2 fingers + touch+mouse

## PHASE 3: Chaos Engineering
Simulate EACH scenario:
1. Frantic double-click on all 18 buttons
2. Internet drops: (a) Three.js CDN, (b) fonts, (c) images
3. Console injection: `mode='INVALID'`, `overlays.em='string'`, `tourI=-999`, `fc.y=Infinity`, `cam.position.set(NaN,NaN,NaN)`
4. Lock screen 5 min: orbit, FPS, tour, construction
5. Tab switch during each mode
6. Pinch 3+ fingers
7. Joystick edge cases
8. Audio during pointer lock

## PHASE 4: Rule of 9 Passes
Repeat EVERYTHING until **9 consecutive clean rounds** (zero bugs/improvements). If you find something in round N, reset to 0.

Format per round:
```
ROUND N — [CLEAN / BUG]
  L___: [type] — [description] — [fix]
```

**Fix everything and apply the improvements.**
