# Google Ads Skills for Claude

Agent Skills that teach Claude how to analyze, audit, optimize, and manage Google Ads accounts. Works with Claude Code, Claude.ai, and the Claude API.

## Skills

| Skill | What It Does | API Required? |
|---|---|---|
| **google-ads-analysis** | Campaign performance analysis, GAQL query patterns, anomaly detection, wasted spend identification | Yes (via MCP) |
| **google-ads-audit** | Structured 7-dimension account audit with severity ratings and 30/60/90-day action plans | Yes (via MCP) |
| **google-ads-write** | Safe write operations using Confirm-Execute-Postcheck (CEP) protocol — pause, bid, budget, keywords, ads | Yes (via MCP) |
| **google-ads-math** | PPC calculations — CPA, ROAS, budget projections, impression share opportunity, break-even analysis | No |
| **google-ads-mcp** | MCP server setup for live Google Ads API access via [google-ads-mcp](https://github.com/itallstartedwithaidea/google-ads-mcp) | Setup guide |

## Quick Start

### Claude Code

```bash
/plugin marketplace add itallstartedwithaidea/google-ads-skills
```

Then install a plugin:

```bash
/plugin install google-ads-full@google-ads-skills
```

Or just the read-only suite:

```bash
/plugin install google-ads-readonly@google-ads-skills
```

### Claude.ai

Upload any `SKILL.md` file from the `skills/` folder directly in your Claude.ai project settings.

### Claude API

Follow the [Skills API Quickstart](https://docs.claude.com/en/api/skills-guide#creating-a-skill) to attach skills programmatically.

## Plugins

| Plugin | Skills Included | Use Case |
|---|---|---|
| `google-ads-full` | All 5 skills | Full Google Ads management |
| `google-ads-readonly` | analysis, audit, math | Analysis only — no write access |
| `google-ads-mcp-only` | mcp | Just the MCP server setup |

## Live API Access

For live Google Ads API queries, connect the MCP server:

1. Install: `pip install git+https://github.com/itallstartedwithaidea/google-ads-mcp.git`
2. Configure credentials (see [google-ads-mcp skill](./skills/google-ads-mcp/SKILL.md))
3. Add `.mcp.json` to your project root

Without the MCP server, skills still work for:
- Math calculations (google-ads-math)
- Strategy and best practice advice (all skills)
- Analyzing data you paste into the conversation

## Write Safety

The `google-ads-write` skill enforces a **CEP protocol** (Confirm → Execute → Post-check):

1. **Confirm** — Claude shows exactly what will change and asks for explicit confirmation
2. **Execute** — Mutation runs only after you say "confirm"
3. **Post-check** — Claude verifies the change took effect and shows before/after

No write operation ever executes without your explicit approval.

## Related Projects

| Project | Description |
|---|---|
| [google-ads-mcp](https://github.com/itallstartedwithaidea/google-ads-mcp) | Python MCP server — 29 tools for Google Ads API |
| [google-ads-api-agent](https://github.com/itallstartedwithaidea/google-ads-api-agent) | Python agent with FastAPI deployment |
| [google-ads-gemini-extension](https://github.com/itallstartedwithaidea/google-ads-gemini-extension) | Gemini CLI extension with MCP server |
| [googleadsagent.ai](https://googleadsagent.ai) | Production system (Buddy) on Cloudflare |

## License

Apache 2.0 — See [LICENSE](./LICENSE)
