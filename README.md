# Park Physics Environment — Unity Project

## 3D Park with Physics (Rigidbody, Collider, Physics Material)

A complete 3D park environment in Unity demonstrating basic physics using
Rigidbody, Collider, and Physics Material components.

---

## 📋 Quick Start — How to Set Up

### Step 1: Open the Project in Unity

1. Open **Unity Hub**
2. Click **Open** (or **Add project from disk**)
3. Browse to this folder: `ParkPhysicsProject`
4. Select it and click **Open**
5. Unity will import the project (this may take 1–2 minutes the first time)

> **Unity Version:** This project is compatible with **Unity 2021.3 LTS** and newer.
> If prompted to upgrade, click **Confirm** to let Unity convert the project.

### Step 2: Generate the Park Scene

Once Unity finishes importing:

1. In the Unity menu bar, click **Park Physics → Create Park Environment**
2. A dialog box will confirm the scene was created
3. The scene is saved to: `Assets/Scenes/ParkPhysicsEnvironment.unity`

### Step 3: Enter Play Mode

1. Press the **Play button (▶)** at the top of the Editor
2. Watch the **red BouncingSphere** fall from above and bounce off the ground
3. The **blue DecorativeSphere** will settle gently onto the ground
4. Press **Play** again to stop

---

## 🏞️ Scene Contents

### Required Objects

| GameObject         | Primitive  | Material        | Physics                              |
|--------------------|-----------|-----------------|--------------------------------------|
| ParkGround         | Plane     | GrassGreen      | MeshCollider (default)              |
| BenchCube_1        | Cube      | WoodBrown       | BoxCollider (default)               |
| BenchCube_2        | Cube      | WoodBrown       | BoxCollider (default)               |
| ParkBlock_3        | Cube      | StoneGray       | BoxCollider (default)               |
| **BouncingSphere** | Sphere    | BouncyRed       | **Rigidbody + SphereCollider + BouncyMaterial** |
| DecorativeSphere   | Sphere    | DecorativeBlue  | Rigidbody + SphereCollider          |
| TreeTrunk          | Cylinder  | BarkBrown       | CapsuleCollider (default)           |

### Decorative Objects

- **Tree_1, Tree_2, Tree_3** — Tree trunks (cylinders) with green foliage crowns (spheres)
- **Pathway** — A flat beige path running through the park
- **StoneDecor_1, StoneDecor_2** — Small stone accent blocks
- **Bench legs** — Small cube legs under each bench

---

## ⚽ Bouncing Sphere — Physics Details

The **BouncingSphere** is the key physics demonstration:

| Component        | Setting                  | Value                       |
|------------------|--------------------------|-----------------------------|
| **Rigidbody**    | Mass                     | 1                           |
|                  | Use Gravity              | ✅ Enabled                  |
|                  | Drag                     | 0                           |
|                  | Angular Drag             | 0.05                        |
|                  | Collision Detection      | Continuous                  |
|                  | Interpolate              | Interpolate                 |
| **SphereCollider** | Radius                 | 0.5 (default)               |
|                  | **Physics Material**     | **BouncyMaterial**          |
| **BouncyMaterial** | Bounciness             | **0.8**                     |
|                  | Dynamic Friction         | 0.4                         |
|                  | Static Friction          | 0.4                         |
|                  | Bounce Combine           | **Maximum**                 |
|                  | Friction Combine         | Average                     |

**How it works:**
- The sphere starts 8 units above the ground
- Gravity pulls it down (Rigidbody with `Use Gravity = true`)
- It hits the ParkGround's MeshCollider
- The BouncyMaterial (Bounciness = 0.8, Bounce Combine = Maximum) causes it to bounce back up
- Each bounce is slightly lower than the previous one due to energy loss
- This is **real Unity physics** — not a scripted animation

---

## 🔍 How to Inspect Components

