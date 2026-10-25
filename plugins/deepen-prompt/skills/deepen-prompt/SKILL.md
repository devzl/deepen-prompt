---
name: deepen-prompt
description: Use when the user wants a deeper (not bigger) version of a task or prompt, asks what a top professional would do differently, wants a prompt rewritten around raw sources, named methods and independent verification, or says "deeper version", "go deeper", "rewrite my prompt like an expert".
---

# Deepen Prompt

## Overview

Deeper means better method, not more scope. Same task, same size, but done the way a top practitioner would do it, with evidence that something other than you or the user can check.

Do not add deliverables, sections or features. If the rewrite asks for more output than the original, it failed.

## Input

The task or prompt to deepen: text in the request, or the most recent task in the conversation. If neither exists, ask for it in one line and stop.

## Output, in this order

Answer all four before rewriting. Each answer is specific to this task and field, never generic.

1. **Unrequested practice.** What a top professional in this field would do that the user did not ask for. Pick the 1 to 3 habits that change the result most.
2. **Rawest material.** The primary, undigested source they would start from instead of summaries, tutorials or pre-processed data. Name the actual thing (a dataset, a spec, a log, a filing, a corpus, a source file), not a category.
3. **Methods and tools.** The named techniques, instruments or software they would use, with the reason each fits this task.
4. **Independent check.** What other than you or the user would show the result is right: a test suite, a reference dataset, a calculation, a regulator or standard, a measurement, an external reader. If nothing independent exists, say so, then name the closest substitute.

Then give **Rewritten prompt**: one prompt in a code block that requires exactly answers 1 to 4, same scope as the original. It must name the raw material, the methods and tools, and the independent check, and say what to report if the check fails.

## Then execute it

Do not stop after the rewrite and do not wait for approval. Carry out the rewritten prompt in the same turn:

- **The ask was an action** (build, fix, write, change, analyze): implement it directly, starting from the raw material, using the named methods and tools, then run the independent check and report the result faithfully, including a failure or a check you could not run.
- **The ask was a question**: answer it, using the rewritten prompt as the method. Cite the raw material. State what independent evidence supports the answer, or that none exists.
- Project rules and user instructions still win. If the project says to hand off for testing, commit only after confirmation, or avoid certain tools, follow that and say the check is pending.
- Stop and ask only if an action is destructive, outward-facing, or blocked by a missing decision only the user can make.

## Rules

- No new deliverables. Depth replaces breadth, in the rewrite and in the work.
- Name real tools and sources. If unsure one exists, search first or flag it as unverified.
- Never invent a verifier. A check that only the model or user can judge is not independent.
- Keep the original goal and constraints unchanged. Say what you changed and why in one line each.

## Common Mistakes

| Mistake | Fix |
|---|---|
| Rewrite grows longer and asks for more output | Cut back to the original scope |
| "Best practices" or "reputable sources" | Name the exact source or tool |
| Verifier is "review it carefully" | Name an external, checkable artifact |
| Starting material is a blog post or summary | Go to the primary source |
