# StreamElements Interactive Bingo Overlay 🎯

A lightweight, interactive 3x3 Bingo grid widget built for **StreamElements** overlays (compatible with Twitch and YouTube). 

Streamers and moderators can toggle bingo cards directly via Twitch chat commands, or the streamer can manually click/toggle them using the **Interact** feature in OBS Studio.

---

## ✨ Features
- **3x3 Grid Layout:** Compact design (320px width) optimized for stream overlays without taking up too much screen space.
- **High Readability:** Large text scaling for easy reading on live streams.
- **Role-Based Chat Controls:** Access restricted to the **Broadcaster**, **Moderators**, and **Lead Moderators**.
- **Dual Functionality:** Works via Twitch chat commands OR direct mouse clicks in OBS.
- **Zero Dependencies:** Pure HTML, CSS, and Vanilla JavaScript—no external libraries or complex bot setups required.

---

## 🎮 Chat Commands

> ⚠️ **Note:** Commands are strictly available to the Channel Owner and Moderators.

| Command | Description | Example |
| :--- | :--- | :--- |
| `!bingo [1-9]` | Toggles (checks/unchecks) card number 1 through 9. | `!bingo 3` |
| `!bingoreset` | Resets the entire bingo board, unchecking all cards. | `!bingoreset` |

---

## ⚙️ How the Code Works

The widget consists of three main parts that work seamlessly inside StreamElements:

### 1. HTML (`index.html`)
The grid is built using a simple `<div>` layout. Each bingo card contains an `onclick` event trigger (`toggleBingoCell(number)`) and an internal `<span>` for the card number overlay.
```html
<div class="bingo-card" id="cell-1" onclick="toggleBingoCell(1)">
  <span class="num">1</span>First Win!
</div>

2. CSS (style.css)
Grid Structure: Utilizes CSS Grid (repeat(3, 1fr)) to maintain a perfectly proportional 3x3 layout.

Visual Feedback: Uses the .checked class to toggle green background highlights, line-through text effects, and soft glowing shadows when a tile is marked.

Responsiveness: Maintains fixed square ratios (aspect-ratio: 1) while auto-fitting long words safely via word-break.

3. JavaScript (script.js)
Cell Toggling: The core toggleBingoCell(num) function simply adds or removes the .checked class on the target element ID (cell-1, cell-2, etc.).

StreamElements Event Listener: Listens to incoming chat messages via window.addEventListener('onEventReceived', ...).

Permission Checking: Evaluates the sender's badges (broadcaster, moderator, lead_moderator) and channel name (CHANNEL_NAME) before processing any command to prevent unauthorized users from editing the board.

🚀 Installation & Setup
1. Log in to your StreamElements Dashboard and open your Overlay Editor.

2. Click Add Element (+) → Static/Custom → Custom Widget.

3. Open the Open Editor menu inside the widget settings:

  Paste the HTML code into the HTML tab.

  Paste the CSS code into the CSS tab.

  Paste the JS code into the JS tab.
  
  In the FIELDS tab, type {}.

4. In the JS tab, make sure to set the channel name variable to your target account:

const CHANNEL_NAME = "YourChannel"; // Change to your Twitch username

4. Click Save and test the widget!

📄 License & Credits
This project is licensed under the MIT License.

Made by Lars_Rubens. Feel free to use, modify, and distribute this widget for your own streams!

