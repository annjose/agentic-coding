# Pomodoro Timer App Spec

## Objective
Build a web-based pomodoro timer app that helps the user work in focused time intervals. 
In its simplest classic form, it is work for 25 min, take a short break for 5 min - do this pair 3-4 times and take a long break of 15-30 min.

## Features
### Must have
1. User can start a pomodoro session which involves 'work' sessions and 'break' sessions
2. User can choose a 'Work' time interval  - pre-defined set (25 min, 45 min and 50 min) or custom time interval (between 5 and 120 min)
3. User can choose a 'Break' time interval - pre-defined set (5 min, 10 min and 15 min) or custom time interval (between 5 and 120 min)
4. User can start working by clicking a 'Start' or 'Work' button which starts the Work timer.
5. When the time interval for the work elapses, (eg: 25 min), the timer goes off and the alarm rings.
6. Then the Break timer starts, when that time interval lapses, alarm rings again and the Work timer starts automatically
7. User has the choice to pause the whole timer sequence anytime, so when they are ready to resume, they can click 'Resume' and the work timer starts from where it left off
8. User can quit the timer sequence altogether, at which all timers reset to the beginning
9. At the end of a pomodoro session, user can take a longer break (pre-configured from default set of 15 min, or 30 min), or choose a custom time

### Good to have
5. User can customize the theme of the app - 5 color palettes to choose from
5. Customize the chime sound of the alarm - 5 chimes
6. Desktop notifications when the work/break timer goes off. 

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

## Coding standards
- Read Coding Standards section in @AGENTS.md
