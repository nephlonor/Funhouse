# Funhouse

Live, face-tracked camera warps in a single HTML file — no build step, no server, everything runs on-device.

Open `index.html` over **HTTPS** (or `localhost`) and tap **Turn on camera**.

## Features

- 27 real-time WebGL warps (balloon, bug eyes, big mouth, alien, swirl, googly, kaleido, jelly, twist, spikes, dizzy, and more).
- 18 **real 3D** character masks rendered with [three.js](https://threejs.org) — unicorn, frog, dog, cat, bunny, pig, bear, reindeer, devil, crown, shades, clown, halo, gentleman, party, flower crown, heart eyes, star eyes. The 468 MediaPipe landmarks (including their z depth) are turned into a full head pose — position, orientation (pitch/yaw/roll) and scale — and each rig is drawn with PBR materials, lighting, tone mapping and a real depth buffer. A hidden head occluder makes accessories wrap around the head. Masks and warps stack, and both composite into saved photos.
- Face tracking via [MediaPipe Tasks Vision](https://developers.google.com/mediapipe) — loaded lazily. Warps fall back to a centre-locked head position if the model can't load; the 3D masks need a tracked face.
- Front/back camera switch, capture, and share-to-Photos. Raw video, no colour filters.

three.js is loaded lazily from a CDN the first time a 3D character is selected, so the page still works offline for the warp filters.

## Worn glTF models

The 3D character rail also supports **full worn-head glTF models** (loaded with three.js `GLTFLoader`), tracked with the same head pose and idle-animated via `AnimationMixer`. To add one, download a `.glb` (see below) and add a registry entry in `index.html`:

```js
const GLTF_SPEC = {
  20: { url:'./models/dog.glb', fit:2.6, rotY:Math.PI, y:1.1, anim:0 },
  // fit = target size in face-width units; rotY/x/y/z place it on the head; anim = clip index
};
```

then add a matching chip to the `MASKS` array. Point `url` at a file committed under `models/` (same-origin, most reliable) or a CORS-enabled CDN URL.

Good sources for **free, permissively-licensed** low-poly models (glTF/GLB):

- [Poly Pizza](https://poly.pizza) — especially [Quaternius](https://poly.pizza/u/Quaternius)'s uploads, which are **CC0** (no attribution required); e.g. the [Animated Animal Pack](https://poly.pizza/bundle/Animated-Animal-Pack-ILAPXeUYiS) and [Farm Animal Pack](https://poly.pizza/bundle/Farm-Animal-Pack-1kUvRTPLzT).
- [quaternius.com](https://quaternius.com) — the same CC0 packs, downloadable directly.

Check the license badge on each model page; non-Quaternius Poly Pizza models are usually **CC-BY** and require a credit.

## Credits

- **Fox** — model by PixelMannen (CC0), rig & animation by Tom Kranis (CC-BY 4.0), distributed as a glTF sample with [three.js](https://github.com/mrdoob/three.js/tree/dev/examples/models/gltf/Fox).

## Running

It's a static file. Any HTTPS host works, e.g.:

```sh
python3 -m http.server 8000
```

then open `https://localhost:8000` (camera access requires a secure context).
