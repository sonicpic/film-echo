# Film Echo Research Mode

## Contents

- Purpose
- When to Run
- Hard Triggers
- Minimum Search Protocol
- Research Targets
- Research Output
- Use During Interview
- Failure and Fallback

## Purpose

Research mode preserves the agentic part of Film Echo.
Before the interview, the agent should build a small but usable understanding of the film instead of pretending to know it already.

Research mode does not exist to pre-write the review.
It exists to produce a `research_pack` that supports better questions.

## When to Run

Run research mode when:
- the host has browsing, search, or source-reading capability
- the user gives only a title or very thin memory
- the film is difficult, ambiguous, or culturally specific enough that blind questioning would be weak

Skip or minimize research mode when:
- the user already provides rich recap and scene-level notes
- tool access is unavailable
- the user explicitly wants a memory-only interview

## Hard Triggers

Research mode is mandatory when both conditions are true:

1. the host has browse, search, or source-reading capability
2. the user input is thin, such as:
   - title only
   - title plus vague feeling
   - title plus "help me understand this film"
   - title plus one or two unspecific remarks

When these conditions hold, do not skip research and jump straight into interviewing.

If tools are unavailable, say so implicitly or explicitly through the opening behavior:
- keep the first visible reply interview-led
- but do not act as if external research already happened

## Research Targets

Gather only what improves questioning:

- basic film facts
- premise and setup
- main character map
- broad structure or situation map
- public discussion signals
- common confusions or recurring disagreements
- candidate formal signals worth testing in interview

Do not gather trivia for its own sake.
Do not gather ready-made theses to hand to the user.

## Minimum Search Protocol

When research mode is mandatory, complete at least a compact search pass before the first visible reply.

Minimum target set:
- one stable metadata or orientation source
- one broad synopsis or setup source
- one public-discourse source or review/discussion source

Minimum outcomes:
- identify basic film facts
- identify one or two recurring public-discourse signals
- identify one or two candidate formal signals worth testing in interview
- record any obvious unknowns

If the search pass fails, record the failure and continue with user-grounded interviewing.
Failure is better than pretending research succeeded.

## Research Output

Produce a compact `research_pack` using [references/research-pack-schema.md](research-pack-schema.md).

The pack should separate:
- `film_facts`
- `public_discourse_map`
- `candidate_formal_signals`
- `unknowns`
- `source_refs`

## Use During Interview

Use the pack in four ways:

- avoid blind scene guessing
- propose sharper follow-up questions
- notice which confusions are common versus personal
- pressure-test interpretations without pretending the public discourse is authoritative

The interview should still center the user's own viewing.
Do not narrate the entire pack unless the user asks for a research summary.

## Failure and Fallback

If research is partial, noisy, or unavailable:
- keep the partial pack
- mark uncertainty explicitly
- fall back to user-grounded interviewing

Partial research is still better than fake confidence.
Unavailable research is still better than fake confidence, but do not silently behave as if browsing never mattered.
