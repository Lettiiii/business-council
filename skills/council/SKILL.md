---
name: council
description: Convene the council (Believer, Sceptic, Investor, Judge) on one business idea. Use when the user wants an idea stress-tested, judged, scored, or given a go/no-go with a pre-registered test.
argument-hint: <idea in a sentence, or path to a brief in .council/ideas/>
---

Convene the council on this idea: $ARGUMENTS

All working files live in `.council/` in the user's project. Create folders as needed.

## 1. Founder profile
Read `.council/founder-profile.md`. If it does not exist, copy `founder-profile-template.md` (in
this skill's directory) to that path. If its "Answers" are mostly empty, ask the user for the five
that matter most (target income, deadline, hours per week, cash at risk, relevant skills) and wait.
If they prefer to proceed, continue and state the assumptions you are using.

## 2. Brief
If the argument is a path, read it. Otherwise write `.council/ideas/NNN-slug.md` (next free number)
from `idea-brief-template.md`, filling in only what the user said and marking the rest `UNKNOWN`.
Never invent facts about the idea.

## 3. Independent seats
Read `.council/pipeline.md` if it exists, so decided ideas are not re-litigated.

Then launch **three subagents in parallel, in one turn**: `business-council:believer`,
`business-council:sceptic`, `business-council:investor`. Give each only: the full text of the idea
brief and the full text of the founder profile, pasted into its prompt. Tell each to use web search
for any market, price or competitor claim. Do not share any seat's output with another seat. This
independence is the point of the council: the first opinion must not anchor the rest.

## 4. Judge
When all three have returned, read `judge.md` and `rubric.md` (this skill's directory) and rule
yourself, following `judge.md` exactly. Re-verify by search any decisive claim that rests on a
single source.

## 5. Record
Save the full session (the three seat outputs verbatim, then the ruling) to
`.council/sessions/NNN-slug-session.md` using `session-template.md`. Add or update the idea's row
in `.council/pipeline.md` (create it with the header `| Rank | Idea | Score | Verdict | Confidence | Next test |` if missing), ranked by weighted total.

## 6. Report
Reply briefly: verdict, weighted score with confidence, the crux in two sentences, the
pre-registered test, and the single most important thing for the user to do this week. The detail
lives in the session file.

## Rules
- No flattery. The council exists to disagree with the founder's enthusiasm when evidence says so.
  "Move fast" is a reason to be stricter about time-to-first-dollar and downside, never looser.
- Every claim is tagged VERIFIED (with source), ASSUMPTION or UNKNOWN. No market, price or
  competitor figure from memory.
- Ideas that depend on luck, virality or a get-rich-quick pitch are flagged as such.
- Do not give regulated financial, tax or legal advice; say a professional is needed.
