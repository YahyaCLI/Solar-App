### Solar App Summary
 An interactive 3D Solar Syestem made using Three.Js and vite along with HTML and CSS that I created for the 2024 NASA Space Challenge.
 
 The goal was to build and use Nasa's NEO(Near earth objects) Data that vizualizes and shows the trajectory of these objects and help understand and distinguish between PHA's and neutral objects my analyzing the orbital    path 

---

# PHA Trajectory Visualizer - 3D Space Orrery

An interactive **3D visualization of Potentially Hazardous Asteroids (PHAs)** built with **Three.js** and **Vite**, originally developed for the **NASA Space Apps Challenge**.

This project focuses on **making asteroid orbital classes interpretable in 3D space**, translating abstract orbital parameters into an intuitive visual system.

<img width="1231" height="878" alt="image" src="https://github.com/user-attachments/assets/1de2ed2b-ce2c-4231-9ad4-cdae2cb7d192" />


---

## Purpose

Near-Earth Objects are typically described through orbital parameters like **semi-major axis (a)**, **perihelion (q)**, and **aphelion (Q)**—but these are not immediately intuitive.

This project turns those parameters into a **visual language**:

* Which asteroids **cross Earth’s orbit**
* Which remain **outside or inside Earth’s path**
* How orbital shape and scale relate to **risk classification**

Rather than exact physical simulation, the goal is **conceptual clarity + spatial intuition** and to distinguish between neutral NEO's and PHA's.

---

## PHA Classification (Visualized)

The system encodes the four primary NEA groups:

* **Amor** > Exterior to Earth’s orbit (Mars-crossing)
* **Apollo** > Earth-crossing, larger orbits
* **Aten** > Earth-crossing, smaller orbits
* **Atira** > Fully interior to Earth’s orbit

Each class is represented using **distinct elliptical trajectories**, positioned relative to Earth’s orbit to reflect their defining constraints:

<img width="1213" height="651" alt="image" src="https://github.com/user-attachments/assets/537eaf41-cc83-4e5e-9fda-bce3d44aba79" />
img source: Nasa cneos


These inequalities directly inform how each orbit is **placed and scaled in the scene**.

---

## 📐 Mathematical Backbone

### 1. Circular Motion Approximation (Planets)

Planetary motion is modeled parametrically:

x(t) = r cos(ωt) , z(t) = r sin(ωt)

* ( r ): orbital radius
* ( ω ): angular velocity

This provides stable, real-time motion while keeping rendering lightweight.

---

### 2. Elliptical Orbit Construction (Asteroids & Comet)

Ellipses are defined by:

x = a cos(θ), z = b sin(θ)

To approximate realistic solar orbits, the ellipse is **offset toward a focus**:

c = √(a^2 - b^2)

x' = a cos(θ) - c


This ensures the Sun is positioned closer to a **focal point rather than the center**, mimicking Keplerian structure.

---

### 3. Parametric Curves in 3D Space

Custom curves (e.g., for comet trajectories) are implemented using:

* Continuous parameter ( t ∈ [0,1] )
* Mapping ( θ = 2πt )
* Sampling via `THREE.Curve`

This allows smooth orbital paths without precomputed datasets.

---

## Implementation Highlights

* **Three.js Scene Graph** for hierarchical object management
* **OrbitControls** for interactive navigation with damping
* **Procedural star field** (around 2000'ish objects) for spatial depth (And because I have a potato PC sigh...)
* **Multiple animation loops** for independent orbital systems
* **Light-source embedding** inside the Sun for consistent illumination

---

## Modeling Note/Notice

This is a **visual and sort educational model**, not a high precision orbital simulator so dont be expected to be flattered it was designed to solve the problem asked and it did.

* Orbital speeds are scaled for clarity, not accuracy
* Elliptical paths are **geometric approximations**, not numerically integrated trajectories
* No perturbations, inclinations, or n-body interactions are modeled

The emphasis is on **interpreting orbital classes**, not reproducing exact ephemerides.

---

## Running the Project

```bash id="run123"
cd solar-app
npm install
npm run dev
```

---

## Why This Project Works

* Translates **orbital inequalities → spatial intuition**
* Uses **mathematics as a design tool**, not just computation
* Demonstrates strong control over **real-time 3D systems**
* Keeps a clean boundary between **data representation vs simulation**

---

## Extensions

* Mapping real NEO datasets into this framework
* Adding elliptical path
* Time scaling + epoch-based positioning
* Scalable to add additional NEO's

I tried :)

