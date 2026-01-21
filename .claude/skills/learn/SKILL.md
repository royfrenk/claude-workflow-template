---
name: learn
description: Pause development to explain a concept in depth. Use when the user wants to understand something we're working on - architecture patterns, code decisions, technologies, or debugging approaches. Provides three-level explanations from core concept to deep dive.
user_invocable: true
---

# Learning Mode

Pause development. The user wants to understand something we're working on.

## Target Audience

Technical PM with mid-level engineering knowledge. Understands architecture, can read code, ships production apps. Not a senior engineer, but not a beginner either.

## Philosophy

80/20 rule - focus on concepts that compound. Don't oversimplify, but prioritize practical understanding over academic completeness.

## How to Use

When invoked with `/learn [concept]`, explain the concept using the three-level structure below.

If no concept is specified, ask: "What would you like to learn about? I can explain something from our current work, or a general concept."

## Three-Level Explanation Structure

Present each level, then pause to let the user absorb before offering the next level.

---

### Level 1: Core Concept

Answer these questions:
- **What is this?** One-sentence definition
- **Why does it exist?** The problem it solves
- **When would you use it?** The trigger that makes you reach for this pattern
- **Where does it fit?** How it connects to the broader architecture

Keep this to 4-6 sentences. Use an analogy if it helps.

After Level 1, ask: *"Does this make sense so far? Want me to go deeper into how it actually works?"*

---

### Level 2: How It Works

Cover:
- **The mechanics** - What happens under the hood
- **Key tradeoffs** - Why we chose this approach over alternatives
- **Failure modes** - What breaks and how you'd notice
- **Debugging tips** - How to investigate when something goes wrong

Use concrete examples from the current codebase when possible. Reference specific files.

After Level 2, ask: *"Want the deep dive? I can cover performance implications, edge cases, and the senior engineer perspective."*

---

### Level 3: Deep Dive

Cover:
- **Implementation details** that affect production behavior
- **Performance implications** and scaling considerations
- **Related patterns** and when to use alternatives instead
- **The "senior engineer" take** - nuances, war stories, things that bite you

This level can be longer. Include code snippets if relevant.

---

## Tone Guidelines

- Peer-to-peer, not teacher-to-student
- Technical but not jargon-heavy
- Concrete examples over abstract explanations
- Acknowledge complexity honestly: "this is genuinely tricky because..."
- If something has a controversial or nuanced answer, say so

## After Explaining

Ask if they want to:
1. Apply this concept to something in the codebase
2. Learn a related concept
3. Return to what we were building

Log the concept to `references/concepts-learned.md` so we can reference it later.
