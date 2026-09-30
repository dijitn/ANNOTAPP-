# ANNOTAPP: Master Conceptual Blueprint & RFC

**ANNOTAPP** is a layer-first spatial annotation workstation designed to eliminate the mechanical friction, ocular strain, and visual clutter inherent in legacy 2D vertex-plotting tools.

---

## 1. Executive Summary & Brand Identity

### 1.1 Brand & Architectural Positioning
* **Product Name:** ANNOTAPP (Portmanteau of *Annotation* and *App*).
* **Category Distinction:** Shifts the industry standard away from legacy CAD-style point-plotters toward a specialized spatial workstation built on **Optical Layer Decomposition**.
* **Core Value Proposition:** Eliminates human ocular strain and mechanical clicking friction by non-destructively isolating and suppressing visual noise (glass, glare, reflections) during the labeling process.

### 1.2 Overview Matrix

| Attribute | Specification |
| :--- | :--- |
| **Project Name** | ANNOTAPP |
| **Core Paradigm** | Layer-Based Spatial Annotation & Noise Suppression |
| **Primary Audience** | Computer Vision Engineers, Autonomous Systems Teams, Data Labeling Operations |
| **Data Integrity** | Zero-damage, non-destructive canvas visibility toggling |

---

## 2. Core Paradigm Shift & Problem Definition

### 2.1 The Legacy Problem (2D Polygon Plotting)
1. **Visual Clutter:** Forces human annotators to trace object contours directly over glare, reflections, and translucency.
2. **Mechanical Friction:** Point-by-point manual clicking creates high cognitive fatigue, visual strain, and slow labeling throughput.
3. **Dimensional Flattening:** Treats complex 3D real-world depth as a flat, single-plane 2D vector polygon.

### 2.2 The ANNOTAPP Solution (Optical Layer Decomposition)
1. **Human-Centric Workspace:** Removes glare and reflections from the active workspace to maximize human eye contrast sensitivity and visual comfort.
2. **Non-Destructive Hiding:** Isolates transparent barriers (`Layer_Transparent`), locks spatial metadata, and toggles visibility off without modifying underlying camera pixels.
3. **Native 3D Spatial Hierarchy:** Preserves real-world spatial depth across a structured multi-plane depth stack:
   * **Foreground Plane ($Z_0$):** Objects positioned in front of the barrier ($Z > Z_{\text{glass}}$).
   * **Secured Transparent Plane ($Z_1$):** Glass, film, glare, or reflection metadata plane ($Z_{\text{glass}}$).
   * **Rear / Deep Background Plane ($Z_2$):** Primary targets and distant background environment behind the barrier ($Z < Z_{\text{glass}}$).

---

## 3. Sequential Operational Pipeline (Annotator UI Workflow)

1. **Step 1 — Load Scene & Initialize Canvas**
   * System loads raw RGB source image into standard workspace view.
   * Canvas presents full-RGB image alongside an active Depth Control Panel on the side dock.

2. **Step 2 — Identify & Lock Transparent Layer**
   * Annotator activates the **Transparent Layer Identifier Tool** (or auto-detect trigger).
   * Annotator defines boundaries of the glass, reflection, or translucent plane.
   * Annotator clicks **Secure & Lock Layer** to log spatial metadata to the manifest and create `Layer_Transparent`.

3. **Step 3 — Toggle Visibility & Clear Workspace**
   * Annotator toggles off `Layer_Transparent` visibility icon.
   * Canvas instantaneously suppresses glare, reflections, and optical distortion.
   * Unobstructed, high-contrast visual surface becomes active for precise human labeling.

4. **Step 4 — Annotate Foreground Layer ($Z > Z_{\text{glass}}$)**
   * Annotator selects `Layer_Foreground`.
   * Annotator labels elements physically sitting in front of the barrier (wiper blades, frames, front clutter).
   * System automatically attaches $Z_0$ spatial tags to all shapes drawn on this plane.

5. **Step 5 — Annotate Rear & Background Layers ($Z < Z_{\text{glass}}$)**
   * Annotator switches to `Layer_Rear_Subject` to label targets behind glass (occupants, room interior, displays) on a clear, glare-free surface.
   * Annotator switches to `Layer_Deep_Background` to mark far-field environment context (sky, buildings).
   * System attaches $Z_1$ and $Z_2$ depth tags to respective shapes.

6. **Step 6 — Re-Assemble Stack & Export Manifest**
   * Annotator toggles `Layer_Transparent` back ON to preview complete scene stack alignment.
   * Annotator triggers **Validate Depth Stack**.
   * Annotator selects **Export Dataset**, compiling raw image files, non-destructive vector masks, and multi-plane 3D spatial JSON manifests.

---

## 4. Architectural System Diagram
