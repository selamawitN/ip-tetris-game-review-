##  1. Efficient Rendering Using a Single `<canvas>`

The game uses **one canvas element** to draw the entire board and falling tetromino pieces.

**Why this is efficient:**
- Canvas operations are fast and pixel-based.
- Browser repaints only one region → lower rendering cost.
- Avoids heavy DOM creation/removal.
- Uses `requestAnimationFrame()` for smooth, optimized rendering.

```javascript
// Efficient animation loop
requestAnimationFrame(update);
```

---

##  2. Lightweight Data Structures (Matrices & Arrays)

Tetris uses small matrices to store board and pieces:

- **Board size:** 10 × 20 → *only 200 cells*
- **Tetromino size:** max 4 × 4

**Benefits:**
- Fast rotation, collision detection, and merging.
- Row checking is quick due to the tiny grid.
- Very low CPU usage.

---

##  3. Optimized Game Loop

The game loop uses:

```javascript
requestAnimationFrame(update);
```

**Advantages:**
- Syncs with the screen refresh rate.
- Stops when the tab is inactive (resource saving).
- Avoids unnecessary updates unlike `setInterval()`.
- Drops pieces only when needed (time-based).

---

##  4. Minimal DOM Interaction

Only UI elements like **score**, **level**, and **lines** are updated.

**This reduces:**
- Layout recalculations  
- Repainting  
- Browser overhead  

---

##  5. Efficient Collision & Line Checking

Collision logic compares the piece’s matrix with the board matrix.

**Why it's fast:**
- Both structures are small.
- Simple loops (no heavy methods).
- Clearing lines requires scanning only 20 rows.

---

##  6. Low Memory Usage

The game uses very little RAM because:
- Only one active piece is stored at a time.
- Cleared rows are immediately removed.
- No large or persistent objects.

---

##  7. Efficient Redraw Strategy

The entire board is redrawn every frame, which is cheap because:
- Only 200 blocks exist.
- Each block is just a small colored rectangle.
- Canvas batching improves rendering speed.

---

##  8. No External Libraries

The game runs **without**:
- Frameworks  
- Heavy external scripts  
- Large libraries  

**Benefits:**
- Tiny bundle size  
- Faster loading time  
- Better performance  

---

##  Summary

The Tetris implementation is efficient due to:
- Lightweight data structures  
- Optimized rendering  
- Minimal DOM updates  
- Smart animation loop  
- Low memory 
