---
name: "LinkedIn Hook Writer"
description: "Write LinkedIn posts that actually get distributed. Generates hooks in the 5 formats that earn the see-more click on the 360 Brew algorithm, respects mobile pixel-width, and structures the body for maximum dwell time. Use when drafting any LinkedIn post."
category: content
---

# LinkedIn Hook Writer

> **Invoke this skill whenever the user is writing, editing, or planning a LinkedIn post.**
> The goal: turn any raw insight into a post whose first 40-50 words earn distribution — because that's all LinkedIn's algorithm reads before deciding your fate.

---

## The One Fact That Governs Everything

LinkedIn's ranking model (internally called **360 Brew**) reads only the **first 40-50 words** of a post — roughly the two lines visible above "see more" on mobile — before deciding whether to push it to feeds.

If those words fail:
- The reader doesn't click see-more → no dwell time signal
- The algorithm doesn't distribute → no reach
- Everything under the fold is dead weight

Every other rule in this skill is downstream of this one.

---

## Hard Rules

1. **Pixel width, not character count.** LinkedIn renders by pixels. "W" is ~4x wider than "i". Budget is **~110 width units per mobile line**. Never trust a "150 characters" limit.
2. **One post = one idea.** Multiple ideas dilute attention. Pick the sharpest angle.
3. **Never open with "I'm excited to announce"**, "Just wanted to share", or any throat-clearing verb. The algorithm deprioritizes these.
4. **The hook opens a gap** between what the reader expects and what you claim. Gap = curiosity = click. Format is just packaging.
5. **The first 45 minutes decides reach.** If <30 engagements happen in that window, the algorithm caps distribution. Plan for this before posting.
6. **No emojis at start.** 2022 tactic — now a "trying too hard" signal.
7. **Hashtags are decorative.** They no longer weight distribution meaningfully. 0-3 max.

---

## The 5 Hook Formats

Use exactly one. Never blend two accidentally.

### Format 1 — Dense
Fill every pixel above see-more. No breaks. Continuous packed text.
Use when the tension needs context to land (data point, story setup, complex claim).

```
Example:
I spent 6 months building an AI feature that shipped last week. It generated $0 in revenue. Here's what my
```
(cuts at see-more with the tension unresolved)

### Format 2 — Punchy + Context  *(highest hit rate, safest default)*
Short hard line → blank line → context line.

```
Example:
Your LinkedIn hook is your algorithm gate.

40 words decide whether 40,000 people see your post.
```

Structure = contrarian claim, beat, stakes. The blank line does real work — it forces the eye to pause.

### Format 3 — Single-Line Bomb
One sentence loaded with enough tension to earn the click alone.
Highest variance — lands harder than any other format when it works, dies completely when it doesn't.

**Technical trap:** MUST insert two manual blank line breaks after the sentence. Without them the next line pulls up mobile-side and the bomb effect disappears.

```
Example:
Most LinkedIn advice is written by people who peaked in 2022.


(rest of post starts here)
```

### Format 4 — Stacked
2-4 short parallel lines with breaks between them. Symmetry does the work — the brain finishes the rhythm.

```
Example:
2024: I posted daily.
2025: I stopped posting.
2026: I get more DMs than ever.
```

Best for: before/after, timelines, "3 things I regret", escalating numbers, contrasts.

### Format 5 — Hybrid
Custom mix. **Do not use until the four above are second nature.**

---

## The Underlying Curiosity Engine

Every viable hook opens one of these gaps:

| Gap Type | Trigger | Example Frame |
|---|---|---|
| Prediction gap | Reader expects X, you claim Y | "Extroverts make the best leaders. Harvard disagrees." |
| Identity gap | Calls out a specific self-image | "If you're an ML engineer applying to jobs in 2026..." |
| Backstory gap | Sets up a story mid-arc | "I got fired 3 weeks before my daughter was born." |
| Number gap | Specific figure that demands explanation | "I fine-tuned a model to 97.77% val accuracy. Here's what broke first." |
| Contrarian gap | Directly opposes a known belief | "Posting daily is the worst LinkedIn advice ever given." |

If the hook does not open a gap, no format will save it.

---

## The 6-Step Workflow

When invoked, follow this order.

### Step 1 — Extract the core insight
Ask the user (or infer from the paste): what is the single most non-obvious thing you know about this topic? Not the surface claim — the earned observation.

Prompt to ask if unclear: *"What did you learn that most people in your space still get wrong?"*

### Step 2 — Give it an angle
Turn the insight into one specific idea. If it can be summarized in two clauses ("X, but Y"), it's ready. If it needs three, it's still two posts pretending to be one.

### Step 3 — Choose the hook format
Default to **Punchy + Context** unless one of these applies:
- Complex setup needed → Dense
- One-line takedown ready → Single-Line Bomb
- Timeline / contrast / list-of-3 → Stacked

### Step 4 — Draft 3 hook variants
Never hand back one. Always three. Vary the gap type across the three so the user can feel which lands.

### Step 5 — Structure the body
- **First line under the hook** must deliver on the hook's promise. No detour.
- **One line = one thought.** Aggressive line breaks. Never a wall of prose.
- **Skimmable framework:** Problem-Agitate-Solution, Before-After-Bridge, or numbered list.
- **Short words. Short sentences.** Reading level ~grade 6.
- **End with a CTA** tightly coupled to the post subject. Not "join my newsletter" — offer a lead magnet that matches the topic (e.g., post on eval harnesses → "Want my eval rubric template? Comment 'eval' and I'll DM it.").

### Step 6 — Validate before shipping

