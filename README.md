# 🌀 MiMoMorph

### Photo Glitch & Distortion Tool — Powered by Xiaomi MiMo V2.5

A fully client-side photo manipulation tool that applies 16 glitch and distortion effects to your images. Pixel sort, RGB shift, VHS distortion, datamosh, kaleidoscope, chromatic aberration — all running in your browser with zero uploads, zero API keys, zero dependencies.

[![Live Demo](https://img.shields.io/badge/Live-Demo-000?style=for-the-badge&logo=github)](https://gyoomei.github.io/mimomorph/)
[![Try Now](https://img.shields.io/badge/Try-Now-ec4899?style=for-the-badge&logo=googlechrome)](https://gyoomei.github.io/mimomorph/)
[![AI](https://img.shields.io/badge/AI-Xiaomi%20MiMo%20V2.5-f97316?style=for-the-badge)](https://mimo.xiaomi.com/)
[![Zero API](https://img.shields.io/badge/Zero-API-22c55e?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

---

## 📖 The Problem

Glitch art tools are either desktop-only (Processing, After Effects), require server uploads (online editors), or are limited to Instagram-style filters. There's no instant browser-based tool with real pixel-level glitch effects — pixel sorting, datamoshing, VHS distortion, kaleidoscope — that processes everything locally without sending your photos anywhere.

## ✨ How it works

```
You upload:   Drag & drop or click Open
You stack:    Pick effects, adjust sliders, Apply each
You compose:  Chain 16 effects in any order, undo freely
You export:   PNG at full resolution
```

**That's the entire UX** — upload, glitch, export. No accounts, no uploads to servers, no watermarks.

## 🎯 Core Features

| Capability | Detail |
|---|---|
| Effects | 16 pixel-level: RGB Shift, Pixel Sort, Scanline, Wave, Glitch Blocks, Noise, Posterize, Threshold, Pixelate, Invert, Channel Swap, VHS Distort, Kaleidoscope, Datamosh, Chromatic Aberration, Emboss |
| Presets | 6 one-click presets: VHS, Cyberpunk, Retro, Corrupt, Dream, Horror |
| Stack System | Chain multiple effects, remove any from stack, reapply all |
| Undo | Full undo history per effect application |
| Adjustable Params | Per-effect sliders (threshold, intensity, block size, etc.) |
| Drag & Drop | Drop images directly onto the canvas |
| Auto-Resize | Large images scaled to 1200px max for performance |
| Export PNG | Full resolution, no watermarks |
| Dark/Light Theme | Toggle with persistence |
| Mobile Responsive | Touch-friendly controls |

## 🏗️ Architecture

```
┌──────────────────────────────────────────┐
│  Canvas 2D ── ImageData Pixel Engine     │
│       │                                   │
│  Upload ──── FileReader → drawImage       │
│  Process ─── getImageData → pixel loop    │
│  Preview ─── putImageData → display       │
│       │                                   │
│  16 Effects ── Per-pixel transforms       │
│  Stack ────── Chain + undo + reapply      │
│  Presets ──── Curated effect combos       │
└──────────────────────────────────────────┘
```

## 💡 Architecture Decisions

**Why Canvas ImageData?** Every effect operates on raw pixel arrays — `getImageData()` returns an RGBA buffer that we transform pixel-by-pixel. This is the most natural API for glitch art: RGB channel shifts, pixel sorting by brightness, block displacement, scanline overlays — all are simple array operations on the RGBA buffer.

**Why a stack system?** Glitch art is about layering. Apply pixel sort first, then add scanlines, then shift RGB — the order matters. The stack lets you compose complex effects from simple primitives and remove any layer without undoing everything.

**Why single HTML?** Image processing is CPU-bound, not network-bound. Everything runs in the browser's Canvas context. Zero servers means zero privacy concerns — your photos never leave your device.

## 🧪 Try these examples

| Preset | What it does |
|---|---|
| VHS | Scanlines + horizontal distortion + noise → retro tape look |
| Cyberpunk | RGB shift + scanlines + posterize → neon city aesthetic |
| Retro | Posterize + noise + scanlines → vintage photograph |
| Corrupt | Glitch blocks + datamosh + RGB shift → broken file aesthetic |
| Dream | Gentle wave + posterize + soft noise → ethereal look |
| Horror | Threshold + heavy noise + glitch blocks → dark distorted |

## 🛠️ Stack

- **Frontend:** Vanilla JavaScript, single HTML file (~30KB)
- **Engine:** Canvas 2D ImageData pixel manipulation (16 effects)
- **Fonts:** [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) + [Outfit](https://fonts.google.com/specimen/Outfit) + [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono)
- **Storage:** localStorage for theme preference
- **Hosting:** GitHub Pages (zero infra cost)

## 🚀 Quick Start

```bash
git clone https://github.com/gyoomei/mimomorph.git
open mimomorph/index.html
# or
python3 -m http.server 8080 -d mimomorph
```

## 📄 License

MIT — free for personal and commercial use.

**Built with 🧠 [Xiaomi MiMo V2.5](https://mimo.xiaomi.com/) · Submitted to [MiMo 100T program](https://mimo.xiaomi.com/)**
