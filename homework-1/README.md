# Homework 1 — Workbook 2: Agents

**Due: Friday, 15 May 2026 — EOD, your local time.**

---

## Context

In class, we walked through **Workbook 1 (Pipeline)** together — the deterministic, step-by-step version of an NL→SQL flow. You watched me wire it up live, ask questions, and we shipped a working pipeline by the end of the session.

For homework, you're going to do the **next workbook on your own** — the one that takes the same problem and re-implements it as a real **agent**: tools, a model loop, decisions about when to call what, and what to do when the model gets it wrong.

This is the homework where you learn what *agentic* actually means in practice — not from the slides, from your own keyboard.

---

## What to do

### 1. Complete Workbook 2 — Agent edition

Reference workbook (the one we used as the base in class):
**https://github.com/fnusatvik07/agentbuilder-class4-nlsql**

Your job:

1. **Fork it or start a fresh repo of your own** (fresh repo preferred — see the root README's submission rules).
2. **Work through Workbook 2 end to end.** Don't skip cells, don't stub things out, and don't only run the happy-path question. Try the messy ones too.
3. **Make it run on your own data or your own keys** — not just a copy-paste of the seed values.
4. **Write up what you learned** in your repo's README (see deliverables below).

### 2. Write up your insights

In your repo's `README.md`, answer these — short and specific, not generic:

- **Pipeline vs. agent — when does each win?** Give one concrete example from your own runs where the agent did something the pipeline couldn't, and one where the pipeline would've been the safer call.
- **Where did the agent surprise you?** Something it got right that you didn't expect, or something it got wrong in a way that taught you about the model's failure mode.
- **What did you change from the workbook defaults, and why?** Prompt tweaks, tool descriptions, model choice, retry logic — anything.
- **One thing you'd do differently next time.**

Keep each answer to 3–6 sentences. We're looking for evidence you *thought*, not for a wall of text.

### 3. Share on Skool

Post in the class Skool group with:

- One-line summary of what you built
- Link to your public repo
- Two or three screenshots of the agent in action (input → tool calls → answer)
- The most surprising thing you learned

---

## Deliverables checklist

- [ ] Public GitHub repo with completed Workbook 2 notebook(s)
- [ ] `README.md` in your repo with the four insight write-ups above
- [ ] `.env.example` showing required keys (no real secrets committed)
- [ ] At least 3 commits showing iterative work (not one giant "initial commit")
- [ ] Skool post with repo link + screenshots + your top insight

---

## Rubric (how this gets reviewed)

| Area | What we're checking |
|---|---|
| **Runs end-to-end** | Fresh clone of your repo + your README → workbook executes without manual fixups |
| **Real engagement** | Commit history, README comments, and notebook markdown show iterative work — not a single dump |
| **Insight quality** | Your four write-ups are specific to your runs, not generic "AI is powerful" filler |
| **Hygiene** | No secrets in git, `.gitignore` correct, dependencies pinned |

---

## Don't do this

- ❌ Paste your `.env` into the notebook "just to make it run on the grader's machine."
- ❌ Submit a notebook where every cell is the workbook's original output and you never re-ran it.
- ❌ Have an LLM rewrite your insights for you. We can tell, and we'd rather read your rough notes than polished slop.
- ❌ Commit `__pycache__/`, `.ipynb_checkpoints/`, or your virtualenv.

---

## If you get stuck

- Compare side-by-side with Workbook 1 (the pipeline version we did in class) — most of the agent's confusion lives in the gap between them.
- The reference workbook's `tools.py` is the most useful file when something's off — start there before changing the prompt.
- Post in `#help` with what you tried, what you saw, what you expected. Drive-by "it doesn't work" pings will get bounced back.
