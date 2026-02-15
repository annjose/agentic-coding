# Statistics Dashboard - Feature Spec

## Context
**Existing App**: Pomodoro Timer Web App
**Current Version**: v1.0.0
**Tech Stack**: React, Next.js, Tailwind CSS, TypeScript, localStorage
**Repository**: https://github.com/user/pomodoro-timer

## Problem Statement
Users want to see their productivity patterns and track their progress over time. Currently, the app only shows real-time session progress but doesn't persist or visualize historical data.

## Objective
Add a Statistics Dashboard that shows users their Pomodoro history, completion trends, and productivity metrics.

## Current State
### What Exists Today
- Timer tracks current session in real-time
- Session count (1 of 4) visible during active Pomodoro cycle
- Settings saved to localStorage
- No historical data persisted

### What Users Cannot Do Currently
- See how many Pomodoros completed yesterday, this week, this month
- Track their longest streak
- View productivity patterns (best times of day, etc.)
- Get motivation from seeing their progress

## Proposed Feature
### What's New
1. Persistent storage of completed Pomodoro sessions
2. Statistics dashboard with key metrics
3. Visual charts showing trends
4. Streak tracking and achievements

### User Flow Changes
**Before**: 
Complete session → Counter increments → After long break, counter resets to 0

**After**: 
Complete session → Counter increments → Session saved to history → Can view in Stats → After long break, counter resets but history preserved

## Integration Points
### Existing Code to Modify
```
src/
├── components/
│   └── Timer.tsx                    # MODIFY: Save session on completion
├── hooks/
│   └── useTimer.ts                  # MODIFY: Add onSessionComplete callback
└── types/
    └── index.ts                     # MODIFY: Add Session and Statistics types
```

### New Code to Add
```
src/
├── components/
│   ├── StatisticsDashboard.tsx      # NEW: Main dashboard
│   ├── StatsCard.tsx                # NEW: Metric display card
│   └── TrendChart.tsx               # NEW: Chart component
├── hooks/
│   └── useStatistics.ts             # NEW: Stats logic and data
├── utils/
│   └── statsCalculator.ts           # NEW: Calculate metrics
└── lib/
    └── storage.ts                   # NEW: localStorage wrapper
```

### Storage Schema (localStorage)
```typescript
// Key: 'pomodoro_sessions'
interface Session {
  id: string;
  type: 'work' | 'short_break' | 'long_break';
  duration: number;          // in minutes
  completedAt: number;       // Unix timestamp
  wasCompleted: boolean;     // true if finished, false if skipped
}

// Key: 'pomodoro_statistics'
interface Statistics {
  totalSessions: number;
  totalFocusMinutes: number;
  currentStreak: number;
  longestStreak: number;
  lastSessionDate: string;   // ISO date
}
```

## UI Changes
### New Route/View
- Add "Statistics" tab/button in navigation
- Opens full-screen dashboard or modal

### Dashboard Layout
```
┌─────────────────────────────────────┐
│  [← Back to Timer]                  │
│                                     │
│  Your Statistics                    │
│                                     │
│  ┌──────┐ ┌──────┐ ┌──────┐        │
│  │  42  │ │ 1050 │ │  7   │        │
│  │Total │ │ Min  │ │Streak│        │
│  └──────┘ └──────┘ └──────┘        │
│                                     │
│  This Week                          │
│  ████████████░░░░░░░░               │
│  Mon Tue Wed Thu Fri Sat Sun        │
│                                     │
│  Recent Sessions                    │
│  • 25 min - Today at 2:30 PM       │
│  • 25 min - Today at 1:45 PM       │
│  • 25 min - Yesterday at 4:00 PM   │
│                                     │
│  [Clear All Data]                   │
└─────────────────────────────────────┘
```

### Main Timer Screen Addition
- Add small "📊 Stats" button near settings
- Shows mini summary: "42 sessions this week"

## Backward Compatibility
### Handling Existing Users
- Users who've been using app have no history
- Statistics start from $0 when feature launches
- Show message: "Start completing sessions to see your stats!"

### No Breaking Changes
- All existing timer functionality remains unchanged
- Statistics are opt-in to view (don't force navigation)

## Edge Cases
1. **localStorage Full**: Show warning, offer to delete old data
2. **localStorage Cleared**: Statistics reset, show "fresh start" message
3. **Date/Time Changes**: Use UTC for storage, display in local time
4. **Multiple Tabs**: Use storage events to sync between tabs
5. **Incomplete Sessions**: Track but mark as `wasCompleted: false`

## Testing Requirements
- [ ] Session saves correctly on completion
- [ ] Statistics calculate accurately across date boundaries
- [ ] Charts render correctly with 0, 1, and 100+ sessions
- [ ] localStorage quota handling
- [ ] Multi-tab synchronization
- [ ] Timezone changes don't corrupt data

## Out of Scope (Future V2)
- Cloud sync across devices
- Comparison with friends
- AI productivity insights
- Export to CSV
- Goals and targets

## Definition of Done
- [ ] Sessions persist across browser refreshes
- [ ] Statistics accurately reflect all completed work sessions
- [ ] Dashboard is mobile responsive
- [ ] No performance impact on timer functionality
- [ ] Data can be cleared by user
- [ ] All existing tests still pass
- [ ] New feature has unit tests