# Fisher-Yates-Shuffle Algorithm

The Fisher-Yates shuffle is an efficient algorithm for randomly shuffling an array. The given JavaScript code implements it dynamically in a **colorful animated grid** where each block is shuffled in real time.


## **1. Code Structure**
The code consists of:
1. **HTML Elements** – Canvas for visualization, buttons for interaction.
2. **CSS Styles** – For layout, styling the canvas, and creating a modern UI.
3. **JavaScript Functionalities** – Implementing Fisher-Yates Shuffle, handling animations, interactions.


## **2. Understanding the Fisher-Yates Shuffle**
The algorithm randomly swaps elements in an array from the end to the beginning, ensuring each item has an equal probability of appearing in any position.

### **Implementation in Code**
```js
function shuffle(array) {
    i = Math.floor(Math.random() * n--);  // Select a random index
    t = array[n];                         // Store the last element
    array[n] = array[i];                   // Swap last element with random index
    array[i] = t;                          // Complete swap
    return array;
}
```
- Picks a random index.
- Swaps it with the last unshuffled element.
- Moves the boundary of shuffled elements backward.
- This ensures a truly random shuffle in **O(n) time complexity**.


## **3. Code Breakdown**
### **a) Initialize the Grid**
```js
s = 15; // Cell size
var gridSize = 20 * s;
c.width = gridSize;
c.height = gridSize;
m = (c.width / s) * (c.height / s);
n = m;
bytes = new Uint8Array(m);
```
- Defines a **grid of 20×15 squares**.
- Each block is stored in an array (`bytes`), representing colors.


### **b) Rendering the Grid with Random Colors**
```js
function render() {
    i = 0;
    while (i < m) {
        t = bytes[i];
        let hue = (t * 137.508) % 360; // HSL color algorithm for mesmerizing colors
        ctx.fillStyle = `hsl(${hue}, 100%, 50%)`;
        x = (i % (c.width / s)) * s;
        y = Math.floor(i / (c.width / s)) * s;
        ctx.fillRect(x, y, s, s);
        i++;
    }
    bytes = shuffle(bytes);
}
```
- Uses **HSL (Hue, Saturation, Lightness) color model** for dynamic color changes.
- Each color is based on the value from the shuffled array.
- The **grid is redrawn continuously**, making the colors shuffle.


### **c) Animation and Event Handling**
```js
function dothedamnthing() {
    if (running) {
        requestAnimationFrame(dothedamnthing);
        render();
    }
}

c.addEventListener("click", function() {
    running = false;
});
```
- `requestAnimationFrame(dothedamnthing)` keeps the shuffle running.
- Clicking on the **canvas stops the animation**.


### **d) UI Elements**
1. **Shuffle Restart Button**
```html
<button id="play" onclick="Shuffle.run()">Run again</button>
```
- Clicking this button **resets the shuffle**.

2. **Info Button with Pop-up**
```html
<button id="infoButton">&#9432;</button>
<div id="infoPopup">
    <strong>Fisher-Yates Shuffle</strong>
    <p>This algorithm efficiently shuffles an array by swapping elements randomly from the end of the array to the beginning.</p>
    <p>Click on the grid to stop the shuffle. Click the 'Run again' button to restart.</p>
</div>
```
- Displays **a brief explanation** of the shuffle algorithm and instructions.
- Toggles visibility on click:
```js
document.getElementById("infoButton").addEventListener("click", function() {
    var popup = document.getElementById("infoPopup");
    popup.style.display = popup.style.display === "none" ? "block" : "none";
});
```

## **4. Summarizing**
- **Fisher-Yates Shuffle** swaps elements randomly to shuffle efficiently.
- **Canvas renders a colorful grid** that dynamically changes.
- **Clicking stops the animation**, and **a button restarts the shuffle**.
- **An info button displays an alert-style pop-up** with instructions.


### **Why Fisher-Yates?**
- It’s an **optimal** shuffling algorithm (**O(n) complexity**).
- Ensures a **uniform random permutation**.
- Used in real-world applications like **games, cryptography, and simulations**.
