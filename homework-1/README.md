# Homework 1: Workbook 2 (Agents)

**Due: Friday, 15 May 2026, 11:59 PM your local time.**

## What this homework is about

In class, we walked through Workbook 1, the Pipeline version of an NL-to-SQL flow. You watched it being wired up live and we shipped a working pipeline by the end of the session.

For homework, you will do the next workbook on your own. Workbook 2 takes the same problem and re-implements it as a real **agent**: tools, a model loop, decisions about when to call which tool, and what to do when the model gets it wrong.

This homework is where you learn what "agentic" actually means in practice. Not from the slides, from your own keyboard.

## What to do

Follow these steps in order. Do not skip ahead.

### Step 1. Set up your repo

1. Go to the reference workbook: https://github.com/fnusatvik07/agentbuilder-class4-nlsql
2. Read its README first. Do not start coding yet.
3. Create a **fresh public GitHub repo of your own** for this homework. Suggested name: `agent_builder_class5_hw1_yourname`.
4. Copy the workbook files into your repo (or fork-then-detach if you prefer; just make sure the commit history is yours).
5. Add a `.gitignore` so you do not accidentally commit `.env`, `.ipynb_checkpoints/`, `__pycache__/`, or your virtualenv.

### Step 2. Get it running locally

1. Set up the Python environment (`uv` or `venv`, your call).
2. Create a `.env` file with your own keys. Do **not** commit it.
3. Create a `.env.example` file (no real values) so a reviewer knows what keys are required.
4. Run the workbook through cell by cell. If a cell errors, fix it before moving on.

### Step 3. Complete Workbook 2 end to end

1. Work through every section of the agent workbook. Do not stub things out and do not skip cells.
2. Run at least 5 different questions through the agent, including:
   - One easy "happy path" question
   - One question that requires the agent to call multiple tools
   - One question that is intentionally ambiguous, so you can see how the agent handles it
   - One question that you expect the agent to get **wrong**, so you can study its failure mode
   - One question of your own choosing
3. For each of the 5 questions, save the input, the tool calls the agent made, and the final answer in a markdown file at `runs.md` in your repo.

### Step 4. Write up your insights

Create a `README.md` at the root of your repo. In addition to the standard "how to run this" instructions, include a section called **"What I learned"** that answers these four questions. Keep each answer to 3 to 6 sentences and keep it specific to *your* runs.

1. **Pipeline vs agent: when does each win?** Give one concrete example from your own runs where the agent did something the pipeline could not, and one example where the pipeline would have been the safer choice.
2. **Where did the agent surprise you?** Either something it got right that you did not expect, or something it got wrong in an interesting way.
3. **What did you change from the workbook defaults, and why?** Prompt tweaks, tool descriptions, model choice, retry logic, anything.
4. **What is one thing you would do differently next time?**

### Step 5. Submit

In this order:

1. Push everything to your public GitHub repo. Make sure the README, `runs.md`, and `.env.example` are all committed.
2. Create a post in the Skool community in the **Homework** category. Title format: `HW1 Submission - YourName`. The post should include:
   - One-line summary of what you built
   - Link to your public repo
   - 2 or 3 screenshots of the agent in action (input, tool calls, final answer)
   - The single most surprising thing you learned, in your own words
3. Drop the link to your Skool post as a comment under the **HW1 Assignment Thread** in Skool.

If any of these three steps is missing, the submission is incomplete.

## Deliverables checklist

Before you hit submit, confirm all of the following:

- [ ] Public GitHub repo with completed Workbook 2 notebook(s)
- [ ] `runs.md` showing your 5 sample questions and the agent's traces
- [ ] `README.md` with setup instructions and the "What I learned" section
- [ ] `.env.example` showing required keys (with no real values)
- [ ] `.gitignore` that excludes `.env`, `__pycache__/`, `.ipynb_checkpoints/`, and your virtualenv
- [ ] At least 3 commits showing iterative work (not one giant initial commit)
- [ ] Skool post in the Homework category with repo link and screenshots
- [ ] Skool post link added as a comment on the HW1 Assignment Thread

## How this gets reviewed

| Area | What we check |
|---|---|
| Runs end to end | Fresh clone of your repo, follow your README, the workbook executes without manual fixups. |
| Real engagement | Commit history, README comments, and notebook markdown show iterative work, not a single dump. |
| Insight quality | Your four write-ups are specific to your runs, not generic filler. |
| Hygiene | No secrets in git, `.gitignore` is correct, dependencies are pinned. |

## Common mistakes to avoid

1. Committing your `.env` "just to make the grader's life easier". This will cost you points.
2. Submitting a notebook where every cell still shows the workbook's original output and you never re-ran anything.
3. Having an LLM rewrite your insights for you. We can tell. We would rather read your rough notes than polished filler.
4. Committing `__pycache__/`, `.ipynb_checkpoints/`, or your virtualenv folder.
5. Skipping the Skool post and hoping the GitHub repo is enough. It is not.

## If you get stuck

1. Compare the workbook side by side with Workbook 1 (the Pipeline version we did in class). Most of the agent's confusion lives in the gap between the two.
2. The reference workbook's `tools.py` is usually the most useful file when something is off. Start there before changing the prompt.
3. If you have been stuck for more than 30 minutes on the same thing, post in `#help` on Skool. Include what you tried, what you saw, and what you expected.
