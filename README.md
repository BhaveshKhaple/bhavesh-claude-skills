# bhavesh-claude-skills

> A growing collection of production-ready Claude / Runner skills by [Bhavesh Khaple](https://github.com/BhaveshKhaple).
> Free to use, fork, and adapt. If you build on these, a mention is appreciated but not required.

---

## What Are Claude Skills?

Skills are slash-command instructions that extend Claude Code and Runner with domain-specific knowledge. Drop a `SKILL.md` into your workspace and invoke it with `/skill-name` — Claude gets the full context injected before it responds.

Think of them as reusable "expert modes" you can invoke on demand.

---

## Skills in This Repo

### `/graph-engineering` — Agent Workflow Design

> Design resilient multi-step LLM/agent workflows using the loops-and-graphs pattern.

**Invoke when:** you're building any multi-step LLM pipeline and would otherwise write a fragile `step1 → step2 → step3` chain.

**Covers 5 layers:**

| Layer | What it does | When to add it |
|---|---|---|
| 1. Reflection | Agent critiques its own draft | Almost-right first drafts |
| 2. Tool Use | Agent calls external tools/APIs | Needs fresh data or computation |
| 3. Planning | Explicit plan before execution | ≥3 steps, order matters |
| 4. Multi-Agent | Split roles across specialist agents | One agent doing too many jobs |
| 5. Critique Loop | Rubric-based revision cycle | Quality > latency |

**Core insight:** *Loops let agents think. Graphs let agents remember.*

[→ Full skill docs](./graph-engineering/SKILL.md)

---

## Installation

### Runner (recommended)

```bash
# Clone into your workspace skills folder
git clone https://github.com/BhaveshKhaple/bhavesh-claude-skills \
  ~/.runner/workspaces/my-workspace/skills/bhavesh-claude-skills

# Or copy a single skill
cp -r bhavesh-claude-skills/graph-engineering \
  ~/.runner/workspaces/my-workspace/skills/graph-engineering
```

Then invoke in Runner: `/graph-engineering`

### Claude Code (CLI)

```bash
# Per-project
cp -r graph-engineering /path/to/project/.claude/skills/

# Global
cp -r graph-engineering ~/.claude/skills/
```

Then invoke: `/graph-engineering`

---

## Skill Format

Each skill follows the standard Claude Code `SKILL.md` format — fully compatible between Claude Code CLI and Runner:

```
skill-name/
├── SKILL.md       ← instructions injected into Claude's context
├── icon.svg       ← shown in Runner UI
└── README.md      ← (optional) extended docs
```

---

## Roadmap

Skills I'm planning to add as I build them:

- [ ] `/agent-critique-loop` — standalone layer-5 rubric builder
- [ ] `/mlops-eval` — LLM evaluation design (Hamel Husain / HELM patterns)
- [ ] `/rag-pipeline` — retrieval-augmented generation design
- [ ] `/snowflake-cortex-agent` — Snowflake-native agent stack (Cortex MCP)
- [ ] `/loop-engineering` — single-prompt loop optimization (Karpathy method)

---

## Philosophy

**No bloat.** Every skill in this repo:
- Solves one specific problem
- Tells you when **not** to use it (anti-patterns section mandatory)
- Has a concrete output format so you know what to expect
- Ships the smallest solution that works

---

## Contributing

Found a bug? Have a skill to add? PRs and issues welcome.

When submitting a skill, include: problem it solves, when to skip it, and an anti-patterns section.

---

## Credits

Skill concepts draw from:
- [Andrew Ng's 4 Agentic Design Patterns](https://www.deeplearning.ai/the-batch/how-agents-can-improve-llm-performance/)
- [Andrej Karpathy — Software 3.0 framing](https://x.com/karpathy)
- [codila (@0xCodila)](https://x.com/0xCodila) — Loop Engineering (Jul 1 2026) + Graph Engineering (Jul 21 2026)

---

## License

MIT — use freely, commercially or otherwise. Attribution appreciated but not required.

---

*Made by [Bhavesh Khaple](https://github.com/BhaveshKhaple) · [LinkedIn](https://www.linkedin.com/in/bhavesh-khaple) · [X/Twitter](https://x.com/idkwhoisbhavesh)*
