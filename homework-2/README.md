# Homework 2 — Build the Multi-DB Agent

**Due: Friday, 15 May 2026 — EOD, your local time.**

---

## Context

In class, we built a **SkyNova Airlines** customer-service agent end-to-end: a single ReAct loop that can pull from a **SQL** database (passengers, flights, bookings), a **NoSQL** database (support tickets, reviews, activity logs), and a **vector handbook** (RAG over policy docs). One question in, one grounded answer out, with the receipts.

Your homework is to **build the same project yourself, from scratch**, run it against real databases, test it, and demo it.

This is *the* homework where the cohort separates into people who can ship an agent and people who can talk about agents. Pick which one you want to be.

---

## What you're building

A small full-stack app with:

### Backend
- **FastAPI** server with a single `POST /chat` endpoint
- **LangChain v1** ReAct agent (`create_agent`) using **OpenAI `gpt-4o-mini`** (or any model you prefer — document the swap)
- **Three tools**, each typed with Pydantic args:
  1. `sql_query` — read-only SELECT against **Supabase Postgres** (or any Postgres). Must reject writes, multi-statements, and dangerous keywords. Auto-injects a `LIMIT`. Statement timeout.
  2. `mongo_query` — typed args against **MongoDB Atlas** (or local Mongo). Collection whitelist. Hard limit cap. Aggregation pipelines must be restricted to safe stages — no server-side JS.
  3. `handbook_search` — vector RAG over **pgvector** using `text-embedding-3-small`. Returns top-k chunks with their section labels.
- Returns `{answer, tool_calls, warnings, elapsed_ms}` — yes, include `tool_calls` so the UI can show what the agent actually did.

### Frontend
- **Vite + React + TypeScript** chat UI (Tailwind optional but recommended)
- Shows the user's question, the agent's answer, and the **tool call trace** (which tool, what args, what came back)
- Doesn't need auth, doesn't need streaming, doesn't need multi-turn memory. Single-turn is fine.

