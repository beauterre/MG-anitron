![Ani-tron Icon](https://raw.githubusercontent.com/beauterre/MG-anitron/main/anitron-icon.png)
# Anitron 🎬

github-page: https://beauterre.github.io/MG-anitron/

github-repo: https://github.com/beauterre/MG-anitron

**Anitron** is a lightweight, browser-based animation and composition engine designed for overlaying sprites and elements onto video frame sequences. 

Unlike traditional editors that simply draw pixels, MG-Anitron operates as a **state-machine simulation**. It decouples the timeline (the instructions) from the stage (the current state), allowing for high-precision control over instances, layering, and timing.

## 🚀 Core Concepts

### 1. The Edit Decision List (The Authority)
The project is driven by a JSON-based **Edit Decision List (EDL)**. Every action—whether it's a sprite entering the screen, moving to a new coordinate, or leaving the scene—is a specific entry in this list.
- **Chronological Processing**: The engine replays the EDL from time `0` to the current playhead to determine exactly what should be on screen.
- **JSON-Driven**: Every EDL entry is a JSON object, making the project easily scriptable or integrable with other professional tools.

### 2. The Stage (The Simulation)
The Stage is the "Single Source of Truth" for the current frame. 
- **Instance Model**: The system distinguishes between a **Sprite** (the library DNA/image) and an **Instance** (the specific object on the stage). This allows you to have multiple copies of the same sprite, each with its own position, scale, and Z-index.
- **Z-Order Rendering**: Elements are rendered based on a Z-index, ensuring backgrounds stay back and overlays stay front.

### 3. The Pipeline
`EDL Instructions` →\rightarrow→ `Stage State` →\rightarrow→ `Canvas Render`

---

## ✨ Features

- 📂 **Project Folder Loading**: Load an entire directory of video frames and assets via the File System Access API.
- 🎨 **Sprite Library**: Manage anchor points and assets for your characters and elements.
- 🏗️ **Instance Management**: A dedicated "Stage" tab to toggle visibility and edit active instances in real-time.
- ✏️ **Live JSON Editing**: Modify EDL parameters (X, Y, Z, Scale) on the fly with an integrated JSON editor.
- 🎞️ **Frame-Accurate Navigation**: Precise control over current frames and timeline FPS.
- 💾 **Project Persistence**: Save and load your entire composition (EDL, sprite anchors, and metadata) as `.ant` files.

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

## 🔮 Future Development: Primitive Engine

The vision for Anitron is to move beyond external assets and introduce a robust system of **Internal Primitives**, allowing users to create complex visuals directly within the engine:

- **Dynamic Shapes**: Closed-path shapes capable of morphing and featuring customizable partial outlines.
- **Sausage Curves**: A specialized curve-primitive where the "meat" (fill), "skin" (outline), and thickness can be modulated independently per control point, creating organic, variable-width paths.
- **Expanded Asset Support**: Native integration for Video files, Bitmaps, Spritesheets, and SVGs as first-class EDL instances.

## 🗺️ Roadmap

- [ ] **Interpolation/Tweening**: Smooth transitions between EDL entries.
- [ ] **Primitive Support**: Implementation of Shapes and "Sausage" curves.
- [ ] **Multi-Asset Integration**: Native support for SVG sequences, Spritesheets, and Video.
- [ ] **Collision Detection**: Trigger actions based on instance overlaps.
- [ ] **Audio Integration**: Couple sound effects to the EDL timeline.

**☕ Support: Link coming soon!**
I'll use the standard *sponsor* button in github..

---
*Developed via Synthetic Pair Programming.*
