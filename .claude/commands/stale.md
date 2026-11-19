# Stale Items Report

Find PRs and issues that have gone stale and need attention or closure.

## Instructions

Search for stale items:

```bash
# PRs older than 30 days
gh search prs --author shadetheory --state open --json repository,title,url,createdAt | jq '[.[] | select(.createdAt < (now - 2592000 | strftime("%Y-%m-%dT%H:%M:%SZ")))]'

# All open PRs to check age
gh search prs --author shadetheory --state open --limit 25 --json repository,title,createdAt,url

# Issues that might be stale
gh search issues --author shadetheory --state open --limit 25 --json repository,title,createdAt,url
```

## Output Format

```
## Stale Items Report
Generated: [timestamp]

### Stale PRs (>30 days old)
These need action: merge, close, or update

| PR | Repo | Age | Action Needed |
|----|------|-----|---------------|
| [title] | [repo] | X days | [merge/close/update] |

### Stale Issues (>60 days old)
Consider closing or updating

| Issue | Repo | Age | Recommendation |
|-------|------|-----|----------------|
| [title] | [repo] | X days | [close/still-relevant] |

### Quick Actions
- Close these now: [list]
- Need review: [list]
- Still relevant: [list]
```