### Inspect the BouncingSphere:
1. In the **Hierarchy** panel (left side), click on **BouncingSphere**
2. In the **Inspector** panel (right side), you will see:
   - **Transform** — Position, Rotation, Scale
   - **Sphere (Mesh Filter)** — The sphere mesh
   - **Mesh Renderer** — BouncyRed material
   - **Sphere Collider** — With BouncyMaterial assigned
   - **Rigidbody** — Mass, gravity, and collision settings

### Inspect the BouncyMaterial:
1. In the **Project** panel, navigate to `Assets/PhysicsMaterials/`
2. Click on **BouncyMaterial**
3. The Inspector shows Bounciness = 0.8, Bounce Combine = Maximum

---

## ✅ Verification

Use the built-in verification tool:

1. In the Unity menu bar, click **Park Physics → Verify Scene Requirements**
2. A checklist will appear in the **Console** window
3. All items should show ✅

### Manual Checklist:
- [x] 1 Plane (ParkGround)
- [x] 3+ Cubes (BenchCube_1, BenchCube_2, ParkBlock_3)
- [x] 2 Spheres (BouncingSphere, DecorativeSphere)
- [x] 1+ Cylinder (TreeTrunk)
- [x] 2+ Rigidbody components
- [x] Appropriate Colliders on all objects
- [x] Ground prevents objects from falling through
- [x] BouncingSphere visibly bounces (real physics)
- [x] BouncyMaterial assigned with Bounciness = 0.8
- [x] Camera shows clear park view
- [x] Meaningful hierarchy names
- [x] Scene saved as ParkPhysicsEnvironment

---

## 📁 Project Structure

```
ParkPhysicsProject/
├── Assets/
│   ├── Editor/
│   │   └── ParkSceneCreator.cs      ← Editor script (scene generator)
│   ├── Materials/                    ← Created by the script
│   │   ├── GrassGreen.mat
│   │   ├── WoodBrown.mat
│   │   ├── StoneGray.mat
│   │   ├── BouncyRed.mat
│   │   ├── DecorativeBlue.mat
│   │   ├── BarkBrown.mat
│   │   ├── LeafGreen.mat
│   │   └── PathBeige.mat
│   ├── PhysicsMaterials/             ← Created by the script
│   │   └── BouncyMaterial.asset
│   └── Scenes/
│       └── ParkPhysicsEnvironment.unity  ← The main scene
├── Packages/
│   └── manifest.json
└── README.md                         ← This file
```

---

## 📸 Screenshots to Capture for Submission

1. **Park Overview:** The Scene or Game view showing the full park layout
2. **BouncingSphere Rigidbody:** Select BouncingSphere → screenshot the Inspector showing Rigidbody settings
3. **BouncingSphere Collider + Physics Material:** Scroll down in the Inspector → screenshot the SphereCollider with BouncyMaterial
4. **Play Mode Bounce:** Enter Play mode → capture the sphere mid-bounce

---

## 🎥 Demonstration Steps

1. Open the scene `ParkPhysicsEnvironment` from `Assets/Scenes/`
2. Press **Play (▶)**
3. Observe the red sphere falling from height and bouncing repeatedly
4. Select **BouncingSphere** in the Hierarchy while in Play mode to see Rigidbody values update in real-time
5. Press **Play** again to stop
6. Show the Inspector for BouncingSphere to demonstrate the component setup

---

## ⚠️ Troubleshooting

| Issue | Solution |
|-------|----------|
| Sphere falls through the ground | Ensure ParkGround has a MeshCollider. Re-run the scene creator. |
| Sphere doesn't bounce | Check that BouncyMaterial is assigned to the SphereCollider (not the Rigidbody). Bounciness should be 0.8. |
| Scene is empty | Go to **Park Physics → Create Park Environment** in the menu bar. |
| Pink/magenta materials | The project may be using URP. The script has a fallback, but you may need to convert materials via **Edit → Rendering → Materials → Convert**. |
| Script errors in Console | Ensure you're using Unity 2021.3+ with the Built-in Render Pipeline. |
