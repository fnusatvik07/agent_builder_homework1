# Agent Builder. Class 5 Homework

Welcome. This repo contains the two homework assignments for Class 5 of Agent Builder.

Both assignments are due **Friday, 15 May 2026, by 11:59 PM in your local time zone.**

This repo is the assignment brief, not the solution. Each folder has a full README explaining what to do, what to submit, and how it will be reviewed. Read the brief inside the folder before you start.

## At a glance

| # | Title | What you do | Folder |
|---|---|---|---|
| 1 | Workbook 2: Agents | Complete the Agents workbook (the follow-up to the Pipeline workbook we did in class). Write up your insights. | [`homework-1/`](./homework-1/) |
| 2 | Multi-DB Agent: full build | Build the same SkyNova-style agent we built in class (SQL, NoSQL, and RAG over three tools). Run it, test it, demo it. | [`homework-2/`](./homework-2/) |

## Deadline

**Friday, 15 May 2026, 11:59 PM your local time.**

That gives you 5 full days from the date this brief was published (Sunday, 10 May 2026). Plan accordingly.

We will start reviewing submissions on Saturday morning. Late submissions will still be reviewed, but they will not be eligible for the showcase round in next class.

## How to submit (read this carefully)

The submission flow is the same for both homeworks:

1. **Push your work to a public GitHub repo of your own.** Create a fresh repo per homework. Do not fork the reference repo.
2. **Make a post in the Skool community first.** Use the cohort group, in the "Homework" category. Your post should include:
   - A one-line summary of what you built or learned
   - The link to your public GitHub repo
   - Screenshots (Homework 1) or a short demo video (Homework 2)
   - 2 to 3 sentences on what was the most surprising or hardest part
3. **Once your Skool post is up, paste the Skool post link as a comment on the assignment thread for that homework.** That is what we use to track who submitted.

In short: GitHub repo first, Skool post second, then drop the Skool link on the assignment thread. If any of those three steps is missing, your submission is incomplete.

## Where to ask questions

Questions go in the Skool community, not in DMs. Two reasons:

1. Other students learn from your question and the answer.
2. Posting publicly forces you to phrase the problem clearly, which often surfaces the answer on its own.

Use the `#help` channel in Skool. When you post:

- Say what you tried.
- Say what you saw (paste the actual error, not a paraphrase).
- Say what you expected to happen.

Posts that say only "it doesn't work" or "can someone help" will be redirected back with a request for the three points above.

## Ground rules

1. **Do not blindly vibe-code.** Using Claude Code, Cursor, Codex, or other AI tools is expected and fine. The bar is that you understand every line you committed, and could walk through it if asked. If you cannot defend a section of your code, you should not have committed it.
2. **For non-trivial decisions, leave a short note in your README explaining why.** One or two sentences each. Things like "I picked Postgres over SQLite because…" or "I lowered the agent's max iterations to 6 because…". This is the difference between a homework that gets full marks and one that does not.
3. **Never commit secrets.** No `.env` files, no API keys, no database URLs in git. Use a `.env.example` file to document the shape, and add `.env` to your `.gitignore`.
4. **Iterate visibly.** We will look at your `git log`. A single commit with 4,000 lines of changes is a red flag. Aim for a commit per meaningful step.

## What "good" looks like

Both homeworks are reviewed against the same three principles:

1. **Does it run?** Fresh clone of your repo, follow your README, working result.
2. **Did you think?** README, commit messages, and code show that you understood the problem and made deliberate choices.
3. **Did you teach it back?** Your Skool post should be useful to the next student in the cohort. Concrete gotchas and learnings, not "great class".

If those three boxes are checked, you will do well.

## Class resources

- Class 5 recording: posted in Skool under the Class 5 module
- Reference repo for Workbook 1 (the Pipeline workbook we did live): https://github.com/fnusatvik07/agentbuilder-class4-nlsql
- Office hours: see the calendar pinned in Skool

Good luck. Build something you would actually want to use.