Checklist:
- [ ] Hook is under ~110 pixel-width units per mobile line (test in a LinkedIn preview tool, not by counting chars)
- [ ] Blank line spacing renders correctly (especially for Single-Line Bomb — needs 2 manual breaks)
- [ ] One idea, not two
- [ ] No AI tells (see below)
- [ ] Image or carousel attached if the post is a "value" post — infographic dramatically boosts distribution
- [ ] Post is scheduled for Tue-Thu, 8-10am target-audience-timezone (peak engagement window)
- [ ] Have 5-10 people primed to engage within 45 minutes

---

## AI-Tell Patterns to Strip Before Posting

LinkedIn actively demotes AI-sounding content (~94% of the time per public statements). Remove these before every post:

1. **"It's not X, it's Y" contrastive framing** — LinkedIn named this as a demotion trigger. Delete every one.
2. **Em dashes (`—`)** — strongest AI signal. Max 1 per post, ideally 0. Replace with commas, colons, or rewrites.
3. **Repeated sentence openers** — no 3+ sentences starting the same way.
4. **Staccato chains** — no runs of short punchy sentences back-to-back. Vary sentence length.
5. **Vague impact claims** — "highly skilled in X" → replace with a specific project or number.
6. **Transition filler** — "Furthermore," "Moreover," "It is worth noting," "In conclusion" — cut all.
7. **Hollow closings** — "I look forward to hearing your thoughts" → one specific ask or nothing.
8. **Symmetrical sentence pairs** — "I build fast. I ship clean." → break the symmetry.

Read the draft aloud in your head. If it sounds like a LinkedIn post generator, rewrite.

---

## The Engagement Machine (post-publish)

Publishing is only half the work. The other half is triggering the algorithm's 45-minute velocity check.

**Minimum viable engagement pod:**
- 5-10 people who reliably engage within 45 min of publish
- They comment (not just like) — comments weight ~2x
- They avoid identical wording (algorithm detects pod patterns)

**Ranked signal strength for the algorithm:**
1. **Reposts** (3x weight — strongest amplifier)
2. **Comments with replies** (2x weight — dwell time signal)
3. **See-more clicks** (dwell time)
4. **Likes** (1x — weakest signal)

**CTA that maximizes signal:** Ask for a specific comment ("Reply 'RAG' and I'll DM the doc"). This forces comments (not just likes) and creates a DM funnel that also builds relationship signal.

---

## The 4 Content Categories That Compound

Not every post should chase reach. Balance across:

| Type | Purpose | Frequency |
|---|---|---|
| **Growth post** | Broad-reach viral hook, big idea, contrarian take | 1-2x/week |
| **Authority post** | Deep-dive on your niche — the *how*, not the *what* | 2-3x/week |
| **Conversion post** | Direct offer, case study, testimonial, lead magnet | 1x/week |
| **Personal post** | Story, background, values — humanizes the brand | 1x/week |

Post 5-6x/week total. Consistency > perfection.

---

## Hook Templates (Copy-Paste Ready)

### For AI/ML/Engineering (matches Bhavesh's positioning)
- `"I fine-tuned [model] to [specific metric]. Here's what broke first."`
- `"Everyone's shipping AI agents. Nobody's shipping the eval harness."`
- `"[Common ML belief]. Wrong. Here's the actual failure mode:"`
- `"I studied [N] production LLM systems. [Surprising pattern]."`

### For Career / Job Search (per user memory: no placement-cell content)
- `"I applied to [N] AI/ML roles in [timeframe]. Here's what actually got replies."`
- `"[Timeframe] ago I couldn't [skill]. Today [outcome]. What changed:"`
- `"The [industry] hiring bar just shifted. Most candidates haven't noticed."`

### For Build-in-Public
- `"[Product name] launched [timeframe] ago. [Specific metric]. Here's what surprised me:"`
- `"I tried building [thing] with [tool]. It failed. Here's why that was the point:"`

### For Contrarian Takes
- `"Everyone says [conventional wisdom]. I've built [N] systems and here's what actually happens:"`
- `"The most dangerous advice in [space] right now: [belief]."`

---

## What Not To Post

Based on r/LinkedInLunatics and r/marketing sentiment:

- **Humblebrag transformations** — "I forgot my laptop, so I wrote code on paper, and here's what it taught me about leadership"
- **Generic vulnerability posts** — "here's what my [life event] taught me about [SaaS metric]"
- **"Solution mode + reflection" template posts** — instantly recognized as LinkedIn cringe
- **Motivational quote + irrelevant photo**
- **"Excited to announce..."** anything
- **Reposts of your own reposts** — kills your account's authority signal

The reader can smell formulaic content in 0.3 seconds. Better to post nothing than to post cringe.

---

## Skill Invocation Pattern

When the user says any of:
- "Write me a LinkedIn post about..."
- "Help me draft a LinkedIn hook for..."
- "This flopped, rewrite it..."
- "Turn this into a LinkedIn post..."
- "What should I post about [topic]?"

→ Load this skill. Ask clarifying questions from Step 1 if the insight isn't clear. Return 3 hook variants + a structured body draft + a validation checklist result.

---

## Sources

Synthesized from:
- Pierre Herubel (30M LinkedIn views/year, 100K+ view post breakdowns)
- Diandra Escobar (131-hook study across 21 currently-growing creators, 5 hook formats)
- Matt Gray (846K followers, 59M organic views/month, 24M-view single post)
- Reddit r/marketing + r/LinkedInLunatics (what to avoid)
- LinkedIn's public statements on AI-content demotion (~94% demoted)

Research date: July 2026.
