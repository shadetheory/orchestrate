# PR Dashboard

Show all open PRs organized by status and urgency.

## Instructions

```bash
gh search prs --author shadetheory --state open --json repository,title,createdAt,url,isDraft
```

## Output Format

```
╔══════════════════════════════════════════════════════════════════╗
║                      PULL REQUESTS                                ║
╠══════════════════════════════════════════════════════════════════╣
║  🔴 NEEDS ATTENTION (>7 days old)                                 ║
║  ├── [title]                                                      ║
║  │   └─ repo • XX days old • [url]                               ║
╠──────────────────────────────────────────────────────────────────╣
║  🟡 IN PROGRESS                                                   ║
║  ├── [title]                                                      ║
║  │   └─ repo • X days old                                        ║
╠──────────────────────────────────────────────────────────────────╣
║  📝 DRAFTS                                                        ║
║  ├── [title]                                                      ║
║  │   └─ repo                                                      ║
╠──────────────────────────────────────────────────────────────────╣
║  SUMMARY                                                          ║
║  Total: XX | Stale: XX | Drafts: XX | Ready to merge: XX         ║
╚══════════════════════════════════════════════════════════════════╝
```

Group by:
- WORK (PSTrax/*)
- CONDUIT (conduit-ui/*, conduit-*)
- PERSONAL (everything else)
