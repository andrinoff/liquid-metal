# Liquid Metal - Interactive WebGL Molten Surface

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Three.js](https://img.shields.io/badge/Three.js-000000?style=for-the-badge&logo=three.js&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![GLSL](https://img.shields.io/badge/GLSL-000000?style=for-the-badge&logo=opengl&logoColor=white)

A stunning and interactive liquid metal simulation created with `three.js` and custom GLSL shaders. This project, titled "Chromaflux," renders a dynamic, reflective surface that ripples and distorts in response to mouse movement, mimicking the appearance of molten metal.

## ✨ Features

-   **Dynamic Ripples:** The surface reacts to your mouse pointer, creating beautiful, spreading ripples.
-   **Realistic Reflections:** Uses a `CubeCamera` to generate real-time reflections of a dynamic skybox, giving the surface a metallic, reflective quality.
-   **Simplex Noise:** Implements simplex noise in the vertex shader to create a constant, gentle, and natural-looking wave motion.
-   **GLSL Shaders:** Custom vertex and fragment shaders are used to control the geometry and appearance of the liquid.
-   **Fresnel Effect:** The fragment shader includes a Fresnel effect for more realistic reflections at grazing angles.
-   **Responsive Design:** The WebGL canvas resizes to fit the browser window.

## 🚀 Live Demo

[**Click here to disturb the liquid metal!**](https://raw.githack.com/andrinoff/liquid-metal/main/index.html)

*(Link points to a raw version of the project's index.html for direct viewing)*

## 🛠️ Technologies Used

-   **Core:** `JavaScript`
-   **3D Rendering:** `three.js` (r128)
-   **Shading Language:** `GLSL` (for custom shaders)
-   **Markup:** `HTML5`
-   **Styling:** `Tailwind CSS` for the information overlay.

## ⚙️ How It Works

1.  **Setup:** A `three.js` scene is initialized with a `PerspectiveCamera` and a `WebGLRenderer`.
2.  **Skybox:** A simple gradient skybox is created using a custom shader, which serves as the environment for reflections.
3.  **Reflection:** A `CubeCamera` is added to the scene. In each frame, it renders the skybox from the plane's position into a `WebGLCubeRenderTarget`. This render target is then used as an environment map.
4.  **The Liquid Plane:** A `PlaneGeometry` is created with a high number of segments for smooth deformation. Its material is a `ShaderMaterial` containing custom GLSL code.
    -   **Vertex Shader:** This shader displaces the plane's vertices based on a combination of simplex noise (for ambient waves) and a radial sine wave originating from the mouse's position (for interactive ripples). It also calculates the vertex normals to pass to the fragment shader.
    -   **Fragment Shader:** This shader calculates the final color of each pixel. It uses the `reflect` function with the view direction and the vertex normal to get a reflection vector, which is then used to sample the environment map (`t_envMap`). A Fresnel effect is applied to make the reflections more convincing.
5.  **Interaction:** A `Raycaster` is used to detect the intersection point of the mouse and the plane, updating a `u_mouse` uniform with the coordinates. The `u_intensity` uniform is smoothly animated to create a fluid response when the mouse enters or leaves the canvas.

## ▶️ Usage

No installation or build process is required. Simply open the `index.html` file in a modern web browser that supports WebGL.

```bash
# Clone the repository (optional)
git clone [https://github.com/your-username/liquid-metal.git](https://github.com/your-username/liquid-metal.git)

# Navigate to the directory
cd liquid-metal

# Open index.html in your browser
```

---

*This project was created by andrinoff and serves as a beautiful demonstration of WebGL's capabilities.*
