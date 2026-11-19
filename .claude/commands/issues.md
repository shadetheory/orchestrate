# Issues Dashboard

Show all open issues organized by project.

## Instructions

```bash
gh search issues --author shadetheory --state open --json repository,title,url,createdAt --limit 30
```

## Output Format

```
╔══════════════════════════════════════════════════════════════════╗
║                        OPEN ISSUES                                ║
╠══════════════════════════════════════════════════════════════════╣
║  📦 CHAT (shadetheory/chat)                                   ║
║  ├── #X [title]                                                   ║
║  ├── #X [title]                                                   ║
╠──────────────────────────────────────────────────────────────────╣
║  📦 FINANCES (shadetheory/finances)                           ║
║  ├── #X [title]                                                   ║
╠──────────────────────────────────────────────────────────────────╣
║  📦 THE-SHIT/CORE                                                 ║
║  ├── #X [title]                                                   ║
╠──────────────────────────────────────────────────────────────────╣
║  SUMMARY                                                          ║
║  Total: XX issues across XX repos                                 ║
║  Oldest: [issue] (XX days)                                        ║
╚══════════════════════════════════════════════════════════════════╝
```

Flag issues older than 30 days as potentially stale.
Suggest which could be closed vs still relevant.
