# Music Visualizer (Vite + React)

![screenshot placeholder](./screenshot.png)

A browser audio visualizer that uses microphone input via Web Audio API and fallback demo mode. Built with Vite + React + plain CSS.

## Features

- Microphone setup using `navigator.mediaDevices.getUserMedia({ audio: true })`
- Web Audio pipeline: `AudioContext` → `createMediaStreamSource` → `createAnalyser`
- `analyser.fftSize = 256`; `analyser.smoothingTimeConstant = 0.82`
- Real-time frequency updates via `analyser.getByteFrequencyData()`
- Four visualization modes: Bars, Wave, Radial, Particles
- Sensitivity slider (1–5)
- Mic toggle with red active state and status message
- Demo mode with synthetic sine wave data when mic is off

## Install & Run

```bash
npm install
npm run dev
```

## How it works

1. The app requests microphone permission and, on success, connects it to an `AnalyserNode`.
2. On each `requestAnimationFrame`, the visualizer reads frequency bins and transforms them into graphics.
3. In mic-off state, demo data is generated (sine-based wave) so canvas is never blank.

## Deploy to Netlify

1. Push repository to GitHub.
2. Create a new site on Netlify from GitHub.
3. Set build command: `npm run build`, publish directory: `dist`.
4. Deploy and enjoy.

