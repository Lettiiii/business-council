---
name: scout
description: Generate and shortlist candidate business ideas that fit the founder, before the council judges them. Use when the user has no idea yet, or wants new options.
argument-hint: [optional theme, sector or constraint, e.g. "B2B software" or "no client work"]
---

Scout candidate businesses for the user. Theme or constraint (optional): $ARGUMENTS

This skill only generates and screens ideas. It does NOT rule on them; that is the `council` skill.

1. Read `.council/founder-profile.md` and `.council/pipeline.md`. If the profile does not exist,
   copy `founder-profile-template.md` from the `council` skill's directory to that path. If the
   answers are mostly empty, ask for the five that matter most (target income, deadline, hours per
   week, cash at risk, skills) before scouting widely. Scout anyway, with stated assumptions, if
   the user prefers.
2. Generate 10 to 15 candidates across different models (productized service, software,
   content or audience, marketplace, niche agency, tooling, data). Favour ideas one person can
   bootstrap, that reach first revenue quickly, and that have a lever beyond the founder's hours.
   Do not repeat anything already in the pipeline or listed as discarded.
3. Ground each in something real using web search: a visible demand signal, a live competitor, or a
   stated pain point. Tag claims VERIFIED (with source) or ASSUMPTION.
4. Quick-screen each against three gates: (a) can the founder start alone in under 30 days,
   (b) is there a plausible way to reach a paying customer fast, (c) is there a path to something
   bigger than a job. Drop failures and say why in one line.
5. Write the top 5 survivors as briefs in `.council/ideas/` using `idea-brief-template.md` from the
   `council` skill's directory.
6. Reply with a short ranked list (one line each plus gate results) and recommend which one or two
   to send to the council first, and why.

Do not promise outcomes.
