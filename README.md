# ai-procurement-decision-landing

Static landing site for the **[AI Procurement Decision Card spec](https://github.com/mizcausevic-dev/ai-procurement-decision-spec)** — a cross-cutting, buyer-side spec in the twelve-spec [Kinetic Gain Protocol Suite](https://github.com/mizcausevic-dev/kinetic-gain-protocol-suite).

Live at **[decisions.kineticgain.com](https://decisions.kineticgain.com)**.

## What's here

```
.
├── index.html              # the landing page
├── style.css               # styles (indigo + slate palette)
├── .github/workflows/
│   └── deploy.yml          # FTPS push to /decisions/ on Hostinger on push to main
└── README.md
```

No build step. Hand-written HTML + CSS so the page loads instantly and degrades cleanly without JS.

## Local preview

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Deployment

Pushes to `main` trigger a GitHub Actions workflow that FTP-syncs the site root to `/decisions/` on Hostinger.

Required repo secrets:

| Secret | Description |
|---|---|
| `FTP_HOST` | Hostinger FTP server hostname |
| `FTP_USER` | Hostinger FTP username |
| `FTP_PASS` | Hostinger FTP password |

(Same values as every other landing repo in the Suite.)

## Related repositories

- **[ai-procurement-decision-spec](https://github.com/mizcausevic-dev/ai-procurement-decision-spec)** — the specification, JSON Schema, and three canonical example fixtures (EdTech district, HealthTech hospital, Federal agency)
- **[procurement-decision-api](https://github.com/mizcausevic-dev/procurement-decision-api)** — FastAPI service that drafts Decision Cards from a buyer rubric + vendor Suite documents
- **[policy-as-code-engine](https://github.com/mizcausevic-dev/policy-as-code-engine)** — translates a Decision Card's `conditions[]` into a PolicyBundle; live request gating requires a separately deployed trusted policy path
- **[incident-correlation-rs](https://github.com/mizcausevic-dev/incident-correlation-rs)** — walks the Suite graph from an AI Incident Card, recommends Decision Card re-reviews
- **[mcp-decision-intelligence](https://github.com/mizcausevic-dev/mcp-decision-intelligence)** — read-only MCP server, 4 deterministic preview tools
- **[mcp-kinetic-gain](https://github.com/mizcausevic-dev/mcp-kinetic-gain)** — v0.10.0 unified MCP server with 75 tools covering twelve Suite specs, DefenseTech checks, and implementation previews
- **[kinetic-gain-visualizer](https://github.com/mizcausevic-dev/kinetic-gain-visualizer)** — unified visualizer; auto-detects via `decision_card_version`

## License

Apache-2.0 for this site. The underlying specification is MIT-licensed; reference implementations carry their own licenses.
