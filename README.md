# MG-Anitron 🎬

**MG-Anitron** is a lightweight, browser-based animation and composition engine designed for overlaying sprites and elements onto video frame sequences. 

Unlike traditional editors that simply draw pixels, MG-Anitron operates as a **state-machine simulation**. It decouples the timeline (the instructions) from the stage (the current state), allowing for high-precision control over instances, layering, and timing.

## 🚀 Core Concepts

### 1. The Timeline (The Authority)
The project is driven by a JSON-based timeline. Every action—whether it's a sprite entering the screen, moving to a new coordinate, or leaving the scene—is an **Event**. 
- **Chronological Processing**: The engine replays events from time `0` to the current playhead to determine exactly what should be on screen.
- **JSON-Driven**: Every event is a JSON object, making the project easily scriptable or integrable with other tools.

### 2. The Stage (The Simulation)
The Stage is the "Single Source of Truth" for the current frame. 
- **Instance Model**: The system distinguishes between a **Sprite** (the library DNA/image) and an **Instance** (the specific object on the stage). This allows you to have multiple copies of the same sprite, each with its own position, scale, and Z-index.
- **Z-Order Rendering**: Elements are rendered based on a Z-index, ensuring backgrounds stay back and overlays stay front.

### 3. The Pipeline
`Timeline Events` →\rightarrow→ `Stage State` →\rightarrow→ `Canvas Render`

---

## ✨ Features

- 📂 **Project Folder Loading**: Load an entire directory of video frames and assets via the File System Access API.
- 🎨 **Sprite Library**: Manage anchor points and assets for your characters and elements.
- 🏗️ **Instance Management**: A dedicated "Stage" tab to toggle visibility and edit active instances in real-time.
- ✏️ **Live JSON Editing**: Modify event parameters (X, Y, Z, Scale) on the fly with an integrated JSON editor.
- 🎞️ **Frame-Accurate Navigation**: Precise control over current frames and timeline FPS.
- 💾 **Project Persistence**: Save and load your entire composition (timeline, sprite anchors, and metadata) as `.ant` files.

## 🛠️ Technical Stack

- **Language**: Vanilla JavaScript (ES6+)
- **Rendering**: HTML5 Canvas API
- **Data Format**: JSON
- **Styling**: CSS3

## 🚦 Getting Started

1. Clone this repository.
2. Open `index.html` in a modern web browser (Chrome or Edge recommended for File System API support).
3. Select your project folder containing your video frames (e.g., `video/prod0001.png`) and assets.
4. Start animating!

## 🗺️ Roadmap

- [ ] **Interpolation/Tweening**: Smooth transitions between move events.
- [ ] **Advanced Sprite Types**: Support for SVG sequences and Spritesheets.
- [ ] **Collision Detection**: Trigger events based on instance overlaps.
- [ ] **Audio Integration**: Couple sound effects to timeline events.

## ☕ Support

If this tool helped you with your project or saved you hours of manual work, feel free to buy me a coffee! 

[Still setting up Ko-Fi for support payments](https://ko-fi.com/)

---
*Developed via Synthetic Pair Programming.*
