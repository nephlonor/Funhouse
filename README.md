# Funhouse

Live, face-tracked camera warps in a single HTML file — no build step, no server, everything runs on-device.

Open `index.html` over **HTTPS** (or `localhost`) and tap **Turn on camera**.

## Features

- 27 real-time WebGL warps (balloon, bug eyes, big mouth, alien, swirl, googly, kaleido, jelly, twist, spikes, dizzy, and more).
- 18 **real 3D** character masks rendered with [three.js](https://threejs.org) — unicorn, frog, dog, cat, bunny, pig, bear, reindeer, devil, crown, shades, clown, halo, gentleman, party, flower crown, heart eyes, star eyes. The 468 MediaPipe landmarks (including their z depth) are turned into a full head pose — position, orientation (pitch/yaw/roll) and scale — and each rig is drawn with PBR materials, lighting, tone mapping and a real depth buffer. A hidden head occluder makes accessories wrap around the head. Masks and warps stack, and both composite into saved photos.
- Face tracking via [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) — loaded lazily. Warps fall back to a centre-locked head position if the model can't load; the 3D masks need a tracked face.
- Front/back camera switch, capture, and share-to-Photos. Raw video, no colour filters.

three.js is loaded lazily from a CDN the first time a 3D character is selected, so the page still works offline for the warp filters.

## Running

It's a static file. Any HTTPS host works, e.g.:

```sh
python3 -m http.server 8000
```

then open `https://localhost:8000` (camera access requires a secure context).
