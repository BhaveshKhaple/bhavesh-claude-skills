# Graph Engineering: How I Stopped Writing Fragile AI Pipelines

*By Bhavesh Khaple · July 26, 2026*

---

Most people building AI agents make the same mistake I did.

They write a chain: prompt → step 1 → step 2 → step 3 → output. It works in the demo. It breaks in production. Step 1 emits something slightly off, step 2 compounds the error, and by step 3 you have confident-sounding garbage.

I spent weeks debugging pipelines that "should have worked." The root cause was always the same — **I was thinking in lines when I should have been thinking in graphs.**

This is what changed how I build.

---

## The Core Idea

There's a concept called **Loop Engineering** — popularized by Andrej Karpathy and amplified by @0xCodila — that says:

> Most people use AI the same way they used Google in 2005. Type something in, read what comes back, type again. The AI sits idle between prompts.

The better approach: keep the model in a loop. Let it think across multiple steps. Let it check its own work.

But loops alone aren't enough. Loops let agents *think*, but they forget everything between calls. They have amnesia.

The fix is **Graph Engineering** — structuring your agents not as a loop or a line, but as a graph where nodes can:

- Loop back and self-correct
- Branch to specialized sub-agents
- Call external tools and bring results back in
- Get scored against a rubric before output ships

> Core insight: **Loops let agents think. Graphs let agents remember.**

---

## The 5 Layers (Use Minimally)

Most articles on agentic AI oversell complexity. The framework below has 5 layers — **you almost never need all 5.** Start with layer 1 and layer 5. Add others only when a real failure demands them.

---

### Layer 1 — Reflection Loop

Agent generates a draft. A second prompt critiques it. Agent revises.

The cheapest intervention. One extra API call typically improves output quality by ~30%. The critic prompt must be specific — "make it better" adds noise, not signal.

```python
draft = agent.generate(task)
feedback = critic.evaluate(draft, rubric)
if feedback.issues:
    final = agent.revise(draft, feedback)
```

**Add when:** first drafts are almost-right but have a predictable, fixable flaw.
**Skip when:** output is deterministically verifiable by code.

---

### Layer 2 — Tool Use

Agent decides what external tool to call (search, code execution, database, MCP), calls it, and reads the result back.

Key design lesson: **narrow tools beat wide tools.** `search_papers(query, year)` produces reliable calls. `do_research(anything)` produces flaky routing.

**Add when:** the model needs current information or computation it can't do from parameters.

---

### Layer 3 — Planning

Agent writes an explicit, inspectable plan before executing anything.

Transformative for debugging. Separate planning from execution — catch bad plans *before* they cost tokens on execution. The plan also becomes an audit trail.

```json
{
  "goal": "Summarize competitor pricing changes this week",
  "steps": [
    { "id": 1, "action": "search_web", "query": "competitor pricing July 2026" },
    { "id": 2, "action": "extract_prices", "depends_on": [1] },
    { "id": 3, "action": "compare_to_baseline", "depends_on": [2] }
  ]
}
```

**Add when:** 3+ steps that must execute in order and mistakes are expensive.

---

### Layer 4 — Multi-Agent Coordination

Multiple agents, each with exactly one responsibility, working in sequence or parallel.

The rule I follow: **if one agent's system prompt has more than one verb, split it.**

Writer/Critic. Planner/Executor. Researcher/Synthesizer.

Do NOT add agents for the sake of it. N overlapping agents performs *worse* than 1 focused agent.

---

### Layer 5 — Critique Loop *(highest-leverage)*

A dedicated critic agent scores the output against an explicit rubric. Failures feed back into revision. Loop runs until pass OR max-iteration cap.

**This is the layer that matters most.** One critique pass is the highest-ROI intervention in the entire stack.

Hard rule: **the rubric must be concrete.** Not "is this good?" — that's a wish, not a rubric.

```json
{
  "dimensions": [
    { "name": "accuracy",     "check": "all claims verifiable", "weight": 0.4 },
    { "name": "clarity",      "check": "no jargon unexplained", "weight": 0.3 },
    { "name": "completeness", "check": "covers all sub-questions", "weight": 0.3 }
  ],
  "threshold": 0.85,
  "max_iterations": 3
}
```

Always set `max_iterations`. Production loops must have an exit.

---

## The Graph in Practice

Here's a real pipeline with layers 1, 2, and 5:

```
User Input
    │
    ▼
Tool: Search & Retrieve
    │
    ▼
Agent: Generate Draft ◄──────────┐
    │                            │
    ▼                            │
Critique vs Rubric          Revise (iter < 3)
    │
    ├── Score >= 0.85 ──► Final Output
    └── iter = 3      ──► Best Draft + Warning
```

No more straight lines. No more silent compounding errors.

---

## The Anti-Patterns

| Anti-Pattern | Why It Fails |
|---|---|
| All 5 layers on every task | Rube Goldberg machine. Most tasks need 2 layers. |
| Multi-agent when reflection would do | More agents = more bugs, cost, and debugging surface |
| Critique loop without a rubric | Loops forever, or accepts garbage confidently |
| Reflection prompt that says "improve this" | No idea what to look for. Random noise. |
| Unbounded loops | Always cap iterations. Always. |

---

## The Claude Skill

I turned this entire framework into a **reusable Claude skill** — a `/graph-engineering` slash command you can drop into any Claude Code or Runner workspace.

Invoke `/graph-engineering` on any multi-step agent task and it will:

1. Diagnose why your current chain is fragile
2. Pick only the layers you actually need (not all 5)
3. Produce a Mermaid graph of your workflow
4. Write a concrete critique rubric
5. Set your iteration cap

**Install:**

```bash
git clone https://github.com/BhaveshKhaple/bhavesh-claude-skills \
  ~/.runner/workspaces/my-workspace/skills/bhavesh-claude-skills
```

Then: `/graph-engineering`

**GitHub:** [BhaveshKhaple/bhavesh-claude-skills](https://github.com/BhaveshKhaple/bhavesh-claude-skills)

---

## Why I'm Sharing This

I'm building a public collection of Claude skills — practical, no-bloat, open source. Every skill solves one problem, tells you when NOT to use it, and ships the smallest solution that works.

More skills coming: eval design, RAG pipelines, Snowflake Cortex agents, MLOps evals.

Find me: [X @idkwhoisbhavesh](https://x.com/idkwhoisbhavesh) · [LinkedIn](https://linkedin.com/in/bhavesh-khaple)

---

*Credit: Andrew Ng (4 Agentic Patterns), Andrej Karpathy (Software 3.0), codila @0xCodila (Loop + Graph Engineering, Jul 2026)*
