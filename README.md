# 🎭 Who Said It? — The Bard’s Game

A fast-paced browser game about Shakespeare. A famous quote appears at the top of the screen while the names of Shakespearean characters rain down from above. Steer a tiny Shakespeare left and right, **catch the character who said the line**, and **dodge everyone else**.

**▶ Play it now: [andguerreiro.github.io/bardsgame](https://andguerreiro.github.io/bardsgame)**

---

## How to play

1. Tap **Play** (or press `Enter`). You start with **10 lives**.
2. Read the quote at the top of the screen.
3. Catch the name of the character who said it before it hits the floor.
4. Avoid all the other names. They fall vertically, at different speeds.

You lose a life when you:

- catch the **wrong** character, or
- let the **right** character fall to the floor.

When your lives run out, the curtain falls. Your best score is saved in your browser.

### Automatic difficulty

There is no difficulty menu. The game starts gentle and speeds up on its own as you catch the right characters:

| Stage  | Reached after        | Fall speed |
| ------ | -------------------- | ---------- |
| Easy   | start                | Slower     |
| Normal | 5 correct catches    | Standard   |
| Hard   | 12 correct catches   | Faster     |

Your lives are not reset when the stage changes.

### Scoring

- Each correct catch earns **10 points**, plus **2 bonus points per catch in your current streak** (the bonus caps at +20).
- Wrong catches and misses reset your streak.
- Every **4 correct catches** you level up, and the names fall faster.

## Controls

| Action                       | Keyboard                    | Mouse / Touch           |
| ---------------------------- | --------------------------- | ----------------------- |
| Move                         | `←` `→` or `A` `D`          | Click/tap and drag      |
| Start / replay               | `Enter` or `Space`          | Tap anywhere on the title screen |

The game works on desktop and mobile browsers.

## Features

- 29 quotes from *Hamlet*, *Macbeth*, *Romeo and Juliet*, *Julius Caesar*, *Richard III*, *The Merchant of Venice*, *A Midsummer Night’s Dream*, *The Tempest*, *Othello* and *King Lear*
- 34 characters to catch (or avoid)
- Automatic difficulty ramp: Easy → Normal → Hard
- Names that fall vertically at random speeds
- Streak bonuses and a level system
- Local best score (stored with `localStorage`)
- No dependencies, no build step: a single HTML file with plain JavaScript and the Canvas API

## Run it locally

Clone the repository and open the page in a browser:

```bash
git clone https://github.com/andguerreiro/bardsgame.git
cd bardsgame
open index.html   # macOS; on Linux use xdg-open, on Windows just double-click the file
```

Or serve it with any static server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy with GitHub Pages

1. Make sure the game file is named `index.html` and sits in the root of the repository.
2. On GitHub, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select your main branch and the `/ (root)` folder, then save.
4. After a minute or so, the game is live at `https://andguerreiro.github.io/bardsgame`.

## Project structure

```
bardsgame/
├── index.html   # the whole game: markup, styles and code
└── README.md
```

## Customizing the game

Everything lives in `index.html`. Look for these pieces near the top of the script:

- **`Q`**: the list of quotes. Each entry has the format `[quote, unused, character, play]`. The second field is not displayed, so you can leave it as an empty string. Example:

  ```js
  ["Brevity is the soul of wit.", "", "Polonius", "Hamlet"]
  ```

- **`POOL`**: every character name that can fall. The `character` of each quote must also appear here, spelled exactly the same way.
- **`DIFF`** and **`stage()`**: the speed multiplier of each stage and the number of correct catches that trigger Normal (5) and Hard (12). Tweak these to rebalance the game.
- **`PLAYS`**: maps stored play names to the display names shown after a correct catch. Play names that are not in this map are shown as written.

## Tech

- HTML5 Canvas
- Vanilla JavaScript (no frameworks, no libraries)
- Georgia/serif system fonts, so there are no external requests

## Credits and license

The quotes are from the works of William Shakespeare, which are in the public domain. The game code is released under the MIT License. Add a `LICENSE` file to the repository if you want to make that official.

Made with a quill, a ruff collar and a lot of ado. *All the world’s a stage.*
