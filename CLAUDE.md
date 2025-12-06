# Orchestrate: AI-Powered GitHub Portfolio Management

This project demonstrates Claude Code agents managing a complex GitHub portfolio - turning chaos into clarity.

## IMPORTANT: Agent-First Development

**ALWAYS use agents for tasks. ALWAYS think parallel.**

### Mandatory Agent Usage

| Task | Agent | Never Do Directly |
|------|-------|-------------------|
| Git commits | `git-commit-manager` | Don't run git commands manually |
| GitHub scanning | `github-context` | Don't run gh commands one at a time |
| Code exploration | `Explore` | Don't grep/glob manually for open-ended searches |
| Multi-repo analysis | `general-purpose` (parallel) | Don't analyze repos sequentially |

### Parallel Strategy

When analyzing multiple repos/items, **ALWAYS spawn parallel agents**:

```
# BAD: Sequential
for repo in repos:
    analyze(repo)

# GOOD: Parallel agents
Task(agent="general-purpose", prompt="Analyze repo1", background=true)
Task(agent="general-purpose", prompt="Analyze repo2", background=true)
Task(agent="general-purpose", prompt="Analyze repo3", background=true)
# ... then gather results
```

**Rule of thumb**: If you can do 10 things at once, DO 10 things at once.

### Examples

**Analyzing issues across repos:**
```
# Spawn one agent per repo
Agent 1: "Analyze issues in conduit-ui/conduit"
Agent 2: "Analyze issues in jordanpartridge/chat"
Agent 3: "Analyze issues in jordanpartridge/finances"
# All run simultaneously, synthesize results after
```

**Committing code:**
```
# ALWAYS delegate to git-commit-manager
Task(agent="git-commit-manager", prompt="Commit the changes we made to CLAUDE.md and slash commands")
```

---

## What This Project Does

**Orchestrate** is both a tool and a showcase:
1. **Manages Jordan's 50+ GitHub repos** using AI agents
2. **Documents the journey** from scattered projects to focused impact
3. **Demonstrates agent patterns** for others to learn from

## The GitHub Portfolio Being Orchestrated

### Priority Projects (Active Focus)
- `conduit-ui/conduit` - Developer Liberation Platform (Laravel Zero CLI)
- `conduit-knowledge` - AI-powered codebase understanding
- `jordanpartridge/chat` - Multi-model AI chat (Laravel 12 + Vue 3)

### Infrastructure (Maintained)
- `github-client` - Laravel GitHub API wrapper (Saloon-based)
- `strava-client` - Fitness API integration
- `spotify-client` - Music API for developer wellbeing

### Component Ecosystem
- `conduit-spotify`, `conduit-docker`, `conduit-knowledge`, `conduit-env-manager`

## Slash Commands

- `/dashboard` - Visual GitHub activity dashboard
- `/focus` - Show only priority project status
- `/stale` - Find PRs and issues needing attention
- `/conduit` - Conduit ecosystem deep dive
- `/prs` - All open PRs organized by urgency
- `/issues` - All open issues by project
- `/analyze` - Multi-agent portfolio analysis

## Agent Architecture

This project uses specialized Claude Code agents:
- **git-commit-manager** - All git operations (commits, branches)
- **github-context** - Scans activity across repositories
- **github-orchestrator** - Comprehensive GitHub management
- **Explore** - Deep dives into codebases
- **general-purpose** - Complex multi-step analysis (use for parallel work)

## The Vision

> "Use AI to fade out the background noise"

Not just project management - **developer wellbeing intelligence**:
- Understand work patterns (commits, PRs, activity)
- Understand context (time of day, music, energy)
- Gentle nudges when patterns suggest burnout
