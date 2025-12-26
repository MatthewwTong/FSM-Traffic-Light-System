# Traffic Light FSM (5-State) — Logisim

A finite state machine (FSM) traffic light controller built in **Logisim / Logisim Evolution** with **5 states**:
- **Green**
- **Yellow**
- **Red**
- **Red + Walk**
- **Power-Saving (all lights off)**

This was made as a digital logic / state machine course project to practice **FSM design, state encoding, and synchronous control logic**.

---

## Demo / Screenshots
> Add screenshots or a GIF here (highly recommended for recruiters)

- `docs/screenshot.png`
- `docs/waveform.png` (optional)

---

## Features
- Cycles through **Green → Yellow → Red → Green** on a clock/timer
- **Walk button** triggers a **Red + Walk** state (only when in Red)
- **Power-saving mode** turns off outputs (e.g., at night / low traffic)
- **Reset** returns the system to **Green** (known safe state)
- Fully synchronous FSM (recommended: DFFs / registers)

---

## How It Works

### Inputs
- `CLK` — clock input (drives state transitions)
- `RESET` — resets FSM to Green
- `WALK_BTN` — request pedestrian crossing (only takes effect during Red)
- `POWER_SAVE` — toggles power-saving mode (forces outputs off / enters a mode state)

### Outputs
- `GREEN_LED`
- `YELLOW_LED`
- `RED_LED`
- `WALK_LED` (white pedestrian LED)
- `POWERSAVE_LED` (pink LED)
---

## State Definitions
| State Name       | Meaning |
|------------------|---------|
| `GREEN`          | Cars go |
| `YELLOW`         | Prepare to stop |
| `RED`            | Cars stop |
| `RED_WALK`       | Cars stopped + pedestrian walk |
| `POWER_SAVING`   | All lights off |

### Example Transition Logic (High-Level)
- `GREEN → YELLOW → RED → GREEN` (normal loop)
- If `WALK_BTN=1` while `RED`, then `RED → RED_WALK → GREEN`
- If `POWER_SAVE=1`, go to `POWER_SAVING` (or force outputs off, depending on your design)
- `RESET` always returns to `GREEN`

> If your project uses slightly different rules (ex: power-save returns to last state), update this section.

---

## State Encoding (Edit to match your circuit)
Example 3-bit encoding:
- `000 = GREEN`
- `001 = YELLOW`
- `010 = RED`
- `011 = RED_WALK`
- `100 = POWER_SAVING`

If you used different encodings, replace the table above.

---

## File Structure (Recommended)
