# Focus Mode: Priority Projects Only

Show status of ONLY the priority projects, filtering out all noise.

## Priority Projects

1. **conduit-ui/conduit** - The platform
2. **shadetheory/conduit-knowledge** - The differentiator
3. **shadetheory/chat** - The AI layer

## Instructions

Gather focused data:

```bash
# Conduit core
gh repo view conduit-ui/conduit --json pushedAt,openIssues
gh pr list --repo conduit-ui/conduit --state open --json title,url,createdAt --limit 5
gh issue list --repo conduit-ui/conduit --state open --limit 5

# Conduit knowledge
gh repo view shadetheory/conduit-knowledge --json pushedAt,openIssues 2>/dev/null || echo "Check repo status"

# Chat
gh repo view shadetheory/chat --json pushedAt,openIssues
gh pr list --repo shadetheory/chat --state open --json title,url --limit 5
gh issue list --repo shadetheory/chat --state open --limit 5
```

## Output Format

```
## Focus Mode: What Matters Now
Generated: [timestamp]

### Conduit (The Platform)
Last activity: [time]
Open PRs: [list]
Open Issues: [list]
Next action: [recommendation]

### Conduit-Knowledge (The Differentiator)
Status: [active/needs-work/missing]
Next action: [recommendation]

### Chat (The AI Layer)
Last activity: [time]
Open PRs: [list]
Open Issues: [list]
Next action: [recommendation]

---
Everything else is background noise. Stay focused.
```
