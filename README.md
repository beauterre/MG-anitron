![Ani-tron Icon](https://raw.githubusercontent.com/beauterre/MG-anitron/main/anitron-icon.png)
# Anitron 🎬

github-page: https://beauterre.github.io/MG-anitron/

github-repo: https://github.com/beauterre/MG-anitron

**Anitron** is a lightweight, browser-based animation and composition engine designed for overlaying sprites and elements onto video frame sequences. 

Unlike traditional editors that simply draw pixels, MG-Anitron operates as a **state-machine simulation**. It decouples the timeline (the instructions) from the stage (the current state), allowing for high-precision control over instances, layering, and timing.

## 🚀 Core Concepts

### 1. The Edit Decision List (The Authority)
The project is driven by a JSON-based **Edit Decision List (EDL)**. Every action, whether it's a sprite entering the screen, moving to a new coordinate, or leaving the scene, is a specific entry in this list.
- **Chronological Processing**: The engine replays the EDL from time `0` to the current playhead to determine exactly what should be on screen.
- **JSON-Driven**: Every EDL entry is a JSON object, making the project easily scriptable or integrable with other professional tools.

### 2. The Stage (The Simulation)
The Stage is the "Single Source of Truth" for the current frame. 
- **Instance Model**: The system distinguishes between a **Sprite** (the library DNA/image) and an **Instance** (the specific object on the stage). This allows you to have multiple copies of the same sprite, each with its own position, scale, and Z-index.
- **Z-Order Rendering**: Elements are rendered based on a Z-index, ensuring backgrounds stay back and overlays stay front.

### 3. The Pipeline
`EDL Instructions` → `Stage State` → `Canvas Render`

### 4. ⏳ The Timeline & Temporal Navigation

The Ani-tron timeline is a high-precision temporal coordinate system. Rather than a linear tape, it operates as a **virtual window into the EDL**, allowing for non-linear navigation and extreme scale.

#### 1. Frame-Relative Logic
The engine treats time as a function of `Frame / FPS`. This ensures that regardless of the playback speed or the target output, the composition remains frame-accurate. By decoupling the playhead from the rendering loop, the engine can "jump" to any point in time and instantly rebuild the stage state.

#### 2. Negative Time & Infinite Horizon
Unlike traditional editors that start at `0`, Ani-tron supports **Negative Time**. This allows users to set up "pre-roll" events—actions that happen before the official start of the sequence—ensuring that elements are already in motion or correctly positioned when the project hits frame zero.

#### 3. Dynamic Zoom & Panning
The timeline viewport is fully elastic. Using a combination of mouse-wheel zooming and click-and-drag panning, the user can shift perspectives:
- **Macro View**: Zoom out to see the entire structure of a multi-minute composition.
- **Micro View**: Zoom in to a fraction of a second to align events with sub-frame precision.
- **Adaptive Markers**: Time markers (seconds, minutes, hours) dynamically scale their intervals based on the zoom level, maintaining readability across all scales.

#### 4. The "Replay" Mechanism
Because the timeline is driven by an Edit Decision List, moving the playhead doesn't just "slide" a frame; it triggers a **State Rebuild**. The engine re-scans the EDL from the beginning of time up to the current playhead, calculating every move, enter, and leave event to determine the exact visual state of the stage at that micro-moment.




### 5. 🧬 Resource Architecture: The SVG Library

To ensure maximum flexibility and interoperability, Ani-tron is evolving toward an **SVG-based Resource Container** model. Instead of relying on loose files or bloated JSON strings, the project utilizes a specialized SVG structure as its primary asset database.

#### Why SVG?
Traditional bitmap-based projects suffer from resolution loss and massive file sizes. By treating the project file as an SVG, Ani-tron achieves:
- **Interoperability**: Project assets can be opened, edited, and refined in professional vector tools like **Inkscape** or **Adobe Illustrator**, then re-imported seamlessly.
- **Resolution Independence**: Core assets are stored as mathematical paths, ensuring the composition remains crystal clear at any scale.
- **Hybrid Storage**: The SVG `<defs>` section acts as a unified library, housing both complex vector paths and embedded Base64 bitmaps in a single, portable file.

#### The "Database" Workflow
1. **The Library**: Every sprite, shape, or "Sausage" curve is stored as a unique ID within the SVG's definition layer.
2. **The Reference**: The **Edit Decision List (EDL)** doesn't store the asset itself, but a reference to the SVG ID.
3. **The Render**: The engine parses these IDs and renders them to the HTML5 Canvas using `Path2D` for vectors and `Image` objects for bitmaps, combining the power of vector precision with the speed of canvas rasterization.

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

1. I''ll make a nice demo.. right now.. you can add a defaultsprite. change its place.

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
