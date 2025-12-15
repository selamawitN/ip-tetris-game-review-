
<h2>Input validation</h2>
   <p>Here’s how input validation works in the Tetris game. Since everything runs on the client, the main thing that matters is keeping the game logic tight—making sure you can’t break the rules, mostly through collision detection. That’s what keeps the game state from falling apart.</p>
<p>Players can’t type in random text or enter anything outside the game controls. It’s all about the keyboard arrows.</p>
 <h3> I. Keyboard Input </h3>
<p>Tetris listens for keyboard events—specifically, when you press or release a key. That’s how you move and rotate the tetromino pieces.</p>
<h4>A. Allowed Keys and Actions:</h4>
 <ul>
   <p>It only cares about four keys:</p>
<li>Arrow Left (←): Move left.</li>
<li>Arrow Right (→): Move right.</li>
<li>Arrow Up (↑): Rotate.</li>
<li>Arrow Down (↓): Drop faster (soft drop).</li>
 </ul>
<h4> B. Input Filtering </h4>
<p> The code filters out everything else. If you hit any other key, the game ignores it. That’s the first line of defense against weird input. </p>
<h3> II. Input Validation (Collision Detection and Reversal) </h3>
<p> The heart of validation sits inside the ‘keydown’ event handler. Whenever you try to move or rotate a piece, the game checks—right away—if that move causes a collision. It uses <i>isTetrominoColliding()</i> for this. If the move isn’t allowed, the game instantly undoes it. So you never actually see the game enter an illegal state, even for a split second.</p>
<p>The keys execute this when touched:</p>
<dl>
  <li>ArrowLeft: Moves the piece left (tetrominoPosition.column--).</li> 
     <dd> -If that’s a collision, it bumps it right back (column++).</dd>
  <li>ArrowRight: Moves right (column++).</li> 
     <dd>-If it hits something, it moves back left (column--).</dd>
   <li>ArrowUp: Rotates the piece.</li>
     <dd>-If it collides, it just rotates it back.</dd>
   <li>ArrowDown: Speeds up the drop by setting dropInterval to 20.</li> 
     <dd> We don’t check for collisions here since gravity in the game handles it on the next tick. When you let go of the key, dropInterval goes right back to 500.</dd> 
  </dl>

<p>This setup is pretty solid—bad moves and illegal rotations never sneak through.</p>

## User Experience

The Tetris game features a clean and intuitive interface, clearly displaying the game board, score, level, and lines cleared. Control instructions are easy to follow, allowing players to quickly understand and interact with the game. The layout of the canvas alongside the informational panel enhances visual clarity and usability.

While the interface is functional, several improvements could enhance engagement and playability:

- **Next-Piece Preview:** Shows upcoming tetrominoes for better strategic planning.  
- **Hold-Piece Mechanic:** Allows storing a piece for later use, adding tactical depth.  
- **Visual and Audio Feedback:** Line-clear animations, piece-drop effects, and sound cues increase immersion.  
- **Smooth Animations:** Animated piece movements reduce abrupt visual transitions.  
- **Accessibility Enhancements:** Consistent key recognition across browsers and prevention of default key actions (e.g., scrolling) improve playability.  
- **Difficulty Scaling:** Adjustable levels or incremental drop speed maintain challenge and replay value.

These enhancements would significantly improve player satisfaction, engagement, and retention, bringing the game closer to professional Tetris standards.

