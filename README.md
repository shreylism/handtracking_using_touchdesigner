# NewProject — Hand-Tracked Audio & Visual Controller

A TouchDesigner project that uses real-time hand tracking via MediaPipe to control audio, video playback, and on-screen text through hand gestures — no controllers, no keyboard required.

---

## Overview

This project uses the [MediaPipe TouchDesigner Plugin](https://github.com/torinmb/mediapipe-touchdesigner) to capture hand landmark data from a webcam and map it to audio parameters, video controls, and dynamic text — making it suitable for live performance and interactive installations.

---

## Requirements

| Requirement | Details |
|---|---|
| [TouchDesigner](https://derivative.ca/) | 2023.11340 or later |
| [MediaPipe TouchDesigner Plugin](https://github.com/torinmb/mediapipe-touchdesigner) | v0.5.2 or later |
| Webcam | 720p or higher recommended |
| OS | Windows 10/11 or macOS 12+ |

---

## Setup

### 1. Install the MediaPipe Plugin

Download the latest `release.zip` from the [MediaPipe TouchDesigner releases page](https://github.com/torinmb/mediapipe-touchdesigner/releases).

> **Important:** When dragging the MediaPipe component into a new project, make sure to select **"Enable External .tox"** — otherwise your `.toe` file size will be very large.

### 2. Clone this repository

```bash
git clone https://github.com/shreylism/NewProject.git
cd NewProject
```

### 3. Add your own assets

This project does not include audio or video files. You will need to provide your own and place them in the correct folders:

```
assets/audio/    ← your .mp3 file
assets/video/    ← your .mp4 file
```

Once placed, open the project in TouchDesigner and re-link the files:
- Click the `audiofilein` CHOP node and set the **File** parameter to `assets/audio/your-file.mp3`
- Click the `moviefilein` TOP node and set the **File** parameter to `assets/video/your-file.mp4`

### 4. Open the project

Open `NewProject.toe` in TouchDesigner. Allow webcam access when prompted.

### 5. Configure MediaPipe

Inside the MediaPipe component, select your webcam from the dropdown and enable the **Hand Tracking** model. Other models can be turned off to improve performance.

### 6. Run

Press **F5** or click Play in TouchDesigner. Position your hands in front of the camera and start gesturing.

---

## Gesture Controls

This project requires both hands simultaneously, each hand controlling a different aspect of the experience.

| Hand | Gesture | Action |
|---|---|---|
| Scale hand | Pinch fingers together | Zooms in and creates a text pattern |
| Scale hand | Open/spread fingers | Zooms out and creates a text pattern |
| Audio hand | Rotate index finger and thumb until horizontal (180 degrees) | Switches to next video and creates a text pattern |
| Audio hand | Pinch (index + thumb) | Lower volume |
| Audio hand | Open (index + thumb apart) | Raise volume |

---

## Project Structure

```
NewProject/
├── NewProject.toe        # Main TouchDesigner project file
├── .gitignore            # Excludes backups and auto-generated files
└── README.md             # This file
```

> **Note:** Audio and video assets are not included. Bring your own `.mp3` and `.mp4` files and re-link them inside the project. The MediaPipe plugin (`toxes/`) is also not included — download it separately from the [MediaPipe TouchDesigner releases page](https://github.com/torinmb/mediapipe-touchdesigner/releases).

---

## Performance Tips

- **Turn off unused MediaPipe models** — each active model adds CPU/GPU load. Only enable Hand Tracking if that is all you need.
- **Lighting matters** — ensure your hands are well-lit for accurate tracking.
- **Resolution** — the MediaPipe plugin is currently limited to 720p webcam input.
- **Hyperthreading (Windows)** — disabling Intel HyperThreading or AMD SMT in BIOS can improve TouchDesigner cook times significantly.

---

## License

Copyright (c) 2026 Shreya Raj. All Rights Reserved.

This project and its contents are protected under copyright law. No part of this project may be reproduced, distributed, modified, or used in any form without explicit written permission from the author.

---

## Credits

Created by **Shreya Raj**

Built with [TouchDesigner](https://derivative.ca/) by Derivative and the [MediaPipe TouchDesigner Plugin](https://github.com/torinmb/mediapipe-touchdesigner) by Torin Blankensmith.

---

## Contact

GitHub: [@shreylism](https://github.com/shreylism)
