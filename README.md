# handtracker-neon-aesthetic
# ⬡ Cyberpunk Hand Tracker

<div align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![MediaPipe](https://img.shields.io/badge/MediaPipe-0097A7?style=for-the-badge&logo=google&logoColor=white)
![OpenCV](https://img.shields.io/badge/OpenCV-27338e?style=for-the-badge&logo=OpenCV&logoColor=white)

**Real-time hand tracking with a neon cyberpunk aesthetic — runs entirely in your browser.**

</div>

---

## ✨ Features

- 🖐 **Real-time hand tracking** — detects up to 2 hands simultaneously using MediaPipe Hands
- 🌐 **Pure browser-based** — no Python, no installs, just open and run
- 🖤 **Black canvas background** — original camera feed is never shown
- 💠 **Neon cyan skeleton** — glowing hand skeleton with two-pass glow effect
- 🩷 **Pinch detection** — skeleton switches to electric pink when thumb & index finger touch
- 📏 **Two-hand distance** — gold dashed line + live pixel distance between both palms
- 📊 **Live FPS counter** — real-time performance display
- 📺 **Scanline overlay** — subtle CRT scanline effect for extra cyberpunk feel

---

## 🎨 Visual Style

| Element | Color |
|---|---|
| Normal skeleton | Neon Cyan `#00ffff` |
| Pinch state | Electric Pink `#ff1493` |
| Palm distance line | Gold `#ffd700` |
| Background | Pure Black `#000000` |
| Core line | White `#ffffff` |

---

## 🚀 Quick Start

### Option A — Browser (Recommended, zero setup)

1. Download or clone this repository
2. Open the folder in **VS Code**
3. Install the **Live Server** extension (`Ctrl+Shift+X` → search "Live Server")
4. Right-click `cyberpunk_hand_tracker.html` → **Open with Live Server**
5. Allow camera permission in the browser
6. Done — point your hand at the webcam 🤙

> ⚠️ Must use Live Server (or any local server). Opening the file directly via `file:///` will block webcam access due to browser security.

---

### Option B — Python version

**Requirements**

```bash
pip install opencv-python mediapipe numpy
```

**Run**

```bash
python cyberpunk_hand_tracker.py
```

Press `Q` or `ESC` to quit.

---

## 📁 Project Structure

```
cyberpunk-hand-tracker/
│
├── cyberpunk_hand_tracker.html   # Browser version (single file, no dependencies)
├── cyberpunk_hand_tracker.py     # Python version (OpenCV + MediaPipe)
└── README.md
```

---

## 🛠️ How It Works

### Hand Detection
MediaPipe Hands detects 21 landmarks per hand in real time. Each landmark is a normalised (x, y) coordinate that gets mapped to the canvas pixel dimensions.

### Neon Glow Effect
Each skeleton line is drawn in two passes:
1. **Glow pass** — thick coloured line with `shadowBlur` spread
2. **Core pass** — thin white line on top for the bright centre

### Pinch Detection
Euclidean distance between landmark `4` (thumb tip) and landmark `8` (index tip). If distance < 40px, pinch is active and the colour switches to pink.

### Two-Hand Distance
Palm centre is calculated as the mean (x, y) of all 21 landmarks per hand. A gold dashed line connects both centres with the distance shown in pixels.

---

## ⚙️ Configuration

You can tweak these constants at the top of the JS script in the HTML file:

| Constant | Default | Description |
|---|---|---|
| `PINCH_THRESH` | `40` | Pinch sensitivity in pixels |
| `maxNumHands` | `2` | Max number of hands to track |
| `minDetectionConfidence` | `0.7` | Detection threshold (0–1) |
| `minTrackingConfidence` | `0.6` | Tracking threshold (0–1) |
| `shadowBlur` | `18` | Glow spread intensity |

---

## 🧰 Tech Stack

| Technology | Purpose |
|---|---|
| [MediaPipe Hands](https://google.github.io/mediapipe/solutions/hands) | Hand landmark detection |
| HTML5 Canvas API | Drawing the neon skeleton |
| `getUserMedia()` | Webcam access |
| MediaPipe Camera Utils | Frame feeding loop |

---

## 🐛 Troubleshooting

| Problem | Fix |
|---|---|
| **"Device in use"** error | Close Zoom, Teams, Discord, or other camera apps and refresh |
| **Blank black screen** | Wait 5–10 seconds for the model to load |
| Loading screen stuck | Check your internet connection (CDN scripts need to download) |
| No hands detected | Ensure good lighting and keep your full hand in frame |
| Very low FPS | Close other browser tabs; reduce resolution in the `getUserMedia` options |
| Camera permission denied | Go to browser settings → Site permissions → Camera → Allow |

---

## 📜 License

MIT License — free to use, modify, and distribute.

---

<div align="center">
Built with 💠 and neon lights
</div>
