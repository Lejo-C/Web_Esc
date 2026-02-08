# Web Escape Room - Solutions & Bugs Guide

This document lists all the bugs intentionally introduced into the "Web Escape Room" (Pages 16-20) and their respective solutions.

## Page 16: Robin's Ancient Poneglyph

### Bugs:
1.  **Button Disappearance**: The "DECIPHER TEXT" button is pushed down by `margin-top: 9000000px`, making it effectively nonexistent on the screen.
2.  **Hidden Translation**: The translation text is hidden with `visibility: hidden` and `opacity: 0`.

### Solution:
*   Inspect the element and remove or reduce the `margin-top` on the `button` style.
*   Click the button to trigger `decipherPoneglyph()`, which reveals the translation and the "Next Page" button.

## Page 17: Brook's Musical Performance

### Bugs:
1.  **Invisible Button Text**: The "PLAY BINKS' SAKE" button has `color: black` set on a black background, making it invisible.

### Solution:
*   Highlight the text on the screen to find the button, or inspect the DOM.
*   Change the CSS `color` of the button to a visible color (e.g., `#fff` or `var(--soul-green)`).
*   Click the button to play the music and reveal the "Next Page" button.

## Page 18: Franky's Radical Beam

### Bugs:
1.  **Missing Cola Button**: The `.btn-cola` class has `display: none`, hiding the button needed to refuel.
2.  **Broken Function Call**: The visible button (if revealed) has a typo in the onclick attribute: `add.Cola()`.
3.  **Radioactive Beam Disabled**: The main firing button is disabled until fuel reaches 100.

### Solution:
*   Remove `display: none` from `.btn-cola` in the CSS.
*   Change `onclick="add.Cola()"` to `onclick="addCola()"` in the HTML.
*   Click the Cola button 3 times (or more) to reach 100% fuel.
*   Click "FIRE RADICAL BEAM".

## Page 19: God Usopp's Sniper Nest

### Bugs:
1.  **Evasive Target**: The target has a `mouseover` event listener that moves it to a random position whenever the cursor gets close, making it impossible to click.

### Solution:
*   **Method 1 (Console):** Type `winGame()` in the browser console.
*   **Method 2 (Code):** Remove the `target.addEventListener('mouseover', moveTarget);` line in the script.
*   **Method 3 (Fast Reflexes):** Not recommended, almost impossible.

## Page 20: Luffy's Pirate King Challenge

### Bugs:
1.  **Decoy Buttons**: Three visible buttons (`#btn-1`, `#btn-2`, `#btn-3`) are fake and redirect to a "You Are Lost" page.
2.  **Hidden Real Button**: The real button (`#btn-4`) is hidden behind the entire page content using `z-index: -9999` and is placed outside the main container.
3.  **Hyper-Speed**: All buttons move every 100ms, making them hard to interact with.

### Solution:
*   **Method 1 (Console):** Type `revealSecret()` in the browser console.
*   **Method 2 (DOM Manipulation):** Delete the `<div id="gatekeeper">` element. This removes the black overlay and the fake buttons, revealing the real button (if you also fix its z-index or if the overlay was the only thing blocking interaction). OR, find `#btn-4` and change its `z-index` to `9999`.