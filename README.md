# Funhouse

Live, face-tracked camera warps in a single HTML file — no build step, no server, everything runs on-device.

Open `index.html` over **HTTPS** (or `localhost`) and tap **Turn on camera**.

## Features

- 27 real-time WebGL warps (balloon, bug eyes, big mouth, alien, swirl, googly, kaleido, jelly, twist, spikes, dizzy, and more).
- 18 face-tracked character masks drawn as an AR overlay — unicorn, frog, dog, cat, bunny, pig, bear, reindeer, devil, crown, shades, clown, halo, gentleman, party, flower crown, heart eyes, star eyes. Masks and warps stack, and both composite into saved photos.
- Optional face tracking via [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) — loaded lazily. If the model can't load, warps and masks fall back to a centre-locked head position.
- Front/back camera switch, capture, and share-to-Photos. Raw video, no colour filters.

## Running

It's a static file. Any HTTPS host works, e.g.:

```sh
python3 -m http.server 8000
```

then open `https://localhost:8000` (camera access requires a secure context).
