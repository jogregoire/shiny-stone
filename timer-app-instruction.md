# Timer App Instructions

## Purpose
A universal timer app for web browsers, supporting both mouse and touch input, with animated lightning effects and a persistent leaderboard. Designed for educational and demo use.

## File: `timer-app.html`
- **Self-contained**: All HTML, CSS, and JS are in one file. No build step or external dependencies.
- **Responsive**: Works on mobile and desktop, portrait and landscape.
- **Leaderboard**: Top 5 times are saved in `localStorage` and displayed with medals.
- **Lightning Effects**: Canvas-based visual feedback for user actions.

## Key Patterns
- **Universal Input**: Handles both mouse and touch events for timer control and effects.
- **State Machine**: Timer logic uses `timerState` (`idle`, `ready`, `running`, `stopped`).
- **Leaderboard Management**: Scores are sorted, deduplicated, and deletable. Leaderboard stays visible after all scores are deleted.
- **Debounced Delete**: Delete button uses a debounce to prevent accidental double deletion.
- **No External Libraries**: Only vanilla JS and browser APIs.

## Usage Flow
1. **Start**: Press and hold anywhere to prepare timer.
2. **Release**: Starts timing.
3. **Press again**: Stops timer and saves score.
4. **Leaderboard**: View and delete top scores. Leaderboard remains visible even if empty.

## Customization Points
- **Lightning Effect**: See `LightningBolt` class and `createLightning()` for visual tweaks.
- **Leaderboard Limit**: Change the `scores.slice(0, 5)` logic to adjust number of saved scores.
- **Status Messages**: All user feedback is managed via the `statusEl` element.

## Example Functions
- `handlePressStart(event)`: Handles both mouse and touch start events.
- `handlePressEnd(event)`: Handles both mouse and touch end events.
- `saveScore(time)`: Adds, sorts, and persists scores.
- `deleteScore(index, stayOnLeaderboard)`: Removes a score and updates leaderboard view.

## Mobile Considerations
- Prevents scrolling/zooming with `touchmove` and gesture event listeners.
- Uses viewport units for font sizes and layout.

## Troubleshooting
- If leaderboard disappears after deleting all scores, check `deleteScore()` logic to ensure `leaderboardEl.style.display = 'block'` is set when `scores.length === 0`.
- If timer does not start, verify input event listeners are attached and `timerState` transitions are correct.

---
For further details, see code comments in `timer-app.html`. All logic is inline and documented for educational clarity.
