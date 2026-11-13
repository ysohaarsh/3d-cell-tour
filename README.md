# 3D Cell Tour

An interactive 3D model of a human cell, built entirely from code — one organelle at a time.
Single HTML file, [three.js](https://threejs.org/), no build step.

[![Overview](screenshots/overview.png)](cell-tour.mp4)

**▶ [Watch the narrated video](cell-tour.mp4)** (1:53, 1080×1080, rendered frame-by-frame from the same code)

## Run it

Open `index.html` in a browser. Needs internet on first load (three.js comes from a CDN).

Or serve it locally:

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

## Controls

| Input | Action |
|---|---|
| Drag | Orbit the model |
| `←` / `→` or ◀ ▶ | Previous / next step |
| `Space` or ❚❚ | Play / pause |
| ♪ | Toggle narration (browser text-to-speech) |
| `index.html#N` | Jump to step `N` (0-based), paused |

## The 15 steps

| # | Step | |
|---|---|---|
| 1 | One human cell (20 µm scale bar) | ![](screenshots/01-cell.png) |
| 2 | Cell membrane + bilayer close-up | ![](screenshots/02-membrane.png) |
| 3 | Nucleus: DNA as loose thread, nucleolus | ![](screenshots/03-nucleus.png) |
| 4 | Nuclear pores + messenger RNA | ![](screenshots/04-nuclear-pores.png) |
| 5 | Ribosomes | ![](screenshots/05-ribosomes.png) |
| 6 | Rough ER | ![](screenshots/06-rough-er.png) |
| 7 | Smooth ER | ![](screenshots/07-smooth-er.png) |
| 8 | Golgi apparatus | ![](screenshots/08-golgi.png) |
| 9 | Mitochondria (one cut open) | ![](screenshots/09-mitochondria.png) |
| 10 | Lysosomes | ![](screenshots/10-lysosomes.png) |
| 11 | Peroxisomes | ![](screenshots/11-peroxisomes.png) |
| 12 | Centrosome: two centrioles | ![](screenshots/12-centrosome.png) |
| 13 | Cytoskeleton: microtubules, actin, intermediate filaments | ![](screenshots/13-cytoskeleton.png) |
| 14 | One cell, assembled | ![](screenshots/14-assembled.png) |
| 15 | About 30 trillion of them | ![](screenshots/15-many-cells.png) |

## How it's built

- **Toon look:** `MeshToonMaterial` with a 3-step gradient, plus inverted-hull outlines for the inked edges.
- **Procedural geometry:** wobbly cell blob, extruded ER sheets, merged-cylinder smooth-ER web, lathe-cut mitochondrion with folded inner membrane, instanced ribosomes.
- **Choreography:** each part has a visibility rule per step and pops, fades or counts in with staggered delays. The camera tweens between framed shots.
- **Overlays:** captions, callout leaders and the membrane close-up are HTML/SVG positioned from projected 3D points.

## Credit

Inspired by [this post from @claudeai](https://x.com/claudeai/status/2120174844822298730), which showcased a cell model by @kevin_t_ngo.
This is an independent re-implementation. No code or assets from the original.
