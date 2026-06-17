# lookdev

![License: MIT](https://img.shields.io/badge/license-MIT-blue) ![Claude Code skill](https://img.shields.io/badge/Claude%20Code-skill-d97757) ![Human-in-the-loop](https://img.shields.io/badge/human--in--the--loop-46d39a) ![Web · Three.js](https://img.shields.io/badge/web-Three.js-111)

**Stop guessing values from a screenshot. lookdev spins up a live, in-browser studio — sliders, color pickers, drag handles, inline markup — so you *dial in* AI-generated output by eye, then bakes the chosen state back into reproducible assets or code.**

![lookdev: a bas-relief XPS extrusion studio rendering a depth map into a 3D relief, with a full control panel and ViewCube](docs/lookdev.png)

*A real lookdev studio (the relief-extrusion example). Drag a control → it re-renders; you never type a number you guessed.*

## 🤔 Why

Claude Code is text-first, so it tends to **guess** visual values — a blur radius, an easing curve, a crop, a grade — from a static screenshot, then ask you to react in prose. That loop is slow and lossy. lookdev adds the missing interaction mode: a **real-time visual studio with a human in the loop**. You act on the artifact; the change is captured; the agent gets exact values back.

> **What this is:** not a one-shot render and not a Q&A where you dictate numbers — a studio you manipulate, where "show me, I'll pick" beats "ask me to specify."

## 🔁 How it differs from how most people use Claude Code

![How lookdev differs: most Claude Code use is a text round-trip where Claude guesses values from a screenshot; lookdev builds a live studio you tune by eye, capturing exact values](docs/how-it-works.svg)

Most Claude Code work is text the whole way down — you describe a look, Claude *guesses* the values from a screenshot, hands back code, you eyeball it, describe the fix in prose, and wait for the next round. Every iteration is a **time-delayed round-trip**: generate → wait → critique in words → regenerate, minutes at a time.

lookdev collapses that to **seconds of real-time feedback**. Claude builds the studio once; then **you** drag a slider and the result updates live — no waiting on a regeneration to find out whether 12px or 16px was right. The slow part of agent iteration was never the compute, it's the **human round-trip** — the back-and-forth of putting visual fixes into words. Tuning by hand removes it, and the exact state you land on (not a guess) becomes the code or asset.

> **We didn't invent this.** It's a pattern already emerging in agent workflows — call it *ephemeral tooling*: the agent builds a disposable, single-use interface for one tuning session instead of iterating blind. lookdev just codifies it into a repeatable skill.

## ✨ What it does

- 🎛️ **Live controls** — sliders, pickers, drag handles, scrubbers; tune and see the result instantly
- 🖼️ **Image processing** — dither, halftone, posterize, ASCII, blur, edge, quantize, color-grade
- 🎨 **Color** — palette extraction (coverage %), per-band pickers, saturation / contrast / gamma curves, theme tokens
- 🔤 **Typography** — font / size / weight / leading / tracking / measure on live sample text
- 📐 **Layout & framing** — draggable, selectable elements; resize handles; spacing rulers; snap-to-grid; aspect-lock crop
- 🌀 **Animation** — easing-curve editor, duration sliders, scrubber, replay
- 🧩 **Component variants** — hover / focus / disabled / loading / dark, side by side
- 🟦 **3D / render lookdev** — orbit, material (color · roughness · metalness · stone presets), lighting rigs, ViewCube — the relief studio above
- 📝 **Text & media review** — inline editing + selection highlight + anchored margin comments for posts, copy, and media sets
- 💾 **Reproducible** — the chosen state round-trips to JSON / settings (and, for the relief studio, into exported STL metadata)

## 🧭 Two studio shapes

| | 🎚️ Visual-parameter lookdev | 📝 Text & media lookdev |
|---|---|---|
| The artifact | look set by numbers/choices (color, type, layout, image, 3D) | a document, post, copy, or media set |
| Controls | sliders · pickers · drag handles | inline edit · highlight · margin comments · media annotation |
| You're doing | tuning by feel | editing / curating / marking up |

## 📦 Install (Claude Code plugin)

```
/plugin marketplace add connerkward/ckw-skills
/plugin install lookdev@connerkward
```

Standalone (this repo only):

```
/plugin marketplace add connerkward/lookdev-studio-skill
/plugin install lookdev@lookdev
```

Or drop this repo's `SKILL.md` into your agent's skills directory.

## 🗂️ Part of [ckw-skills](https://github.com/connerkward/ckw-skills)

The human-in-the-loop sibling of [`lookdev-auto`](https://github.com/connerkward/lookdev-auto-skill) (a vision model is the eye) and [`deterministic-design`](https://github.com/connerkward/deterministic-design-skill) (measure the UI instead of trusting the eye).

## License

MIT © Conner K Ward
