# 3 — GizaScan: Performance Engineer / V8+WebGL Architect
I don't want you to describe everything you are processing or the reports, and the final result, the updated file.

Act as a Staff Performance Engineer, V8 Engine Specialist (Chrome) and Web Rendering Architect. Target: 60fps on Snapdragon 425 (2 GB RAM, Adreno 308).

You will receive the complete code of **"GizaScan"**: a standalone 3D app (single HTML, ~130 KB, ~1200 lines). Three.js r128, ~200 draw calls worst-case, particles (sand 1500, dust 800, muons 200, charge 120), 38+ animated overlay meshes (tunnels, Osiris, Sphinx chamber, water table, Tesla bolts, crystal lattice, Earth wireframe, DNA helix, Platonic solids, great circle, megalithic markers), Canvas 2D (minimap+waveform+construction), Web Audio.

---

## PHASE 1: Rendering Bottlenecks

**1A — Allocations/frame**: count EVERY `new THREE.*`, `.clone()`, `new Array`, `.map()`, `.filter()`, template literals in the animate loop + all called subfunctions (upHS, drawMM, updateLiveData, drawWaveform). Calculate: bytes/frame × 60 = KB/s GC pressure. Pre-allocate EVERYTHING.

**1B — DOM thrashing**: count EVERY `getElementById`, `.style.*`, `.classList.*`, `.textContent`, `.setAttribute`, `.innerHTML` in the loop. Cache ALL refs in global variables assigned in init().

**1C — Draw calls**: list draw calls per mode (orbit/xray/FPS/all overlays). Identify merge opportunities (InstancedMesh for scattered blocks? Merge geometry for shells?).

**1D — Particle systems**: for EACH system (sand 1500, dust 800, muons 200, charge 120), verify: bounds check (particles escape?), needsUpdate (called every frame?), estimated CPU cost.

**1E — GPU pipeline**: shadow map size, pixel ratio, antialias, toneMapping, outputEncoding — each on mobile.

## PHASE 2: Big O — Complete Table

For EACH function/loop in animate:
```
function | O(?) | n | estimated ms | when active | optimizable?
```
Include: oc.update, capstone, intG.children flames, dustP loop, emFieldMeshes, acWaves, thHeatmap, starLines, geoLayers (with water table vertex anim), mathOverlays (with Platonic orbit), energyMeshes (with charge particles), sphinxG, sandP loop, godRays, muonParticles, upHS, drawMM, drawWaveform, updateLiveData, compass.

Calculate TOTAL worst-case CPU and compare with 16.6ms budget.

## PHASE 3: Memory Leaks & VRAM

1. Event listeners: how many added, where, removed?
2. Web Audio: oscillators created/destroyed, permanent nodes, audioCtx.close()?
3. Timers: setInterval, setTimeout, rAF — all cleaned?
4. VRAM: textures (count, size), geometries (count, vertices), materials. Total MB.
5. Geometry/Material/Texture created AFTER init?
6. .dispose() called anywhere?

## PHASE 4: Concrete Optimizations

For EACH optimization:
```
BEFORE: [exact code]
AFTER: [exact code]
SAVINGS: CPU ms | Memory KB/s | GPU draws | % of 16.6ms budget
```

## PHASE 5: Worst Case Benchmark

Scenario: Night + ALL 7 overlays + muons + waveform + construction + FPS + audio + all animations on Snapdragon 425.

Calculate frame budget for:
- Desktop (RTX/Apple M-series)
- Mid-range mobile (Snapdragon 600-series)
- Low-end mobile (Snapdragon 425, Adreno 308)

**Fix everything and apply the improvements.**
