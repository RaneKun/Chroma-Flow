# 🌊 [CHROMA FLOW](https://ranekun.github.io/Chroma-Flow/)

![WebGL2](https://img.shields.io/badge/WebGL-2.0-990000.svg)
![JavaScript](https://img.shields.io/badge/javascript-ES6+-yellow.svg)
![Platform](https://img.shields.io/badge/platform-browser-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Status](https://img.shields.io/badge/status-live-brightgreen.svg)

> *"A real GPU fluid simulation — velocity fields, swirling vorticity, dye that actually flows and mixes like smoke or ink in water."*

> Highly inspired from- [PavelDoGreat - WebGL-Fluid-Simulation](https://github.com/PavelDoGreat/WebGL-Fluid-Simulation)

---

## 🎨 What Is It?

**Chroma Flow** is a browser-based fluid simulation that runs entirely on your GPU via WebGL2. It's the same family of algorithms used in professional fluid dynamics and mobile "fluid paint" apps, but open-source and completely free.

- **Drag to stir** the fluid with your mouse or finger
- **Watch dye flow** and mix like smoke or ink in water
- **Auto mode** generates endless generative art patterns
- **Symmetry modes** create mandalas and kaleidoscopes
- **Built-in screen tester** for displays

<img width="2560" height="1440" alt="GraalVM17 Screenshot 2026 07 18 - 21 40 04 95" src="https://github.com/user-attachments/assets/e2b7cab6-d6cf-49d7-bf8e-f354765ef7ae" />

## ✨ Features

### 🌊 Fluid Physics
- **Stable Fluids** algorithm (Jos Stam, GDC 2003)
- **Vorticity confinement** — creates swirling tendrils
- **Pressure projection** — divergence-free flow
- **Real-time advection** — dye carried by velocity field
- **GPU-accelerated** — runs at 60fps on most devices

### 🎨 Creative Controls
- **Manual Mode** — paint the flow with your mouse
- **Auto Mode** — random splashes on the screen
- **7 Palettes** — Neon, Pastel, Fire, Ocean, Thermal, Aurora, Crimson
- **8 Symmetry Modes** — Mirror ×2/×4, Kaleidoscope ×3/×6/×8/×12, Mandala ×6/×10
- **6 Background Colors** — Black, White, Sage, Umber, Violet, Maroon

### 🖥️ Screen Testing
Built-in display testing tools:
- `1` — White (brightness / dead pixels)
- `2` — Black (dead pixel / backlight bleed)
- `3-5` — Red / Green / Blue
- `6` — 50% Gray (uniformity)
- `7` — RGB Stripes (subpixel)
- `8` — Gradient (banding)
- `9` — Spectrum (full hue sweep)
- `0` — Back to simulation

## 🚀 Quick Start

1. Open `chroma_flow.html` in a **modern browser** (Chrome, Edge, Firefox)

2. Click **"Enter Fullscreen & Begin"**

3. Start painting!

### No Installation Required
- Single HTML file — no server, no dependencies
- Works offline after first load
- Just double-click and go!

## 🎮 Controls

### Mouse / Touch
| Action | Effect |
|--------|--------|
| **Click & Drag** | Paint dye into the flow (Manual mode) |
| **Click & Drag (fast)** | Inject velocity — fluid swirls |

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Toggle Manual / Auto mode |
| `1-9` | Screen test patterns |
| `0` | Exit screen test |
| `C` | Clear canvas |
| `H` | Hide/show control panel |
| `R` | 🎲 Surprise! (random palette + symmetry) |
| `S` | 📸 Save PNG snapshot |
| `D` | Debug HUD (toggle) |
| `F` | Toggle fullscreen |
| `Esc` | Exit fullscreen / blur input |

## ⚙️ How It Works

### The Physics Engine

The simulation uses **Jos Stam's Stable Fluids** method, implemented entirely in WebGL2 fragment shaders:

1. **Curl** — measures local rotation of velocity
2. **Vorticity Confinement** — amplifies existing spin (creates curling tendrils)
3. **Divergence** — measures how "incompressible" the field is
4. **Pressure Solve (Jacobi)** — relaxes a pressure field to cancel divergence
5. **Gradient Subtraction** — removes pressure gradient from velocity
6. **Advection** — moves dye and velocity through the field
7. **Splat** — user input injects velocity + dye

### Symmetry Layer

Every splat passes through a symmetry transform before being applied:

- **Mirror** — reflects across centre lines
- **Kaleidoscope** — rotational symmetry (N copies)
- **Mandala** — rotational + reflection symmetry (2N copies)

### Rendering Pipeline

1. Dye + Bloom + Sunrays passes
2. **ACES Filmic Tonemap** — cinematic color grading
3. **Bloom** — soft glow on bright areas
4. **Sunrays** — radial light shafts from bright cores
5. Configurable background compositing

## 🎛️ Control Panel

### Sliders
| Control | Range | Effect |
|---------|-------|--------|
| **Brush Size** | 1-15 | Splat radius |
| **Trail Persistence** | 1-100 | How long dye lasts (higher = longer) |
| **Swirl Strength** | 0-60 | Vorticity confinement intensity |
| **Auto Speed** | 0.2-3.0 | Speed of auto-generated patterns |

### Palettes
| Palette | Description |
|---------|-------------|
| **Neon** | Bright, saturated cyberpunk colors |
| **Pastel** | Soft, gentle tones |
| **Fire** | Reds, oranges, yellows |
| **Ocean** | Blues, teals, cyans |
| **Thermal** | Blue → magenta → orange sweep |
| **Aurora** | Green → cyan → violet |
| **Crimson** | Red → pink → orange monochrome |

### Symmetry Modes
| Mode | Copies | Description |
|------|--------|-------------|
| **Off** | 1 | No symmetry |
| **Mirror ×2** | 2 | Reflect across vertical axis |
| **Mirror ×4** | 4 | Reflect across both axes |
| **Kaleido ×3** | 3 | 3-way rotational |
| **Kaleido ×6** | 6 | 6-way rotational |
| **Kaleido ×8** | 8 | 8-way rotational |
| **Kaleido ×12** | 12 | 12-way rotational |
| **Mandala ×6** | 12 | 6-way + reflection |
| **Mandala ×10** | 20 | 10-way + reflection |

## 🖥️ System Requirements

### Browsers
- ✅ **Chrome** 56+
- ✅ **Edge** 79+
- ✅ **Firefox** 51+
- ❌ Safari (WebGL2 support varies)
- ❌ Internet Explorer (not supported)

### Hardware
- GPU with WebGL2 support
- Float render targets (EXT_color_buffer_float)

### Performance
- **Dedicated GPU** → No worries!
- **Integrated GPU** → Adaptive quality scaling
- **Mobile** → Adjusts automatically

### 🙏 Credits
Made with ♥ by Rane Kun
