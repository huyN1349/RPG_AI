Tech Stack for Heroes of the Rift (Base Game)
Guiding Principles
Simplicity: Use widely understood, minimal-dependency technologies.

Robustness: Leverage stable, performant tools with strong community support.

Mobile Focus: Prioritize lightweight, browser-compatible solutions.

1. Frontend Framework
Choice: Vanilla JavaScript + HTML5 + CSS3
Why Simple: No external frameworks (e.g., React, Vue) means no build tools or complex setup—just plain JS, HTML, and CSS files.

Why Robust: Native browser APIs are universally supported, fast, and require no additional overhead. HTML5 provides canvas/WebGL for graphics, and CSS3 handles responsive design.

Use Case: 
HTML5 for structure (e.g., battlefield grid, UI sections).

CSS3 for vertical layout and mobile responsiveness (flexbox, media queries).

Vanilla JS for game logic (combat, hero recruitment).

2. Graphics and Rendering
Choice: HTML5 Canvas (2D Context)
Why Simple: Built into browsers, no external libraries needed. Basic 2D drawing is straightforward for grids, sprites, and text.

Why Robust: Canvas is performant for 2D games, widely supported, and lightweight for mobile. Scales easily to pixel art style.

Use Case: 
Draw the 3x5 battlefield grid.

Render hero names/health and enemy positions.

Simple animations (e.g., attack effects) via frame updates.

3. Styling
Choice: Pure CSS (No Preprocessors)
Why Simple: No need for Sass/Less setup or compilation—just write CSS directly in a single file.

Why Robust: CSS3 is mature, with flexbox and grid for vertical layouts, and media queries for mobile optimization. No runtime dependencies.

Use Case: 
Stack UI sections vertically (Enemy Area, Battlefield, Player Area).

Style buttons and grid cells with borders, colors, and tap-friendly sizes.

4. Data Persistence
Choice: Browser LocalStorage
Why Simple: Built-in browser API, no server or database setup required. Just key-value pairs stored as strings.

Why Robust: Reliable for small-scale data (heroes, gold), persists across refreshes, and works offline. Sufficient for base game needs.

Use Case: 
Save player’s hero array and Gold after recruitment or victory.

Load data on page start.

5. Development Tools
Choice: Visual Studio Code + Live Server Extension
Why Simple: VS Code is free, lightweight, and easy to install. Live Server provides instant browser previews with auto-reload.

Why Robust: VS Code has excellent JS/CSS/HTML support (syntax highlighting, debugging). Live Server mimics a web server for testing.

Use Case: 
Edit index.html, main.js, and style.css.

Test game in real-time on a mobile browser via localhost.

6. Deployment
Choice: GitHub Pages
Why Simple: Free hosting directly from a GitHub repo—just push files (index.html, main.js, style.css) and enable Pages.

Why Robust: Stable, globally accessible, and supports HTTPS. Ideal for a webgame with no backend.

Use Case: 
Deploy the game for public testing.

Access via mobile browser for vertical play.

