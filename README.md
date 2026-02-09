# Agentic Coding - Specs & Plans

A collection of specifications and plans for building software with AI coding agents.

## What This Is

Templates and real examples of specs that work well with AI agents. Use them as reference when writing your own.

**The key insight:** Clear specs with specific success criteria produce better results than vague instructions.

## What's Inside
```
agentic-coding/
├── templates/
│   ├── new-apps/           # For building from scratch
│   └── new-features/   # For adding to existing code
└── examples/
    └── new-apps/
        └── pomodoro-timer/    # Real spec + plan
```

## Using This Repo

Browse the templates and examples to see what makes a good spec:
- Clear objectives and success criteria
- Specific UI/UX requirements with examples
- Edge cases and constraints spelled out
- Tech stack and integration points defined

Copy what works for your project. Adapt to your needs.

### Templates

##### New App
Use `new-app/spec-template.md` when building something from scratch.

#### Feature Enhancement  
Use `feature-enhancement/spec-template.md` when adding to existing code.

Replace `[placeholders]` with your specifics. Delete sections that don't apply.

### Examples

Real specs from actual projects. Use these as reference for structure and level of detail.

- **new-apps/pomodoro-timer** - Complete web app spec
- **new-features/pomodoro-statistics** - Feature added to existing app

## Workflow
```
1. Write spec.md (use [/templates](/templates) as reference)
   ↓
2. Give spec to agent → agent creates plan.md
   ↓
3. Review/edit plan.md
   ↓
4. Agent executes plan step by step
   ↓
5. Agent updates plan.md and AGENTS.md before closing
```

## Why Specs Matter

Good specs help agents:
- Understand what "done" looks like
- Make fewer assumptions
- Stay focused on the right constraints
- Produce code you can actually use

Bad spec: "Build a timer app"

Good spec: See [`examples/new-apps/pomodoro-timer/spec.md`](examples/new-apps/pomodoro-timer/spec.md)

## Contributing

Have a spec that worked well? Share it! Open a PR with your example.

## Learn More

Background on this approach: [Agentic Coding In Practice](https://annjose.com/post/agent-coding-in-practice/)

## License

MIT