Tetris Code Efficiency Analysis

The Tetris implementation is generally efficient because it uses
lightweight data structures, minimal DOM manipulation, and optimized
rendering techniques. The following points summarize its efficiency
characteristics:

1.  Efficient Rendering Using a Single
    ```{=html}
    <canvas>
    ```

The game uses one canvas element to draw the entire Tetris board and
falling pieces. This is efficient because:

Canvas operations are pixel-based and fast, especially for a small grid
like 10×20.

The browser only repaints one area, reducing layout and rendering
overhead.

No repeated creation or removal of DOM elements, avoiding expensive DOM
updates.

Using requestAnimationFrame() ensures drawing only occurs when the
browser is ready, preventing unnecessary CPU usage.

2.  Lightweight Data Structures (Matrices & Arrays)

The board and pieces are stored as small 2D arrays (matrices):

The Tetris board is only 10 columns × 20 rows → 200 cells.

Each tetromino is also a small matrix (4×4 or smaller).

Matrix operations such as rotation, collision detection, and merging are
constant-time or very close to it.

Because the grid is tiny, operations like scanning for full lines or
clearing rows run extremely fast, even in JavaScript.

3.  Optimized Game Loop

The update loop:

requestAnimationFrame(update);

is efficient because:

It matches the screen refresh rate.

It pauses in inactive browser tabs automatically, saving resources.

It avoids fixed-timer intervals like setInterval() which can generate
unnecessary updates.

The game calculates the time delta and only drops the piece when the
drop interval is reached, minimizing calculations per frame.

4.  Minimal DOM Interaction

Only three text elements---score, level, and lines---are updated. This
is efficient because frequent DOM manipulation is expensive, but here:

Updates occur only when needed (after a piece locks or lines clear).

No complex HTML reflows are triggered.

The gameplay stays smooth even on low-end devices.

5.  Efficient Collision and Line Checking

Collision detection is done by comparing the piece matrix with the board
matrix. Because both matrices are tiny:

Checking overlaps is fast.

Line clearing scans only 20 short rows.

Using simple loops avoids heavy built-in functions that introduce
overhead.

This results in very low CPU usage.

6.  Low Memory Usage

The memory footprint is extremely small because:

No large objects or unnecessary data structures are kept in memory.

Only one active piece is stored at a time.

Cleared lines are removed immediately, preventing memory buildup.

The game can run smoothly even on devices with limited RAM.

7.  Efficient Redraw Strategy

The canvas is cleared and redrawn each frame, which might seem
expensive, but for a Tetris grid it is very cheap:

Only 200 possible blocks to draw.

Each block is a small rectangle.

Canvas batching avoids individual DOM node repainting.

This full-redraw strategy is common in game engines and performs
excellently for simple 2D games.

8.  No External Libraries

The game runs:

Without frameworks

Without external heavy scripts

Without unnecessary imports

This keeps the bundle size minimal, loading times fast, and runtime
performance high.
