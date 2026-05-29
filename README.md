# AR/VR Web Experiences

A collection of browser-based augmented and virtual reality demos built with [A-Frame](https://aframe.io/), [AR.js](https://ar-js-org.github.io/AR.js/), and [MindAR](https://hiukim.github.io/mind-ar-js-doc/). An Express server hosts static assets so you can run every scene locally with a single command.

## Overview

This project explores common AR/VR patterns on the web: marker tracking, image-target tracking, geolocation-triggered content, 360° panoramas, GLB model loading, and interactive 3D scenes. Each demo lives in its own HTML page under `public/`, making it easy to study or extend individual techniques.

## Features

| Demo | URL | Description |
|------|-----|-------------|
| Marker AR (AR.js) | `/index.html` | Pattern marker tracking with 3D primitives overlaid on a printed target |
| Image target (MindAR) | `/midar.html` | Image-based AR with an animated torus anchored to a target image |
| GLB on image target | `/glb_target_img.html` | MindAR scene with a rotating GLB model on an image target |
| GLB viewer | `/glb_model_rotation.html` | Load and interact with a GLB model; rotate via UI control |
| Geolocation AR | `/geolocation.html` | Reveal 3D shapes when the device is within range of configured GPS coordinates |
| 360° gallery | `/360_image_gal.html` | Immersive panorama viewer with clickable hotspots to switch scenes |
| 2D shapes | `/2D_shapes.html` | Animated planes, circles, rings, and triangles in a simple 3D scene |
| Hover & click | `/hover_click.html` | Custom A-Frame components for hover highlighting and click-to-scale |

## Prerequisites

- [Node.js](https://nodejs.org/) 18 or later (LTS recommended)
- npm (included with Node.js)
- A modern browser with WebGL support
- **AR demos:** device webcam and permission to use the camera
- **Geolocation demo:** HTTPS or `localhost`, plus location permission
- **Mobile:** recommended for marker and image-target AR for best tracking performance

## Getting Started

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/euph0x1/arvr.git
cd arvr
npm install
```

### Run the server

rename the file that has to be executed to 'index.html' and then run from the root folder:
```bash
node server.js
```


The server listens on port **3000** and serves files from `public/`. Open [http://localhost:3000](http://localhost:3000) and navigate to any demo listed above (for example, [http://localhost:3000/index.html](http://localhost:3000/index.html)).

## Project Structure

```
arvr/
├── server.js              # Express static file server
├── package.json
├── public/                # Web demos and assets
│   ├── index.html         # AR.js marker demo
│   ├── midar.html         # MindAR image target demo
│   ├── glb_target_img.html
│   ├── glb_model_rotation.html
│   ├── geolocation.html
│   ├── 360_image_gal.html
│   ├── 2D_shapes.html
│   ├── hover_click.html
│   ├── aframe.min.js
│   ├── aframe-ar.js       # AR.js for A-Frame
│   ├── mindar-image-aframe.prod.js
│   ├── pattern-letterA.patt
│   ├── targets.mind       # MindAR compiled targets
│   ├── images/            # 360° panorama textures
│   └── model/             # GLB 3D models
└── outputs/               # Screenshots of demo results
```

## AR Setup Notes

### Marker-based AR (AR.js)

1. Print or display `public/pattern-letterA.png` as the tracking image.
2. Open `/index.html` on a device with a camera.
3. Point the camera at the marker; 3D content appears on top of it.

### Image-target AR (MindAR)

1. Use `public/mindar_img_target.jpg` (or your own image compiled to `targets.mind`) as the physical target.
2. Open `/midar.html` or `/glb_target_img.html`.
3. Allow camera access and align the target in view.

### Geolocation demo

Coordinates in `geolocation.html` are configured for a specific area. Update the `locations` array with latitude, longitude, and threshold values for your use case before testing outdoors.

## Technology Stack

- **[Express](https://expressjs.com/)** — static asset hosting
- **[A-Frame](https://aframe.io/)** — WebXR and 3D scene markup
- **[AR.js](https://ar-js-org.github.io/AR.js/)** — marker-based augmented reality
- **[MindAR](https://hiukim.github.io/mind-ar-js-doc/)** — image-target tracking for the web

## Browser Compatibility

| Capability | Chrome | Firefox | Safari | Edge |
|------------|--------|---------|--------|------|
| A-Frame scenes | Yes | Yes | Yes* | Yes |
| Webcam AR | Yes | Yes | Yes (iOS 11.3+) | Yes |
| Geolocation | Yes | Yes | Yes | Yes |

\* Safari may require user gestures for camera and motion permissions.

## Troubleshooting

- **Camera not working:** Ensure you are on `localhost` or HTTPS; most browsers block camera access on plain HTTP except for localhost.
- **Marker not detected:** Improve lighting, reduce glare, and keep the marker flat and fully in frame.
- **MindAR target not found:** Confirm `targets.mind` matches the printed/displayed image used during target compilation.
- **Geolocation shapes hidden:** Grant location permission and verify coordinates are within the configured thresholds.

## License

ISC — see [package.json](package.json) for details.

## Repository

[https://github.com/euph0x1/arvr](https://github.com/euph0x1/arvr)
