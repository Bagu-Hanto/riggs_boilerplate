---
name: agents
description: Sub-agent definitions for specialized research and autonomous tasks.
type: reference
---

# agents — Sub-Agent Definitions

This folder holds agent definition files. Each agent is a specialized sub-process that RIGGS can launch for focused, multi-step tasks — keeping the main conversation clean and the context window lean.

---

## How Agents Work

Agents are launched via the Agent tool inside Claude Code. Each agent definition is a markdown file with YAML frontmatter that tells Claude what the agent does, what tools it has access to, and how to behave.

---

## When to Use an Agent vs. Inline

| Use an agent when...                               | Handle inline when...             |
|----------------------------------------------------|-----------------------------------|
| The task requires many web searches                | It's a quick lookup               |
| You want results without cluttering the main chat  | It's a single-step task           |
| The task could run in the background               | You need the result immediately   |
| It's a recurring research task                     | It's a one-off question           |

---

## Example Agents to Build

- `job_search_researcher` — searches job boards for roles matching your profile
- `market_researcher` — researches pricing, competition, or demand for a product idea
- `news_briefer` — pulls headlines on topics you care about and summarizes them

---

## Agent File Format

```yaml
---
name: agent_name
description: One-line description of what this agent does and when to use it.
tools: WebSearch, WebFetch, Read, Write
---

# Agent Name

[Instructions for the agent — what it does, how it behaves, what it outputs]
```
