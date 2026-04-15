# RIGGS — Personal AI Executive Assistant

> A persistent, file-based AI executive assistant built on Claude Code. RIGGS handles daily check-ins, task prioritization, email, calendar, research agents, and long-term goal tracking — all from a structured markdown knowledge base.

---

## What It Is

RIGGS is a personal AI operating system. It runs inside [Claude Code](https://claude.ai/code) using a structured folder of markdown files as its persistent memory and context. Every morning it opens your day. Every evening it closes it. In between, it executes tasks, runs research agents, manages communications, and tracks your goals across nine life pillars.

It is not a chatbot. It is not a plugin. It is a system you own and operate.

---

## Architecture

```
RIGGS_BRAIN/                        ← Git repo. This is the brain.
│
├── CLAUDE.md                       ← System prompt. RIGGS reads this first, every session.
│
├── 00_context/                     ← Who you are, what you're working on, what matters now
│   ├── me.md                       ← Your background, identity, values
│   ├── work.md                     ← Projects, businesses, active work
│   ├── priorities.md               ← Current focus and urgent items
│   └── scratchpad.md               ← Capture inbox — dump ideas here, reviewed daily
│
├── 00_logs/                        ← Decisions and session history
├── 00_system/                      ← RIGGS system projects and daily tracking
├── 00_references/                  ← Operational guides and cheatsheets
├── 00_templates/                   ← Reusable templates and prompt frameworks
│
├── [01-09]_pillars/                ← Life domains: physical, emotional, social, etc.
│
└── .claude/
    ├── skills/                     ← Skill files — morning check-in, evening check-in, save
    └── agents/                     ← Sub-agent definitions for specialized research tasks
```

**How Claude Code uses it:**

- `CLAUDE.md` is the system prompt — it tells RIGGS who it is, what context to load, and how to behave
- Context files are loaded on demand — RIGGS reads only what's relevant, not everything every session
- Skills are markdown files with step-by-step instructions that Claude executes directly
- Git is the safety net — every session commits changes to history

---

## Core Skills

| Skill             | Trigger             | What It Does                                                                   |
|-------------------|---------------------|--------------------------------------------------------------------------------|
| `morning_checkin` | "good morning"      | Journal prompt → daily precept → email/calendar/weather/tasks rundown → commit |
| `evening_checkin` | "evening check-in"  | Collect daily data → nudge incomplete tasks → log → scratchpad review → commit |
| `save`            | `/save`             | Stage, commit, and push all changes → surface open todos and scratchpad items  |

---

## MCP Integrations

RIGGS uses [Model Context Protocol](https://modelcontextprotocol.io) servers to connect to external services:

| Integration          | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| Gmail MCP            | Read and draft emails during check-ins                         |
| Google Calendar MCP  | Surface today's events in the morning rundown                  |
| Telegram MCP         | Mobile access — send/receive messages to RIGGS from your phone |

---

## How to Set It Up

### 1. Clone this repo

```bash
git clone https://github.com/Bagu-Hanto/riggs_boilerplate.git MY_BRAIN
cd MY_BRAIN
```

### 2. Fill in your context

Copy the `.template` files in `00_context/` and fill them in:

```bash
cp 00_context/me.md.template 00_context/me.md
cp 00_context/work.md.template 00_context/work.md
cp 00_context/priorities.md.template 00_context/priorities.md
```

Edit each file with your own information. The inline comments explain what goes where.

### 3. Customize CLAUDE.md

Edit `CLAUDE.md` to match your name, folder structure, and preferences. The template includes placeholder text and comments.

### 4. Install Claude Code

```bash
npm install -g @anthropic-ai/claude-code
```

[Full setup guide →](https://docs.anthropic.com/en/docs/claude-code)

### 5. Open your first session

```bash
cd MY_BRAIN
claude
```

Say "good morning" to trigger your first check-in.

### 6. (Optional) Connect MCP integrations

Follow the setup guides for [Gmail MCP](https://github.com/anthropics/anthropic-quickstarts/tree/main/mcp) and Telegram to enable communications features.

---

## What Makes This Different

Most "AI assistant" setups are stateless — every conversation starts from zero. RIGGS persists:

- **Memory** — context files hold everything about you, your work, and your goals
- **History** — git log is your decision journal and session archive
- **Agency** — skills execute multi-step workflows, not just answer questions
- **Ownership** — you own the repo, the files, and the context. Nothing lives in someone else's cloud.

---

## Use Cases

- Daily check-ins and journaling
- Task prioritization and weekly planning
- Email triage and draft review
- Research agents for specific domains (job search, healthcare, housing, local resources)
- Goal tracking across multiple life areas
- Knowledge capture and retrieval

---

## Want One Built For You?

This system was designed and built by [Your Name](https://yoursite.dev). If you want a customized RIGGS-style assistant for yourself or your team — [get in touch](mailto:your@email.com).

---

## License

MIT — fork it, modify it, make it yours.
