# RayMobile: Swift Metal Path Tracer

This project involves creating a **basic path tracer** for iOS using **Swift** and **Metal**, designed to generate visually stunning ray-traced images while making use of mobile device capabilities such as the gyroscope and touch interactions.

## Roadmap

### 1. Setup Metal Project and Render Triangle

- Set up a Metal-based project.
- Create a basic vertex and fragment shader to render a triangle on screen.

#### Tools:
- **Xcode**, **Metal Shading Language (MSL)**, **MTLRenderPipelineDescriptor**

### 2. Basic Ray Generation and Surface Rendering

- Create a **fragment shader** that calculates a ray direction from each pixel.
- Intersect rays with a sphere using an analytical solution for **ray-sphere intersection**.

### 3. Basic Lighting (Ambient + Diffuse Shading)

   - **Ambient lighting:** A constant base light to simulate global illumination.
   - **Diffuse shading:** Based on the Lambertian reflectance model, simulating light scattered in all directions from a surface.

### 4. Material Types

Implement materials, i.e. the way surfaces interact with light:
- **Lambertian (Diffuse):** This type scatters light equally in all directions.
- **Specular (Mirror-like Reflection):** This reflects light in a specific direction, simulating a mirror-like surface (the basic concept of reflection, limited to single-bounce reflections).
- **Glass (Refractive):** This bends light as it passes through, simulating transparency and refraction.

### 5. Reflection and Recursion

Extend the reflection model to handle multiple bounces (recursive reflections):
- **Recursive Reflection:** Tracing rays that reflect off surfaces and tracing additional rays from the reflection points. This creates more realistic reflections where objects can reflect other objects multiple times.
- **Performance Control:** Implementing a recursion depth limit to balance performance and visual fidelity.

### 6. Soft Shadows

- Implement **soft shadows** by sampling multiple points on a light source.

### 7. Performance Optimizations

- Basic acceleration structure (grid-based or BVH).
- Implement **anti-aliasing** (super-sampling).

*Optimization Techniques:*
- **Bounding Volume Hierarchies (BVH)**: Reduces the number of ray-object intersection tests.
- **Super-sampling Anti-Aliasing (SSAA)**: Reduces jagged edges by averaging multiple samples per pixel.

### 8. Gyroscope-Controlled Camera Movement

- Use **Core Motion** to access gyroscope data.
- Map device orientation changes to control the camera’s position and rotation.
- The sphere should appear stationary while the environment moves with device tilt.
- Add a toggle for disabling gyroscope control.

#### Tools:
- **Core Motion Framework**

### 9. Touch-Based Interaction (Focus Point Selection)

- Implement **touch interaction** where tapping sends a ray towards the scene.
- Highlight the object hit by the ray (like a light pulse effect).
- Allow **moving the light source** by dragging on the screen.

#### Tools:
- **UIGestureRecognizer**, **MTKView Touch Handling**

### 10. Dynamic Scene Editing (Add/Remove Objects)

- Add tap gestures for **creating spheres or cubes**.
- Implement pinch gestures for **scaling objects**.
- Allow double-tap to **delete objects**.

This can be stored in a dynamic array for objects and passed to the shader.

#### Tools:
- **SwiftUI Data Binding**, **MTLBuffer Management**

### Step 11: Real-Time Adjustments (Sliders for Parameters)

Add **SwiftUI sliders** for dynamic control over:
   - Light intensity
   - Reflection depth (recursion limit)
   - Material roughness
   - Number of rays per pixel (anti-aliasing control)

These values should be passed as uniforms to the shader for real-time changes.

#### Tools:
- **SwiftUI**, **Shader Uniforms**

### 12. Progressive Rendering (Performance Optimization)

- Implement **progressive rendering technique** where the image converges over multiple frames.
- Each frame accumulates samples to reduce noise, ideal for a mobile device’s limited GPU power.

#### Tools:
- **Temporal Accumulation**, **Denoising Techniques**

### 13. Adaptive Resolution for Mobile Performance

- Implement **dynamic resolution scaling** to reduce resolution during motion.
- Restore full resolution when stationary.

#### Tools:
- **MTKView Drawable Size Adjustments**

### 14. Recording and Sharing the Render

- Add a **screenshot** or **video recording** feature so users can capture and share the rendered results.

#### Tools:
- **ReplayKit**

### 15. AR Mode

- Convert the app into an **AR-based path tracer** where the rendered sphere or objects can be placed in real-world space.
- Leverage **ARKit** to anchor objects based on real-world surfaces and light estimation.

#### Tools:
- **ARKit**, **Scene Reconstruction**, **ARAnchors**
