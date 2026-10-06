# Business Council

A Claude Code plugin that puts a business idea in front of a four-seat council before you spend
months on it.

| Seat | Job |
|------|-----|
| **Believer** | Builds the strongest honest case for the idea |
| **Sceptic** | Builds the strongest honest case against it, with evidence and a cheap disproof test |
| **Investor** | Prices it: time, cash, unit economics, scale, exit |
| **Judge** | Reads all three, scores against a rubric, rules PURSUE / TEST / PARK / KILL, and pre-registers the test |

The Believer, Sceptic and Investor run as **separate subagents that never see each other's output**.
Only the Judge sees everything. That stops the first opinion from anchoring the rest, which is
what a single role-played "debate" in one response cannot do.

Other design choices:
- Every claim is tagged `VERIFIED` (with a source), `ASSUMPTION` or `UNKNOWN`. Market, price and
  competitor figures come from web search, not memory.
- Every verdict ends with a pre-registered test: experiment, cost cap, time box, success and kill
  thresholds, written down before it is run.
- A goal gate: every ruling states the probability of reaching your target income by your deadline.
- Everything is saved as plain Markdown in `.council/` in your project: ideas, full sessions, and a
  ranked `pipeline.md`.

## Install

```bash
claude plugin marketplace add Lettiiii/business-council
claude plugin install business-council@business-council
```

Or inside a session: `/plugin marketplace add Lettiiii/business-council`, then
`/plugin install business-council@business-council`.

To try it from a local clone without installing: `claude --plugin-dir ./business-council`.

## Use

```
/business-council:scout                 # generate and screen candidate ideas
/business-council:scout "B2B software, no client work"
/business-council:council "A tool that turns support tickets into a public changelog"
/business-council:council .council/ideas/001-changelog-tool.md
```

On first run the plugin creates `.council/founder-profile.md` and asks for your target income,
deadline, hours, cash at risk and skills. The council judges fit against that profile, so answer
honestly. **Do not commit your founder profile to a public repository.**

## What it creates in your project

```
.council/
  founder-profile.md
  pipeline.md              ranked list of every idea judged
  ideas/NNN-slug.md        one brief per idea
  sessions/NNN-slug-session.md   full council transcript and ruling
```

## Customising

- **Rubric**: edit `skills/council/rubric.md` (weights must sum to 100).
- **Seats**: each is a Markdown file in `agents/`. Change a mandate or add a fifth seat.
- **Judge**: `skills/council/judge.md`.

## Limits

The council is a filter for ordering ideas, not a forecast. Scores on thin data are labelled low
confidence. Nothing here is financial, tax or legal advice.

## License

MIT
