# Agentic Coding - Specs & Plans

A collection of skills, specifications, and plans for building software with AI coding agents.

## What This Is

This repo provides:

- Agent onboarding skills (starting with `agentify-repo`) to prepare repositories for effective agent work.
- Templates for writing clear specs.
- Real examples of specs and plans that work well with AI agents.

**The key insight:** Clear specs with specific success criteria produce better results than vague instructions.

## What's Inside
```
agentic-coding/
├── skills/
│   └── agentify-repo/      # Skill to prepare repos so agents can work effectively
├── specs/
│   ├── templates/           # Spec templates
│   └── examples/            # Example specs
└── plans/
    ├── templates/           # Plan templates
    └── examples/            # Example plans
```

## Start Here: Agentify a Repo

Use the `agentify-repo` skill first when onboarding a repository for AI coding agents.

- Skill path: `skills/agentify-repo/SKILL.md`
- Purpose: prepare a repo so agents can work effectively
- Outcome: repo-specific `AGENTS.md` and supporting docs grounded in real repo evidence

Use this when you need to bootstrap or refresh agent-facing docs before implementation work.

## Using This Repo

After agentifying a repo, use `specs/` and `plans/` to draft and execute work:

- Clear objectives and success criteria
- Specific UI/UX requirements with examples
- Edge cases and constraints spelled out
- Tech stack and integration points defined

Copy what works for your project. Adapt to your needs.

### Specs

##### New App
Use `specs/templates/app-spec-template.md` when building something from scratch.

#### Feature Enhancement  
Use `specs/templates/feature-spec-template.md` when adding to existing code.

Replace `[placeholders]` with your specifics. Delete sections that don't apply.

### Spec Examples

Real specs from actual projects. Use these as reference for structure and level of detail.

- **new-apps/pomodoro-timer** - Complete web app spec
- **new-features/pomodoro-statistics** - Feature added to existing app

## Workflow
```
1. Write spec.md (use `specs/templates/` as reference)
   ↓
2. Use `agentify-repo` to bootstrap or refresh agent-facing repo docs
   ↓
3. Give spec to agent → agent creates plan.md
   ↓
4. Review/edit plan.md
   ↓
5. Agent executes plan step by step
   ↓
6. Agent updates plan.md and AGENTS.md before closing
```

## Why Specs Matter

Good specs help agents:
- Understand what "done" looks like
- Make fewer assumptions
- Stay focused on the right constraints
- Produce code you can actually use

Bad spec: "Build a timer app"

Good spec: See [`specs/examples/new-apps/pomodoro-timer-spec.md`](specs/examples/new-apps/pomodoro-timer-spec.md)

## Contributing

Have a spec that worked well? Share it! Open a PR with your example.

## Learn More

Background on this approach: [Agentic Coding In Practice](https://annjose.com/post/agent-coding-in-practice/)

## License

MIT