### Data
- Seed data for all three stores. You can use your own domain (don't have to be airlines) — but pick one with enough variety that all three tools get exercised.
- A handful of handbook documents to chunk + embed.

### Tests
- **pytest** with a unit / integration / e2e split
- Mock the LLM at the unit level (LangChain's `GenericFakeChatModel` works well)
- At least one e2e test that runs a real question through the full agent loop

---

## Reference architecture (what we built in class)

```
Browser ─→ React UI ─→ FastAPI ─→ LangChain v1 ReAct agent ─→ [sql_query | mongo_query | handbook_search] ─→ live store
```

The agent **never** connects to the data stores directly. Every read goes through one of the three typed tools. This is the part most students get wrong on the first try — if your agent has a `psycopg` connection in its hand, you've broken the pattern.

---

## What to do

### Step 1 — Spec before code (30 min, mandatory)

Before you `uv init`, write a short `SPEC.md` in your repo with:

- **What problem are you solving?** Who's the user, what do they ask the agent?
- **What are the 3 tools, and what's the contract for each?** (input args, return shape, error cases)
- **What's the system prompt going to tell the agent about when to use which tool?**
- **What does "done" look like?** Five sample questions you'll test against, with expected answer shapes.

This file gets committed to your repo. Reviewers will read it first. If your spec is "build an agent like in class," you've already lost the homework.

### Step 2 — Build it

Stand it up incrementally — don't try to wire everything at once:

1. FastAPI hello world → `POST /chat` returning a stub
2. One tool working in isolation (start with `sql_query` — it's the simplest)
3. Wire LangChain ReAct agent with that one tool, get a real question answered
4. Add the second tool, then the third
5. Frontend last (it's the easy part once the backend works)

Commit after each step. We will look at your `git log`.

### Step 3 — Test it

- Unit tests for each tool (good inputs, malformed inputs, dangerous inputs)
- Integration tests that hit a real (test) database
- An e2e test that runs your five sample questions from `SPEC.md` end-to-end

If you can't be bothered to write tests, write **one** integration test per tool and one e2e test. The bar is "you actually verified it works," not "you have 90% coverage."

### Step 4 — Demo

Record a **short screen capture** (2–4 minutes is plenty) showing:

- The UI loading
- You asking a question that hits the **SQL** tool — show the tool trace
- You asking one that hits the **NoSQL** tool — show the trace
- You asking one that hits the **RAG** tool — show the trace
- One question that the agent gets *wrong* or *partially wrong*, and your reaction to it

That last one is the most important. Anyone can demo a happy path. Show us you've actually used the thing.

If you can't record video, post 4–5 screenshots covering the same flows.

### Step 5 — Write up your findings

In your repo's `README.md`, include sections for:

- **Architecture** — your version of the diagram above (a sketch is fine)
- **Why I chose X** — your model, your DBs, your domain
- **What broke and how I fixed it** — the three best war stories from the build
- **What I'd change if I had another week** — be specific

### Step 6 — Share on Skool

- Repo link
- Demo video (or screenshots) embedded in the post
- Two or three sentences on the most surprising thing you learned

---

## Deliverables checklist

- [ ] Public GitHub repo (your own — not a fork of the class repo)
- [ ] `SPEC.md` — written **before** you started coding
- [ ] Working backend (FastAPI + LangChain v1 + 3 tools)
- [ ] Working frontend (chat UI + tool-call trace)
- [ ] Seed data for all three stores + load scripts
- [ ] At least one test per tool + one e2e test
- [ ] `.env.example` with required keys (no real secrets in git)
- [ ] `README.md` covering setup, architecture, decisions, and findings
- [ ] Demo video or screenshots showing all three tools in action *and* one failure case
- [ ] Skool post with everything above

---

## Rubric

| Area | Weight | What we're checking |
|---|---|---|
| **Spec quality** | 20% | `SPEC.md` shows real thinking before coding. Tool contracts are concrete. Sample questions are realistic. |
| **It runs** | 25% | Fresh clone → follow your README → working agent. Reviewers will actually do this. |
| **Tool design** | 20% | Read-only enforced. Inputs validated. Errors don't crash the agent loop. The agent never bypasses a tool. |
| **Tests** | 10% | At least the minimum bar (one per tool + one e2e). They actually pass. |
| **Demo + write-up** | 15% | Demo covers all three tools and one failure. Findings are specific to your build. |
| **Hygiene** | 10% | No secrets. Clean `git log` showing iterative work. README is the friend of a stranger trying to run it. |

---

## Don't do this

- ❌ Skip `SPEC.md` and dive into code. We'll see the empty file in your repo and dock 20% off the top.
- ❌ Let the agent run raw SQL the LLM wrote without validation. One `DROP TABLE` and we're done.
- ❌ Hardcode your `.env` values in `settings.py` to "make it easier for the grader."
- ❌ Submit a single `feat: initial commit` with 4,000 lines. We want to see your build, not the final state.
- ❌ Have Claude/Cursor/Codex generate the whole thing in one shot and submit without reading it. We'll ask you to walk through the code and you won't be able to.
- ❌ Skip the demo because "it works locally." If we can't see it work, it doesn't.

---

## Stretch goals (optional, for the showcase round)

If you finish early and want to push:

- **Streaming responses** so the UI shows the agent's reasoning as it goes
- **Multi-turn memory** with proper conversation summarization
- **Auth** — even fake JWT auth, just to see the pattern
- **A fourth tool** — file search, web search, your call
- **Eval harness** — run your five sample questions on every commit and track pass/fail over time

These are not required. Get the base build solid first.

---

## If you get stuck

- Re-watch the class recording. Most "I don't understand X" is answered there.
- The class reference repo (will be linked in Skool, not here — we want you to try first) is your last-resort lookup, not your starting point.
- `#help` channel: what you tried, what you saw, what you expected. We won't debug "it doesn't work" with no context.
- If you're stuck for more than 90 minutes on the same thing, that *is* the moment to ask. Don't grind alone for a day — that's not the lesson.
