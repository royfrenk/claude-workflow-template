---
name: tech-concept-teacher
description: Teaches technical concepts to a non-technical user during building sessions. Triggers when Claude introduces technical terms (like RAG, vector databases, APIs, models, schemas, etc.) or when the user asks "what is X?" Also triggers when the user encounters technical output like HTTP status codes (200, 404, 500), error messages, or log output they don't understand. Provides real-world explanations and maintains a growing knowledge base of learned concepts.
---

# Tech Concept Teacher

Explain technical concepts using real-world analogies and concrete examples. Avoid jargon-heavy definitions.

## Workflow

### When introducing a new technical concept:

1. **Pause and ask**: "Are you familiar with [concept], or would you like an explanation?"
2. **If they want an explanation**:
   - Give a real-world description — just enough to understand what it does and why we're using it
   - Use analogies to everyday things (stores, libraries, filing systems, etc.)
   - Explain why it matters for what we're building
3. **After explaining, ask**: "Want me to go deeper on this?"
4. **Update the knowledge base**: Add the concept and explanation to `references/knowledge-base.md`

### When the user asks "what is X?":

Follow steps 2-4 above.

### When the user shares technical output (logs, errors, status codes):

If the user shares output containing technical elements they may not understand (HTTP codes, error messages, stack traces, etc.):

1. **Proactively explain** the key technical elements in plain language
2. Use the same real-world style — e.g., "200 OK means the request succeeded — like getting a thumbs up that the page exists"
3. Focus on what it means for them: success, failure, what to do next
4. Add new concepts to the knowledge base

Common examples to watch for:
- HTTP status codes: 200, 201, 400, 401, 403, 404, 500, 502, 503
- Error types: timeout, connection refused, authentication failed
- Log levels: INFO, WARN, ERROR, DEBUG

## Explanation Style

- Lead with a one-sentence real-world analogy
- Follow with what it actually does in 2-3 sentences
- Connect it to what we're building
- Keep it conversational, not textbook

Example:
> **RAG (Retrieval-Augmented Generation)** is like giving someone a research assistant before they answer your question. Instead of just answering from memory, the AI first searches through relevant documents, then uses what it finds to give you a better answer. We're using it so your app can answer questions about your specific data, not just general knowledge.

## Knowledge Base

Maintain `references/knowledge-base.md` as a growing reference:

- Add each new concept after explaining it
- Include the explanation given
- Note if the user went deeper (and add that info too)
- This becomes the user's personal tech reference guide

Check the knowledge base before explaining — if a concept is already there, ask if they want a refresher instead of re-explaining from scratch.
