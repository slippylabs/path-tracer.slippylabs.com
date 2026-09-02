# Path Tracer

Progressive Monte Carlo path tracer running in a Web Worker — diffuse, metal and glass materials, adjustable bounces, and a furnace test that proves the maths conserves energy.

**Live:** <https://path-tracer.slippylabs.com/>

## What it does

- Progressive Monte Carlo path tracer, rendering in a Web Worker so the page stays responsive.
- Diffuse, metal and glass materials, with adjustable bounce depth and resolution.
- Scenes include an emissive night scene and a furnace test.
- Download the accumulated frame as a PNG.

## How it works

The image refines in place: each pass traces one more sample per pixel and averages it into the accumulation buffer, so the render starts noisy and converges rather than making you wait for a final frame.

The **furnace test** is the interesting scene. Put a perfectly reflective object inside a uniformly emissive enclosure and the correct answer is that the object disappears — it must render exactly the same brightness as its surroundings. If it shows up darker the material is losing energy, brighter and it is inventing it. It is a rendering unit test you can see, and it is the reason the BRDF sampling and its PDF weighting can be trusted here.

## Run it locally

A static site. No build step, no package manager, no dependencies:

```
git clone git@github.com:slippylabs/path-tracer.slippylabs.com.git
cd path-tracer.slippylabs.com
python3 -m http.server 8000
```

Then open <http://localhost:8000>.

---

Part of [Slippy Labs](https://slippylabs.com). Every tool is indexed at
[projects.slippylabs.com](https://projects.slippylabs.com).
