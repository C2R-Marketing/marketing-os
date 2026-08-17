# Marketing OS

One skill. Fourteen modules. The full surface a marketer touches.

Built by tearing down the most-starred marketing skill repos on GitHub —
from 44K-star collections to 100-star craft pieces — keeping the structures
that worked, and adding the three things every one of them lacked: scores on
everything, artifacts instead of advice, and an explicit "what I couldn't
determine" in every report.

## What's inside

| Module | Covers |
|---|---|
| audit | Website/funnel audit → weighted 0-100 + prioritized fixes |
| geo | AI-search citability (ChatGPT, Perplexity, AI Overviews) |
| copy | Generate 15-20 variants → expert-panel score → de-slop |
| hooks | 18-tactic hook engine → hook matrix → diagnostic funnel |
| paid-ads | Concept-level fatigue diagnosis → ranked production brief |
| email | Welcome/nurture/launch sequences, written in full |
| social | LinkedIn/X posts that survive the feed |
| launch | Launch playbook incl. Product Hunt |
| positioning | Positioning, offer design, pricing strategy |
| competitive | Competitor teardowns from public sources |
| app-store | ASO diagnosis + metadata + screenshot sequences |
| analytics | Honest data reads, proper test design |
| + slop-patterns | The AI-tell catalogue, run on all prose |
| + rubrics/specs | Scoring bands, engine playbooks, store field rules |

Ads briefs don't stop at paper: if an ad-generation MCP is connected
(e.g. Arcads), the skill generates the briefed assets directly —
diagnose → brief → produce, in one session.

## Install

**Claude Code (one command):**

```
/plugin marketplace add Yuzzyuk/marketing-os
/plugin install marketing-os@marketing-os
```

**Claude (web/desktop):** Settings → Skills → + → upload `marketing-os.zip`
from the [latest release](../../releases/latest). Requires code execution enabled.

**Manual / Codex / Cursor / other agents:** copy `skills/marketing-os/` into
your agent's skills directory (e.g. `~/.claude/skills/marketing-os/`).

## First five minutes

Copy `brand-context.template.md` → `brand-context.md`, fill it in, drop it in
your project root or `.claude/`. Every module reads it. Skip this and the
output is competent and interchangeable — the one thing marketing can't be.

## Design principles

- **Progressive disclosure**: the router loads first (~2k tokens); each task
  loads only its module. Fourteen modules cost nothing until used.
- **Subagent-native**: multi-dimensional work (audits, teardowns, variant
  generation) fans out in parallel when the host supports it.
- **No executable code.** Pure markdown. Nothing to review before trusting it.
- **Honesty spine**: no invented proof, no fake precision, no winners declared
  on ten conversions, and every score labeled as the heuristic it is.

MIT.
