# 🔨 Whack-the-Word!

A fast **sight-word recognition** game for the **Fry First 100** words, built to
beef up a child's visual word recognition through quick matching and repetition.

Two signs on the "mole-hole" board show the **same word**. The student finds and
taps **both** matching words. The computer then **reads the word aloud**, and the
student **says it back** before the next round pops up.

## How to run

**Easiest:** double-click `index.html` — it opens in any browser and just works
(no install, uses the browser's built-in text-to-speech).

## Controls

- **Touchscreen / mouse:** tap the two signs that show the same word.
- **Laptop keyboard:** use the **arrow keys** `← ↑ → ↓` to move the white
  highlight between signs, and press **Space** (or Enter) to pick a word.
  Pick the two matching words to score.

## Teaching flow each round

1. Find & select the two identical words → the sign gets "whacked".
2. 🔊 The computer reads the word out loud.
3. 🗣️ The prompt says **"Now YOU say it"** — the student repeats it aloud.
4. The next round pops up automatically.

## 🪙 Reward mini-game ("Coin Run")

After **every 5 correct matches**, a Mario-style scrolling bonus pops up for
**~30 seconds**. The Roblox character **runs along a trail** that is wider than
the screen (the camera follows), collecting coins by:

- **Bonking golden ? blocks** from below by jumping.
- **Shooting arrows** (🏹) — arrows fly up-and-forward, so you "lead" the shot.
- **Dealing with bugs:** red bugs crawl along the trail. **Touching one costs you
  coins** (with a brief flashing grace period). **Jump over** them, or **shoot
  them** with an arrow (defeating a bug gives a coin).
- **High blocks** (the glowing blue ones, especially the highest) **can't be
  reached by jumping** — you have to pick them off with a well-aimed arrow. They
  are worth **2 coins** each.

Every coin adds bonus points to the main score, then play returns to the word
game automatically.

### Mini-game controls

- **Touchscreen:** the on-screen **◀ / JUMP / SHOOT / ▶** buttons.
- **Laptop:** **← →** (or `A` `D`) to run, **Space / ↑ / `W`** to jump,
  **`P`** to shoot an arrow.

Tweak in `index.html` (the `MINI` object): `duration` (30000 ms), jump/gravity
feel (`JUMP`, `GRAV`, `MOVE`), arrow flight (`ARROW_VX`, `ARROW_VY` — raise
`ARROW_VY` to make high blocks easier), bug difficulty (`BUG_SPEED`,
`BUG_PENALTY`, `IFRAMES`), and the block/bug layout arrays inside `startMini()`.
Coins are worth 5 points each in `endMini()`; the "every 5 matches" trigger lives
in `advance()`.

## Settings

- **Difficulty** (title screen): Easy = 4 words, Medium = 6, Hard = 9.
- **🔊 / 🔇** button mutes/unmutes the computer voice.
- **🏠** returns to the title screen.

## Tweaking

Everything is in `index.html`:

- **Word list** — the `FRY100` array near the top of the `<script>`.
- **Difficulty grids** — the `MODES` object (`holes` + grid `cols`).
- **Voice speed** — the `rate` in `speak()` (default `0.85`, slower = clearer).
- **Repeat pause** — the timeout in `repeatPhase()` (default 2.2s before the
  next round) — increase it to give more time to say the word.
