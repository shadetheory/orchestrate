# GitHub Portfolio Dashboard

Generate a comprehensive, visually organized dashboard of Jordan's GitHub activity.

## Instructions

Create a rich dashboard experience with clear sections. Use box-drawing characters and formatting to make it scannable.

### Data to Gather

```bash
# 1. Recent activity
gh api users/jordanpartridge/events --jq '.[0:15] | .[] | "\(.type)|\(.repo.name)|\(.created_at)"'

# 2. Open PRs by me
gh search prs --author jordanpartridge --state open --json repository,title,createdAt,url --limit 20

# 3. Open issues by me
gh search issues --author jordanpartridge --state open --json repository,title,url --limit 15

# 4. Priority project stats
gh repo view conduit-ui/conduit --json pushedAt,openIssues 2>/dev/null
gh repo view jordanpartridge/chat --json pushedAt,openIssues 2>/dev/null
```

### Output Format

```
╔══════════════════════════════════════════════════════════════════╗
║                    GITHUB DASHBOARD                               ║
║                    Generated: [timestamp]                         ║
╠══════════════════════════════════════════════════════════════════╣
║  QUICK STATS                                                      ║
║  ┌─────────────┬─────────────┬─────────────┬─────────────┐       ║
║  │ Open PRs    │ Open Issues │ Active Repos│ Stale Items │       ║
║  │     XX      │     XX      │     XX      │     XX      │       ║
║  └─────────────┴─────────────┴─────────────┴─────────────┘       ║
╠══════════════════════════════════════════════════════════════════╣
║  PRIORITY PROJECTS                                                ║
║  ├── conduit-ui/conduit     [last push: Xh ago] [X issues]       ║
║  ├── jordanpartridge/chat   [last push: Xh ago] [X issues]       ║
║  └── conduit-knowledge      [status]                              ║
╠══════════════════════════════════════════════════════════════════╣
║  OPEN PRs (need attention)                                        ║
║  │                                                                ║
║  ├─ PERSONAL                                                      ║
║  │  • [title] → repo (X days old)                                ║
║  │                                                                ║
║  ├─ WORK                                                          ║
║  │  • [title] → repo (X days old)                                ║
╠══════════════════════════════════════════════════════════════════╣
║  RECENT ACTIVITY (48h)                                            ║
║  • PushEvent → repo (time)                                        ║
║  • PullRequestEvent → repo (time)                                 ║
╠══════════════════════════════════════════════════════════════════╣
║  RECOMMENDATIONS                                                  ║
║  1. [Most urgent action]                                          ║
║  2. [Second priority]                                             ║
╚══════════════════════════════════════════════════════════════════╝
```

Separate WORK repos (PSTrax/*) from PERSONAL repos in the PR section.
Flag anything older than 7 days as needing attention.
