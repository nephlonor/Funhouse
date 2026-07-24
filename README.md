# Funhouse

Live, face-tracked camera warps in a single HTML file — no build step, no server, everything runs on-device.

Open `index.html` over **HTTPS** (or `localhost`) and tap **Turn on camera**.

## Features

- 19 real-time WebGL warps (balloon, bug eyes, big mouth, alien, swirl, googly, kaleido, and more).
- 8 colour looks (clarity, mono, sepia, lo-fi, thermal, VHS, comic).
- Optional face tracking via [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) — loaded lazily. If the model can't load, warps fall back to a centre-locked head position.
- Front/back camera switch, capture, and share-to-Photos.

## Running

It's a static file. Any HTTPS host works, e.g.:

```sh
python3 -m http.server 8000
```

then open `https://localhost:8000` (camera access requires a secure context).
