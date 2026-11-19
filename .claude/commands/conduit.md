# Conduit Ecosystem Dashboard

Deep dive into the Conduit project family - your priority focus.

## Instructions

Gather data on all Conduit-related repos:

```bash
# Main platform
gh repo view conduit-ui/conduit --json description,pushedAt,stargazerCount,openIssues
gh pr list --repo conduit-ui/conduit --state open --json title,url,createdAt --limit 10
gh issue list --repo conduit-ui/conduit --state open --limit 10

# Component ecosystem
gh repo list shadetheory --json name,description,pushedAt | jq '.[] | select(.name | startswith("conduit-"))'

# Related orgs
gh repo list conduit-ui --json name,description,pushedAt 2>/dev/null
```

## Output Format

```
╔══════════════════════════════════════════════════════════════════╗
║              🔓 CONDUIT ECOSYSTEM STATUS                          ║
║              "Developer Liberation Platform"                      ║
╠══════════════════════════════════════════════════════════════════╣
║  CORE PLATFORM: conduit-ui/conduit                                ║
║  ┌────────────────────────────────────────────────────────────┐  ║
║  │ Stars: X  │  Last Push: X ago  │  Open Issues: X          │  ║
║  └────────────────────────────────────────────────────────────┘  ║
║                                                                   ║
║  Open PRs:                                                        ║
║  • [title] (X days)                                              ║
║                                                                   ║
║  Open Issues:                                                     ║
║  • [title]                                                        ║
╠══════════════════════════════════════════════════════════════════╣
║  COMPONENTS                                                       ║
║  ┌──────────────────┬─────────────────┬──────────────┐           ║
║  │ Component        │ Last Activity   │ Status       │           ║
║  ├──────────────────┼─────────────────┼──────────────┤           ║
║  │ conduit-knowledge│ [date]          │ 🟢 Active    │           ║
║  │ conduit-spotify  │ [date]          │ 🟡 Stale     │           ║
║  │ conduit-docker   │ [date]          │ 🟡 Stale     │           ║
║  │ conduit-env-mgr  │ [date]          │ 🟢 Active    │           ║
║  └──────────────────┴─────────────────┴──────────────┘           ║
╠══════════════════════════════════════════════════════════════════╣
║  NEXT ACTIONS                                                     ║
║  1. [Most important thing for Conduit right now]                 ║
║  2. [Second priority]                                             ║
║  3. [Third priority]                                              ║
╚══════════════════════════════════════════════════════════════════╝
```

Mark components as:
- 🟢 Active (pushed in last 30 days)
- 🟡 Stale (30-90 days)
- 🔴 Dormant (>90 days)
