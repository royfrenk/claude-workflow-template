# Claude Workflow Template

A structured development workflow for Claude Code projects with an Engineering Manager, Developer, and Reviewer agent system.

## Quick Start

### Option 1: Use as GitHub Template
1. Click "Use this template" on the GitHub repo
2. Clone your new repo
3. Update `docs/PROJECT_STATE.md` and `docs/roadmap.md` for your project

### Option 2: Copy to Existing Project
```bash
cp -r ~/templates/claude-workflow/.claude /path/to/your/project/
cp -r ~/templates/claude-workflow/docs /path/to/your/project/
```

## Structure

```
.claude/
├── agents/
│   ├── eng-manager.md   # Coordinates workflow, owns roadmap
│   ├── developer.md     # Implements features, deploys to staging
│   └── reviewer.md      # Reviews code, approves staging deploys
└── skills/
    └── tech-concept-teacher/
        ├── SKILL.md              # Explains technical concepts
        └── references/
            └── knowledge-base.md # Growing glossary of concepts

docs/
├── PROJECT_STATE.md     # Current status, known issues, key files
└── roadmap.md           # Sprint planning and task tracking
```

## Workflow

```
Product Owner (You)
       |
       v
Engineering Manager - coordination, specs, roadmap
       |
       v
Developer <--> Reviewer
       |
       v
develop branch -> staging
       |
       v
Product Owner approves -> main -> production
```

## Agent Roles

### Engineering Manager (EM)
- Sprint planning and task breakdown
- Technical specification writing
- Maintains `docs/PROJECT_STATE.md` and `docs/roadmap.md`
- Coordinates between Developer and Reviewer

**Invoke with:** "EM, [request]"

### Developer
- Code implementation
- Can push to `develop` (staging) only
- Cannot push to `main` (production)
- Follows task specs from EM

### Reviewer
- Code review before staging deployment
- Max 3 review rounds before escalation
- Can approve or block staging deploys
- Cannot approve production deploys

## Branching Strategy

| Branch | Environment | Who Can Push |
|--------|-------------|--------------|
| `develop` | Staging | Developer (after Reviewer approval) |
| `main` | Production | Product Owner only |

## Getting Started

1. **Initialize your project** with this template
2. **Update docs/PROJECT_STATE.md** with your project's current state
3. **Update docs/roadmap.md** with your planned features
4. **Start working** by telling EM what you want to build

Example first interaction:
```
EM, I want to build [feature]. Can you create a spec and add it to the roadmap?
```

## Skills

### Tech Concept Teacher
Automatically explains technical concepts in plain language when:
- A new technical term is introduced
- You ask "what is X?"
- You share error messages or logs you don't understand

Maintains a growing knowledge base at `.claude/skills/tech-concept-teacher/references/knowledge-base.md`.

## Customization

### Adding Project-Specific Checks
Edit `.claude/agents/reviewer.md` to add domain-specific review criteria:

```markdown
## Project-Specific Checks

**For [Your Domain] routes:**
- [ ] Check 1
- [ ] Check 2
```

### Adding New Agents
Create a new file in `.claude/agents/` following the existing format:

```markdown
---
name: agent-name
description: What this agent does
tools: Read, Write, Edit, Bash, Grep, Glob
model: sonnet
---

You are the [Role] for this project...
```

### Adding New Skills
Create a new folder in `.claude/skills/` with a `SKILL.md` file.
