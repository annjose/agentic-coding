# Pomodoro Timer App Spec

## Objective
Build a web-based pomodoro timer app that helps the user work in focused time intervals. 
In its simplest classic form, it is work for 25 min, take a short break for 5 min - do this pair 3-4 times and take a long break of 15-30 min.

## Features
### Must have
1. Timer with three modes: Work (25 min), Short Break (5 min), Long Break (15 min)
2. Session counter showing progress toward long break (every 4 work sessions)
3. Audio notification when timer completes
4. Simple controls: Start, Pause, Reset, Skip

### User Configurations
User can configure the following:
1. duration of the Work interval - pre-defined set (25 min, 45 min and 50 min) or custom time interval (between 5 and 120 min)
2. duration of the Short Break interval - pre-defined set (5 min, 10 min and 15 min) or custom time interval (between 5 and 120 min)
3. duration of the Long Break interval - pre-configured set (15 min, or 30 min), or choose a custom time
4. Number of work sessions in one Pomodoro session

### Features for later
5. User can customize the theme of the app - 5 color palettes to choose from
5. Customize the chime sound of the alarm - 5 chimes
6. Desktop notifications when the work/break timer goes off. 

## Core Timer Behavior
1. User clicks 'Start Work' → Timer counts down from configured work duration (default 25 min)
2. Work timer reaches 00:00 → Alarm plays for 2 seconds → Auto-advances to Short Break timer
3. Short Break timer reaches 00:00 → Alarm plays for 2 seconds → Auto-advances to next Work session
4. This Work-Break sequence repeats for the configured number of sessions (default 4 sessions). This completes one Pomodoro cycle.
5. After final work session → Modal appears: "Take a long break?" with options [15 min] [30 min] [Custom: ___ min] [Skip]

## Example User Flow

### Complete Pomodoro Cycle (Default Settings)
1. User opens app → sees "25:00" timer, "Start Work" button
2. Clicks "Start Work" → Timer counts down: 24:59, 24:58...
3. Timer reaches 00:00 → Alarm plays → Auto-advances to "Short Break 5:00"
4. Break counts down → 00:00 → Alarm → Auto-advances to "Work 25:00" (Session 2)
5. Repeat for sessions 3 and 4
6. After 4th work session → Modal: "Take a long break?"
7. User selects 15min → Long break starts
8. Long break ends → Alarm → Back to "Work 25:00" (Session 1 of new cycle)

### With Pause/Resume
1. User starts Work session → Timer at 18:23
2. User clicks "Pause" → Timer freezes at 18:23
3. User clicks "Resume" → Timer continues: 18:22, 18:21...
4. Session count remains the same throughout

## User Interface

### Layout (Desktop & Mobile)
**Timer Display (Center)**
- Current mode label: "Focus Time" / "Short Break" / "Long Break"
- Large countdown timer in MM:SS format (e.g., "24:35")
- Session progress indicator: Visual dots showing completed sessions (e.g., ●●●○ for 3 of 4)
  - Filled dots = completed sessions
  - Empty dots = remaining sessions

**Control Buttons (Below Timer)**
- Primary button: "Start Work" (initially) / "Pause" (when running) / "Resume" (when paused)
- Secondary buttons: [Skip] [Reset] [Quit]
- All buttons should be touch-friendly (min 44px height on mobile)

**Settings Access**
- Gear icon (⚙️) in top-right corner
- Opens settings modal/panel on click

### Settings Modal
**Layout**
- Overlay/modal that appears when gear icon clicked
- Close button (×) in top-right or click outside to dismiss
- Settings save automatically to localStorage on change

**Configuration Options**
- Work Duration: Radio buttons [25 min] [45 min] [50 min] [Custom: ___ min]
- Short Break Duration: Radio buttons [5 min] [10 min] [15 min] [Custom: ___ min]
- Long Break Duration: Radio buttons [15 min] [30 min] [Custom: ___ min]
- Sessions per Pomodoro: Number input (range: 2-8, default: 4)

### Modals & Notifications

**Long Break Modal** (appears after completing all work sessions)
- Title: "You've completed a Pomodoro cycle!"
- Message: "Take a long break?"
- Buttons: [15 min] [30 min] [Custom: ___ min] [Skip]

**Audio Failure Alert** (if audio.play() fails)
- Toast/banner notification: "Enable audio for timer alerts"
- Dismissible

## State Management
### Pause
- Freezes current timer at current value
- Preserves session count (e.g., still on session 2 of 4)
- Resume continues from exact same point
### Skip
- Immediately ends current timer (work or break)
- Advances to next phase in sequence (Work → Short Break → Work, etc.)
- Increments session count if skipping a work session
- Does NOT increment if skipping a break
### Reset (during active timer)
- Returns current timer to its starting value (e.g., 25:00 for work, 5:00 for short break)
- Preserves session count (still on session 2 of 4)
- Timer returns to paused state
- Useful if user wants to restart current interval
### Quit
- All timers reset to defaults
- Session count resets to 0
- Returns to initial "ready to start" state

## Tech stack
- React, Next.js, Tailwind CSS, TypeScript
- Browser local storage to store any settings, Counterscale for analytics

## Technical Constraints
- All the UI must be mobile responsive
- Should work in modern browsers (Chrome, Firefox, Safari)
  
## Commands
- Build: `npm run build` (compiles code, outputs to dist/)
- Test: `npm test` (runs Jest, must pass before commits)
- Lint: `npm run lint --fix` (auto-fixes ESLint errors)

## Project Structure
- `src/` – source code of the app
- `tests/` – unit and integration tests
- `docs/` – documentation

## Other Constraints
- Always ask before running database schemas,
- DO NOT commit passwords/ secrets, edit node_modules/, modify CI config

## Edge Cases & Special Behaviors

### Browser Tab Backgrounded
- Timer continues to run in background
- Alarm plays when timer completes even if tab not focused
- On tab focus return, UI updates to current timer state

### Browser Closed/Refreshed
- Active timer state is LOST (do not persist running timers)
- Settings persist (loaded from localStorage)
- User returns to initial "ready to start" state

### Audio Playback Fails
- Show visual alert modal if audio.play() fails
- Continue with timer sequence as normal
- Consider adding toast notification: "Enable audio for timer alerts"
  
## Definition of Done
- [ ] User can complete one full Pomodoro cycle (4 work + 3 short breaks + 1 long break)
- [ ] Settings persist across browser sessions
- [ ] Timer continues accurately in background tab
- [ ] All buttons work on mobile touch devices
- [ ] Audio plays on timer completion (tested in Chrome, Firefox, Safari)

## Coding standards
- Read Coding Standards section in @AGENTS.md
