![ReflexJSLogo720](https://github.com/user-attachments/assets/54fb2874-89e5-4c17-8f7d-81af4cbac527)

# Reflex.js

**Turn any DOM element into a stunning glass element.**

Reflex.js is a lightweight JavaScript library that applies a customizable "glassmorphism" effect to your HTML elements, complete with blur, transparency, reflections, and interactive specular highlights.

## Features

*   **Glass Effect:** Applies background blur and transparency.
*   **Customizable:** Control blur intensity, transparency level, border style, border radius, and background color.
*   **Reflection:** Adds a subtle top reflection for a more realistic glass look.
*   **Specular Highlight:** (Non-touch devices only) Creates an interactive highlight that follows the mouse cursor.
*   **Touch Device Optimized:** Provides a slightly different rendering approach for optimal performance and appearance on touch devices (no specular highlight).
*   **Lightweight:** No external dependencies.
*   **Easy to Use:** Simple API for initialization, updates, and removal.

## Installation

1.  Download the `Reflex.js` file from the `js/` directory.
2.  Include it in your HTML file:

    ```html
    <script src="path/to/js/Reflex.js"></script>
    ```

## Usage

1.  **HTML:** Have an element you want to apply the effect to:

    ```html
    <div id="myGlassElement" style="width: 200px; height: 150px; padding: 20px;">
      Some content inside the glass
    </div>
    ```

2.  **JavaScript:** Create a new `Reflex` instance:

    ```javascript
    // Wait for the DOM to be ready
    document.addEventListener('DOMContentLoaded', () => {
      const glassElement = document.getElementById('myGlassElement');

      // Basic usage
      const reflexInstance = new Reflex(glassElement);

      // Usage with options
      const customReflex = new Reflex('#myGlassElement', {
        blur: 15,
        transparency: 0.2,
        borderRadius: 20,
        reflection: true,
        specular: true, // Only effective on non-touch devices
        color: '#e0e0e0' // Set a light grey background tint
      });

      // You can store the instance to update or destroy it later
      // window.myReflex = customReflex;
    });
    ```

## Options

You can customize the effect by passing an options object during initialization or update:

| Option          | Type    | Default             | Description                                                                                                |
| :-------------- | :------ | :------------------ | :--------------------------------------------------------------------------------------------------------- |
| `blur`          | Number  | `10`                | The intensity of the background blur in pixels.                                                            |
| `transparency`  | Number  | `0.1`               | The opacity level of the background color (0.0 to 1.0).                                                    |
| `color`         | String  | `'rgb(255,255,255)'`| The background tint color (accepts hex `#RRGGBB` or `rgb(r, g, b)`).                                       |
| `borderRadius`  | Number  | `10`                | The border radius in pixels. Only applied if `preserveRadius` is `false`.                                  |
| `preserveRadius`| Boolean | `false`             | If `true`, keeps the element's original `border-radius`. If `false`, applies the `borderRadius` option.    |
| `borderWidth`   | Number  | `1`                 | The width of the border in pixels.                                                                         |
| `borderOpacity` | Number  | `0.2`               | The opacity of the white border (0.0 to 1.0).                                                              |
| `reflection`    | Boolean | `true`              | Whether to show the top reflection effect.                                                                 |
| `specular`      | Boolean | `true`              | Whether to enable the mouse-following specular highlight (only works on non-touch devices).                |
| `preserveShape` | Boolean | `true`              | *Currently unused, intended for future shape preservation features.*                                       |

## Methods

### `update(options)`

Updates the existing Reflex instance with new options.

```javascript
const reflexInstance = new Reflex('#myElement');

// Later... change the blur and color
reflexInstance.update({
  blur: 5,
  color: 'rgba(0, 0, 255, 0.15)' // Update color and transparency together
});
```

### `destroy()`

Removes the glass effect, cleans up added styles and event listeners, and restores the element's original basic styles (like border-radius, position, overflow).

```javascript
const reflexInstance = new Reflex('#myElement');

// Later... remove the effect
reflexInstance.destroy();
```

## Licensing and Attribution

Reflex.js is licensed under the **GNU Affero General Public License v3.0**.

**Important:** In accordance with the AGPLv3 license and the author's request, if you use Reflex.js in your project (especially if the source code is accessible to users, e.g., in a web application), you **must provide attribution to the original author, KaliforniaGator**, within your source code or documentation. A simple comment near where Reflex.js is initialized is often sufficient.

Example:

```javascript
// Initialize the glass effect using Reflex.js by KaliforniaGator
const reflex = new Reflex('#myElement');
```
