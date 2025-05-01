
# Snake³
#### Video Demo: https://www.youtube.com/watch?v=xx3iPQll8v0
#### Description:

### **CS50x Final Project: 3D Snake Game in Babylon.js**

For my CS50x final project, I built a modern twist on the retro classic *Snake*. This isn't your typical 2D pixel grid — my version is a **3D third-person Snake game**, fully playable in the browser. It’s made using **Babylon.js**, a powerful WebGL-based 3D engine, which allowed me to create a real-time interactive game that's completely **client-side and web-based**, with no backend involved.

When I started, I had **zero prior experience with Babylon.js**, but with the help of its official documentation, a few YouTube videos, and GitHub Copilot for suggestions, I managed to wrap my head around it pretty quickly. Honestly, knowledge is knowledge — once you understand the fundamentals, the language or tool is just a means to build.

One of the biggest challenges was handling **snake body movement** in a 3D environment. My first prototype used a **frame-based** approach, where every frame the snake segments would update based on the one in front. But this caused major issues when the frame rate dropped — segments would desync or act jittery. I scrapped that and rebuilt the movement using **arrays and distance-based logic**. Now, each segment follows the one ahead of it based on its position, not the frame count, making movement smooth and consistent even under lag or frame drops.

Visually, the game is minimal but stylized. The **apple** is a low-poly 3D model I grabbed from Sketchfab. Rather than loading it again every time the snake eats it, I simply **reuse the same mesh** and **randomize its position** on each respawn. This saves performance and avoids unnecessary memory usage. The snake itself uses **toon shaders** for a cartoony look. I didn’t write these shaders manually — they were generated with the help of ChatGPT and modified to suit the visual style I wanted.

The game starts on a **start screen**, which simply consists of a large image displaying the controls and instructions. There's also a **start button** — all it really does under the hood is change the snake’s speed from `0` to `0.05`, kicking off the gameplay loop.

Sound plays a key role in making the game feel more alive. I added **background music and sound effects** in the right places — like when the apple is eaten or on collision. The audio used is **royalty-free music**, not made by me, but adds the right amount of atmosphere without overwhelming the gameplay.

Collision detection in this project is smartly optimized. For checking if the apple is collected or if the snake hits its own body, I use an **invisible ray** that shoots out in front of the snake's head. This is a far cheaper method than running continuous mesh-to-mesh intersection checks. But when necessary — like for walls — I still rely on **Babylon.js’s mesh intersection system** for accurate detection.

Once the player reaches a **score of 5**, the game gets spicier. Every time the score updates from that point onward, there’s a **25% chance** that a wall (a block of bricks) will spawn in the arena. These walls are of **random sizes and placed randomly**, but within predictable limits to keep things fair. This introduces unpredictability and difficulty without feeling completely chaotic.

Internally, I implemented a smart naming system to simplify collision logic. Every object that **isn’t the apple** (except for the ground) has a name ending in `_na`. So during collision checks, I can just verify if the collided mesh **is not** the apple — if it ends with `_na`, it’s an instant game over. This avoids cluttering the code with a ton of if-statements checking for specific mesh names.

The entire game was **originally structured using Vite and Node modules**, with a clean setup and separate `main.js`. But when it came time to upload the game to **Itch.io**, I ran into platform limitations — Itch.io doesn’t support custom builds or advanced project structures. To make the game playable there, I migrated everything into a single `index.html`, swapped out module imports for **CDN links**, and stuffed the JavaScript directly in the HTML. Not ideal from a dev perspective, but it got the job done and made the game publicly accessible.

You can now play the game live on **[Itch.io](https://www.solidatary.itch.io/snake)** — no installation, just open and play right in the browser. It's a compact project, but it pushed me into new territory — from working with 3D engines and shaders, to optimizing collisions and learning deployment quirks for web games.

All in all, this project was way more than just a game — it was an intro to 3D development, an exercise in optimization, and a lesson in creative problem solving. I’m extremely thankful to the entire **CS50x** team for building such a powerful and approachable course. It gave me the foundation I needed to turn a simple idea into a functional, playable game, and more importantly, it showed me just how much you can build once you stop hesitating and just start building.

---
