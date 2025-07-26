---
goal: Rubik's Cube Timer Webapp - Universal, No Frameworks, Session/Leaderboard Flow
version: 1.1
date_created: 2025-07-26
last_updated: 2025-07-26
owner: shiny-stone-team
status: 'Completed'
tags: [feature, webapp, timer, leaderboard, vanilla-js, educational]
---

# Introduction

![Status: Completed](https://img.shields.io/badge/status-Completed-green)

This plan details the implementation of a self-contained, framework-free Rubik's Cube Timer webapp. The app features an intro screen, a universal timer session (mouse/touch), and a persistent leaderboard with delete operations. All logic, styles, and markup are embedded in a single HTML file for direct browser use.

The web app is meant to time how long it takes me to solve a rubiks cube. The overall flow of the app is:

1. **intro**: the app starts and explains the app. there's a button to start a session
2. **session**: enter a session: the screen shows a timer ready to start. when the finger lets go of the touch or the click of the mouse, the timer starts. The timer stops when the screen is clicked/touched again. After stopping, the app auto-transitions to the leaderboard after 2 seconds.
3. **leaderboard**: a leaderboard is shown with up to 10 entries that fits in the screen. there are buttons next to each entry to delete them. The leaderboard is persisted in the cache of the browser. There is a "New Session" button to start a new session and return to step #2. Each entry shows the player name "Flo" with a date/time suffix.

**Key Implementation Changes:**
- Removed "View Leaderboard" button from session screen for cleaner interface
- Removed "Back to Home" button from leaderboard screen for streamlined flow
- Auto-transition from session to leaderboard after completing a solve
- Simplified navigation: intro → session → auto-leaderboard → new session loop
- Added player names with "Flo" prefix and date/time suffix (e.g., "Flo Jan 25 15:12:42")


## 1. Requirements & Constraints

- **REQ-001**: App must be a single, self-contained HTML file (`rubiks-timer.html`)
- **REQ-002**: No external dependencies, frameworks, or build steps
- **REQ-003**: Universal input: support both mouse and touch events for timer control
- **REQ-004**: Responsive design for mobile and desktop, portrait and landscape
- **REQ-005**: Leaderboard displays up to 10 entries, each with a delete button
- **REQ-006**: Leaderboard persists in browser cache using `localStorage`
- **REQ-007**: Leaderboard remains visible even if empty
- **REQ-008**: Auto-transition from session to leaderboard after timer completion
- **REQ-009**: Streamlined navigation without manual leaderboard access from session
- **REQ-010**: Each leaderboard entry includes player name as "Flo" with date/time suffix (format: "Flo Jan 25 15:12:42")
- **REQ-011**: Extensive code comments for educational clarity
- **CON-001**: No server-side code; all logic runs in browser
- **CON-002**: All CSS and JS must be embedded in the HTML file
- **PAT-001**: Use state machine for app flow: `intro`, `session`, `leaderboard`
- **PAT-002**: Debounced delete for leaderboard entries
- **PAT-003**: Use viewport units and flexbox for layout

## 2. Implementation Steps

| Task ID      | Description                                                                                           | File Path                        | Dependencies         | Status      | Validation Criteria                                 |
|--------------|------------------------------------------------------------------------------------------------------|----------------------------------|----------------------|-------------|-----------------------------------------------------|
| TASK-001     | Create `/plan/feature-rubiks-timer-1.md` with this implementation plan                               | `/plan/feature-rubiks-timer-1.md`| None                 | ✅ Completed | File exists, template compliance                    |
| TASK-002     | Create `rubiks-timer.html` with embedded CSS/JS, following project conventions                       | `rubiks-timer.html`              | TASK-001             | ✅ Completed | File exists, loads in browser, no errors            |
| TASK-003     | Implement intro screen: app explanation, "Start Session" button                                      | `rubiks-timer.html`              | TASK-002             | ✅ Completed | Intro visible, button triggers session              |
| TASK-004     | Implement session screen: timer ready, universal input (mouse/touch), timer start/stop logic         | `rubiks-timer.html`              | TASK-003             | ✅ Completed | Timer starts/stops as specified                     |
| TASK-005     | Implement leaderboard screen: show top 10 times, delete buttons, persistent via localStorage         | `rubiks-timer.html`              | TASK-004             | ✅ Completed | Leaderboard displays, persists, delete works        |
| TASK-006     | Remove navigation buttons for streamlined flow (no "View Leaderboard" or "Back to Home")            | `rubiks-timer.html`              | TASK-005             | ✅ Completed | Buttons removed, auto-transition implemented        |
| TASK-007     | Ensure leaderboard remains visible when empty                                                        | `rubiks-timer.html`              | TASK-005             | ✅ Completed | Leaderboard visible with zero entries               |
| TASK-008     | Add debounce to delete buttons to prevent double deletion                                            | `rubiks-timer.html`              | TASK-005             | ✅ Completed | Double-click does not delete multiple entries       |
| TASK-009     | Add educational comments to all code sections                                                        | `rubiks-timer.html`              | TASK-002-TASK-008    | ✅ Completed | Comments present, explain logic                     |
| TASK-010     | Validate responsive design: test on mobile/desktop, portrait/landscape                              | `rubiks-timer.html`              | TASK-002-TASK-009    | ✅ Completed | Layout adapts, no overflow, all controls accessible |
| TASK-011     | Add player names with "Flo" prefix and date/time suffix to leaderboard entries                      | `rubiks-timer.html`              | TASK-005             | ✅ Completed | Each entry shows "Flo Jan 25 15:12:42" format      |

## 3. Alternatives

- **ALT-001**: Use multiple HTML files for each screen (Rejected: violates self-contained requirement)
- **ALT-002**: Use external JS/CSS files (Rejected: violates embedded code requirement)
- **ALT-003**: Use a JS framework (Rejected: violates no-frameworks requirement)
- **ALT-004**: Keep "View Leaderboard" and "Back to Home" buttons (Rejected: creates navigation complexity, distracts from focused timing experience)

## 4. Dependencies

- **DEP-001**: Browser supporting ES6, localStorage, and standard DOM APIs
- **DEP-002**: No external libraries or assets required

## 5. Files

- **FILE-001**: `/plan/feature-rubiks-timer-1.md` - This implementation plan
- **FILE-002**: `rubiks-timer.html` - Main app file, all logic/styles/markup embedded

## 6. Testing

- **TEST-001**: Open `rubiks-timer.html` in browser, verify intro screen and session start
- **TEST-002**: Test timer start/stop with both mouse and touch events
- **TEST-003**: Add multiple times, verify leaderboard displays 10 entries max
- **TEST-004**: Delete entries, verify leaderboard persists and remains visible when empty
- **TEST-005**: Test auto-transition from session to leaderboard after timer completion
- **TEST-006**: Validate localStorage persistence across browser sessions
- **TEST-007**: Test responsive layout on mobile/desktop, portrait/landscape
- **TEST-008**: Attempt double deletion, verify debounce works
- **TEST-009**: Verify player names display correctly with "Flo" prefix and date/time suffix format

## 7. Risks & Assumptions

- **RISK-001**: Browser compatibility issues with older browsers
- **RISK-002**: LocalStorage quota exceeded if user adds excessive entries (mitigated by 10-entry limit)
- **ASSUMPTION-001**: User has modern browser with touch/mouse support
- **ASSUMPTION-002**: No server-side persistence required

## 8. Related Specifications / Further Reading

- [Timer App Instructions in `timer-app-instruction.md`](./timer-app-instruction.md)
- [MDN: localStorage API](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage)
- [MDN: Touch Events](https://developer.mozilla.org/en-US/docs/Web/API/Touch_events)
- [MDN: Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout/Basic_Concepts_of_Flexbox)
