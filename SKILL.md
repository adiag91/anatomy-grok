---
name: anatomy
description: Build crafted, highly detailed, interactive isometric SVG figures that explain a technical idea as a real physical object (a test rig, a dial gauge, a cabinet of drawers, a plotter, a lock), with many small precise solid parts, four-tone shading, correct painter's order, a framed card with title, hint and live readout, and calm eased motion. Use this whenever someone wants an isometric illustration, an explanatory diagram or figure for docs, a blog post, a landing page or an article, a "Linear-style" or "premium" technical drawing, an interactive explainer, or an SVG that shows how a system, algorithm or component works, even if they never say "isometric". Works framework-free (HTML/JS that writes SVG) and can be extended with the original kit. Adapted for Grok Build / Grok.
user-invocable: true
---

# Anatomy (Grok Build edition)

This skill makes figures like a small instrument on a bench: a heavy base on feet, rails with tick rulers, a carriage on bushings, knurled knobs, coil springs, a dial gauge whose needle moves, screws as tiny dots. The reader understands the idea because they recognise the machine. Every number the figure shows comes from the same model that moves its parts.

**The object is the explanation.** Don't draw boxes, arrows and labels. Invent a real, well-made physical thing whose working *is* the concept.

## Setup for Grok Build

Before building a complex figure, clone the original kit (it is MIT licensed and agent-friendly):

```bash
git clone --depth 1 https://github.com/wheresryan22/anatomy.git /tmp/anatomy-kit
```

Then work inside or reference `/tmp/anatomy-kit`. For simpler figures you can generate pure SVG/HTML without the full kit using isometric projection math.

Open the closest example in the kit (`examples/dial-indicator/`, `examples/test-rig/`, etc.) before starting if the kit is cloned.

## The one idea that matters

Invent a recognisable machine built from many small, precise, purposeful parts. At 1× it reads as one clear machine. At 4× every region still has something true to find.

## Workflow (adapted for Grok tools)

Work in this order. Use `bash` for cloning/running Node, `write_file` / `edit_file` for source, and verify outputs.

1. **Size it.** Tell the user: Figure (40–80 parts, ~30–90 min), Hero (80–150), or Epic. Build a working page within the first hour.
2. **Truth first.** Collect real numbers. Write a small pure model (JS function or module) that drives motion and readouts.
3. **Invent the object.** One sentence: what moves and what that motion means.
4. **Parts list.** ≥40 parts, grouped: base, structure, mechanism, controls, lit subject. Each sits on another.
5. **Plan the world.** World units ~1 px. Camera: azimuth 45°, elevation 30°. Use isometric projection.
6. **Build geometry.** Prefer the kit's `iso-kit.mjs`, `lathe.mjs`, `tube.mjs` if cloned. Otherwise implement basic isometric solids (slabs, cylinders) with 4-tone shading (lo/mid/hi + one lit accent).
7. **Paint back to front.** Depth-sort. Split wrapping parts. No floating lines.
8. **Frame it.** Card with title, interaction hint, live readout. Words outside the drawing.
9. **Make it live.** Calm motion (springs or exponential follow). Idle tour, pointer/keyboard, reduced-motion still. Standalone HTML is preferred.
10. **Verify.** Use `bash` to run Node audits if kit present (`node build.mjs --audit`). Inspect generated HTML/SVG. Fix overlaps, line ends, clearances.

## Craft rules (short)

- Solids only, filled, painted in depth order. No wireframes or arrows.
- Four tones based on face angle to light. Exactly one lit accent part.
- Lines resolve: every line ends on a face, edge or dot.
- Detail at 4×. Screws as dots, bevels, knurls, ticks.
- True numbers from the model.
- No labels inside the drawing.

## Output

Prefer a single self-contained HTML file (SVG + JS) that can be opened in a browser. For React/Next, follow the kit's `react/` patterns if available.

When done, provide the file path and a short description of the machine and what it explains.

## Notes for Grok

- Use the sandbox `bash` tool freely for Node, git, file ops.
- Save final figures under `/workspace/artifacts/` so the user can download them.
- If the full kit is too heavy for a quick request, produce a high-quality simplified isometric version that still follows the "object is the explanation" rule and the shading/depth principles.
- Always start with the numerical model before drawing.
