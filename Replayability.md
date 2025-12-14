# Replayability Review — *Tetris (Vanilla JavaScript)*  

---

## Overview

**Replayability** means: *Does this game make me want to play again and again?*

In this Tetris, the basic game works: pieces fall, lines clear, and the speed increases.  
To make players return more often, we can make the piece order fair, save best scores, restart quickly,  
and add a few planning tools like **Next** and **Hold**.

---

## What I Checked
- How fair the piece order feels  
- How the speed changes over time (levels)  
- How scoring feels  
- How easy it is to restart  
- If the best score is saved  
- If the game shows **Next** pieces and a **Hold** slot  

---

## What Is Good
- The core loop is fun: drop pieces, clear lines, and survive.  
- Speed increases gradually, adding challenge.  
- Controls are responsive and smooth.  

---

## What Can Be Better for Replayability
- Piece order sometimes feels unfair (long wait for an I‑piece).  
- Best score disappears after refresh.  
- Restart takes extra steps—hurts the *“one more try”* feeling.  
- Planning tools are limited (0–1 Next piece, no Hold).  
- Only one way to play—no alternate modes.  

---

## Suggestions (Step by Step)

### Fair Piece Order — the “7‑Bag”
**Why:** avoids bad‑luck streaks and ensures fair distribution.  
**Idea:** a bag with all 7 shapes is shuffled; pieces come out one‑by‑one, refill when empty.

```js
const pieces = ['I','J','L','O','S','T','Z'];
let bag = [];

function shuffle(a) {
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

function nextPieceType() {
  if (bag.length === 0) bag = shuffle([...pieces]);
  return bag.pop();
}

```
### 🏆 Save and Show High Score
```js
const HIGH_KEY = 'tetrisHighScore';

function getHigh() {
  return Number(localStorage.getItem(HIGH_KEY)) || 0;
}

function saveHighIfBetter(score) {
  const best = getHigh();
  if (score > best) localStorage.setItem(HIGH_KEY, String(score));
}
```
### 🔄 Fast Restart (Keeps the Flow)
```js
window.addEventListener('keydown', (e) => {
  if (gameOver && (e.code === 'Enter' || e.code === 'KeyR')) {
    e.preventDefault();
    startNewGame();
  }
});
```
### 🎯 Better Planning — More Next Pieces + Hold
```js
let holdType = null;
let canHold = true;  // reset to true when a piece locks

function holdSwap() {
  if (!canHold) return;
  if (holdType === null) {
    holdType = current.type;
    current = createPiece(nextPieceType());
  } else {
    const t = holdType;
    holdType = current.type;
    current = createPiece(t);
  }
  current.resetPosition(); // back to spawn
  canHold = false;
}
```
###  ⚡ Smoother Level Speed
```js
function dropSpeedMs(level) {
  const start = 1000;  // 1 second
  const min = 100;     // fastest speed
  const rate = 0.9;    // 10 % faster per level
  return Math.max(min, Math.floor(start * Math.pow(rate, level)));
}
```
