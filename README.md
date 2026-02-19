# ISS Live Tracker

> *Real-time 3D tracking of the International Space Station — live telemetry, orbit trail, mission control aesthetic.*

A live 3D ISS tracker built with Three.js that plots the station's exact position on a rotating Earth globe, updated every 10 seconds from a live telemetry API. Built with a NASA mission control CRT aesthetic — amber readouts, scanlines, terminal boot sequence.

![Three.js](https://img.shields.io/badge/Three.js-r128-black?style=flat-square&logo=threedotjs) ![License](https://img.shields.io/badge/license-MIT-green?style=flat-square) ![Live](https://img.shields.io/badge/live-vercel-black?style=flat-square)

---

## ✨ Features

- **Live ISS position** — latitude, longitude, altitude, velocity updated every 10 seconds
- **3D Earth globe** — blue marble texture, topology bump map, specular water highlights
- **Orbit trail** — teal line traces the ISS's recent path across the globe in real time
- **Dynamic sun lighting** — directional light repositions based on actual solar coordinates from the API
- **NASA mission control aesthetic** — amber CRT terminal feel, scanline overlay, corner brackets
- **Terminal boot sequence** — staggered initialization screen before the globe appears
- **Mission elapsed clock** — counts up from the moment you open the page
- **Live refresh countdown** — animated bar shows exactly when the next data fetch fires
- **Projected ISS label** — "▲ ISS" floats above the dot in screen space, hides when behind Earth
- **Pulsing ISS glow** — animated breathing dot so the station is always easy to spot
- **Orbital parameters panel** — inclination, period, orbits per day, apogee
- **Visibility badge** — styled indicator for daylight vs eclipsed passes
- **Auto-rotating globe** — slow ambient spin so it never looks static
- **Atmosphere glow** — subtle blue haze around Earth's limb
- **5000 background stars** — randomized star field for depth
- **Single HTML file** — zero build step, zero dependencies to install

---

## 🚀 Getting Started

### Option 1 — Open directly
Double-click `index.html`. No server needed — the API is public and CORS-friendly.

### Option 2 — Live Server
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

Then open `http://localhost:8080`

### Option 3 — Deploy to Vercel
```bash
vercel --prod
```

---

## 🌐 Live Demo

**[your-url.vercel.app](https://iss-tracker.vercel.app)**

---

## 🎮 Controls

| Input | Action |
|-------|--------|
| **Drag** | Rotate the globe |
| **Scroll** | Zoom in / out |
| **Auto-rotate** | Globe slowly spins on its own |

---

## 📡 Data Source

Live telemetry is pulled from the **[wheretheiss.at](https://wheretheiss.at)** public API:

```
GET https://api.wheretheiss.at/v1/satellites/25544
```

Returns latitude, longitude, altitude, velocity, visibility, and solar position. No API key required. Updates every 10 seconds.

---

## 🛠 Tech Stack

| Technology | Purpose |
|------------|---------|
| [Three.js r128](https://threejs.org) | 3D rendering, globe, lighting, orbit trail |
| [OrbitControls](https://threejs.org/docs/#examples/en/controls/OrbitControls) | Drag/zoom interaction |
| [Share Tech Mono](https://fonts.google.com/specimen/Share+Tech+Mono) | Terminal monospace readouts |
| [Rajdhani](https://fonts.google.com/specimen/Rajdhani) | Aerospace UI headers |
| [wheretheiss.at API](https://wheretheiss.at/w/developer) | Live ISS telemetry |

---

## 📁 Project Structure

```
iss-tracker/
├── index.html    # Entire tracker — single self-contained file
└── README.md
```

---

## ⚙️ Configuration

Key constants at the top of the `<script>` block:

```js
const EARTH_RADIUS = 5;       // Globe size in scene units
const ISS_API_URL  = '...';   // Telemetry endpoint
const MAX_TRAIL    = 120;     // Number of orbit trail points to keep
```

Refresh interval (default 10 seconds):
```js
// In startRefreshCycle() — change the tick interval and initial timer value
refreshTimer = 10;
```

---

## 🌐 Browser Compatibility

| Browser | Status |
|---------|--------|
| Chrome 90+ | ✅ Full support |
| Edge 90+   | ✅ Full support |
| Firefox    | ✅ Full support |
| Safari     | ✅ Full support |

---

## 📖 Background Reading

- [ISS Orbital Parameters — NASA](https://www.nasa.gov/international-space-station/)
- [Three.js Docs](https://threejs.org/docs/)
- [wheretheiss.at API Docs](https://wheretheiss.at/w/developer)
- [Craig Reynolds — Boids (1987)](https://www.red3d.com/cwr/boids/)

---

## 📄 License

MIT — free to use, modify, and share.

---

*Built with Three.js · wheretheiss.at API · Google Fonts*