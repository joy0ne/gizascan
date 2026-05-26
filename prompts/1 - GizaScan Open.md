# 1 — GizaScan: App MUST Open and Render
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

You will receive the complete code of **"GizaScan"**: a standalone 3D app (single HTML, ~130 KB, ~1200 lines). Three.js r128 via CDN, Web Audio, Canvas 2D, FPS+Pointer Lock+touch joysticks, 7 overlays with 38 animated 3D elements, 16 SCI entries.

---

## MISSION: The app MUST open and render correctly on EVERY target platform.

## TARGETS
- **Chrome mobile via `content://`** (Android file manager opens HTML)
- **Chrome mobile via `file://`**
- **Chrome desktop**
- **Safari iOS / macOS**
- **Firefox desktop**
- **Capacitor WebView** (Android APK + iOS IPA)
- **GitHub Pages / https://**

## RENDERING CHECKLIST

### Initialization
- [ ] `init()` wrapped in try-catch with VISIBLE error feedback (show in #lpct)
- [ ] `init()` deferred to `window.onload` (DOM must be fully ready)
- [ ] Three.js CDN has `onerror` handler showing error to user
- [ ] NO `crossorigin="anonymous"` on Three.js CDN script (breaks `content://`)
- [ ] THREE.Clock created INSIDE init() AFTER `typeof THREE==='undefined'` check
- [ ] All builders wrapped in INDIVIDUAL try-catch (one failure doesn't kill others)
- [ ] Failed builders reported visibly on screen

### WebGL Compatibility
- [ ] `WebGLRenderer({antialias: false})` — antialias off for max compatibility
- [ ] `ren.setPixelRatio(1)` — pixel ratio 1 (not devicePixelRatio)
- [ ] `ren.shadowMap` — NOT set, or explicitly disabled
- [ ] NO `ren.toneMapping` (ACESFilmicToneMapping breaks Android content:// WebView)
- [ ] NO `ren.outputEncoding` (sRGBEncoding breaks Android content:// WebView)
- [ ] NO `scene.fog` (FogExp2 breaks some mobile GPUs)
- [ ] NO `castShadow=true` on ANY mesh (shadows make meshes vanish on content://)
- [ ] NO `receiveShadow=true` on ANY mesh

### Materials
- [ ] ZERO `MeshStandardMaterial` in the code (PBR shader fails on some mobile WebViews)
- [ ] ALL meshes use `MeshBasicMaterial` (or MeshLambert/Phong as fallback)
- [ ] Brighter colors and stronger ambient light to compensate for no lighting
- [ ] No `emissive` properties on non-emissive materials

### Canvas Textures
- [ ] Minimized — ideally only sky texture
- [ ] Small sizes (≤512×256 for sky)
- [ ] Return `null` from functions like `sTex()`, `nTex()`, `hTex()` to disable per-mesh textures
- [ ] Materials with `map:null` fall back to `color` — verify color is set

### Geometry
- [ ] Prefer BUILT-IN geometries (CylinderGeometry, BoxGeometry, ConeGeometry, SphereGeometry) over custom BufferGeometry
- [ ] If custom BufferGeometry used: call `geo.computeBoundingSphere()` and set `mesh.frustumCulled = false`
- [ ] Pyramid: use CylinderGeometry with 4 sides rotated 45° (NOT custom vertices)

### Viewport
- [ ] Canvas CSS: `width:100vw !important; height:100vh !important`
- [ ] `cam.aspect = innerWidth/innerHeight` — simple, no Math.max fallback hacks
- [ ] `ren.setSize(innerWidth, innerHeight)` — direct values
- [ ] Resize handler updates both camera and renderer
- [ ] Force `ren.render(scene, cam)` after loading completes (before animate() starts)

### Animation Loop
- [ ] `animate()` wrapped in try-catch so errors don't freeze the loop
- [ ] ZERO `new THREE.*` allocations per frame (use pre-allocated `_tmpV`, `_tmpE`, etc.)
- [ ] ZERO uncached `getElementById` calls (use cached refs like `_dgf`, `_cnEl`)
- [ ] Null guards on EVERY accessed variable: `if(dustP)`, `if(sandP)`, `if(intG)`, `if(_cnEl)`, etc.
- [ ] Compass uses `_tmpV` (NOT bare variable `d` from old code)
- [ ] Rename checks: no stale variable references after refactoring

### Critical Variables
- [ ] `clk` (Clock) assigned before first use in animate()
- [ ] `scene`, `cam`, `ren` all non-null before animate() starts
- [ ] Pre-allocated vectors (`_tmpV`, `_tmpE`, `_fwd`, `_rgt`, `_dir`, `_hsV`) all declared and assigned
- [ ] Cached DOM refs (`_dgf`, `_dgv`, `_muonInfo`, `_ldMuon`, `_wvEl`, `_cnEl`, `_ldEm`, `_ldAc`, `_ldTh`) all declared globally as `let` and assigned in init()

### Interior Visibility (X-Ray mode)
- [ ] Interior meshes have `depthTest: false` and `depthWrite: false`
- [ ] Interior meshes have `renderOrder: 999` (render on top)
- [ ] Shell materials have `depthWrite: false` when transparent
- [ ] X-Ray opacity = 0.15 (visible but lets interior show through)
- [ ] Interior colors BRIGHT (high contrast with stone)

### Paywall (must not block rendering)
- [ ] Paywall modal hidden by default (CSS `display:none`)
- [ ] Paywall check doesn't interfere with initial render
- [ ] `isPro=false` initially, all features WORK in FREE except paywalled ones

## PROCESS

1. Check EVERY item in the checklist above
2. Fix EVERY failure — even minor ones
3. Add visible error feedback if something fails silently
4. Test mentally: imagine the app running on Android `content://` Chrome
5. If anything could possibly prevent the 3D scene from appearing, fix it

## COMMON FAILURE MODES TO CHECK

- **Black screen**: Three.js CDN failed (add onerror), or `typeof THREE==='undefined'` not handled
- **Static scene after first frame**: ReferenceError in animate loop (check compass `d` vs `_tmpV`), or DOM cached refs scoped wrong
- **Sky and ground visible, no pyramid**: Custom BufferGeometry without `computeBoundingSphere`, or `castShadow=true` on shells
- **Everything invisible**: toneMapping/outputEncoding/fog breaking shader compilation
- **Interior not visible in X-Ray**: Missing `depthTest:false` or `renderOrder:999`

**Fix everything and apply the improvements.**
