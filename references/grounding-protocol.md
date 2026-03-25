# Film Echo Grounding Protocol

## Contents

- Why Grounding Comes First
- Research Pack
- Film Model
- Grounding Sources and Order
- Epistemic Labels
- Question Generation Rules
- Minimal External Grounding
- Grounding Exit Conditions

## Why Grounding Comes First

Film Echo should not ask detailed questions as if it already understands the film when it does not.
Before deep interviewing, build a small internal film model.
The goal is not to replace the user's view with a synopsis. The goal is to stop the interview from inventing scenes, beats, or formal claims out of thin air.

## Research Pack

When tool access allows, build a `research_pack` first.
Use [references/research-mode.md](research-mode.md) and [references/research-pack-schema.md](research-pack-schema.md).

The pack is upstream of the film model:

```text
research_pack -> film_model -> interview questions
```

The pack should help you ask better questions, not speak over the user.

## Film Model

Maintain a minimal structure like:

```text
film_model = {
  title,
  premise,
  known_characters,
  grounded_moments,
  known_formal_signals,
  broad_structure,
  user_reported_confusions,
  unknowns
}
```

Every useful question after the opening should grow out of this model.

## Grounding Sources and Order

Use this order:

1. Research pack, if available
   - stable facts
   - public discussion signals
   - candidate formal signals
2. User grounding
   - the user's recap
   - scenes they mention
   - names, relationships, details, and confusions they remember
3. Minimal external grounding, only if the host allows it and no research pack exists
   - premise
   - main characters
   - broad setup
   - obvious structural facts needed to avoid blind guessing
4. Explicit unknowns
   - things neither the user nor grounding sources have established

Prefer user grounding whenever possible.
If research mode was mandatory and no research pack exists, treat that as a missing step rather than silently collapsing the distinction.

## Epistemic Labels

Track the status of each useful element:

- `stable_fact`
- `discussion_signal`
- `user_confirmed`
- `externally_grounded`
- `assistant_inferred`
- `unknown`

Do not treat `assistant_inferred` as if it were fully known.
Do not generate scene-specific questions from `unknown`.
Do not treat `discussion_signal` as a fact about the film.

## Question Generation Rules

- If only the title is known, ask bounded memory questions, not scene-specific questions.
- If a research pack exists, use it to decide which openings are promising, but keep the first visible move user-centered.
- If a scene is `user_confirmed`, you may ask about acting, framing, sound, rhythm, blocking, or meaning inside that scene.
- If a character name or relation is `externally_grounded`, you may use it for orientation, but do not derive ready-made interpretation from it.
- If a recurring public-discourse question exists, you may ask whether it appeared in the user's own experience.
- If something is only `assistant_inferred`, either mark it tentatively or ask the user to confirm it.
- If the model lacks enough grounding for a formal question, ask for another concrete moment first.
- If mandatory research did not run despite available tools, do not fake a grounded film model.

Good behavior:
- "You mentioned the rooftop scene. Was it the silence, the framing, or the acting that stayed with you there?"

Bad behavior:
- "When the teacher later uses music to redeem the class, is the camera making him saint-like?"
  when neither that scene nor that reading has been grounded

## Minimal External Grounding

Minimal external grounding is allowed only to prevent blind interviewing.
Keep it factual and structural:

- premise
- main character names
- basic setting
- broad relation map

Do not use grounding to import criticism, symbolism, or a ready-made thesis before the interview.
If a research pack already exists, prefer it over ad hoc external grounding.

## Grounding Exit Conditions

You have enough grounding to move into deep interview when at least one of these is true:

- the user has supplied one concrete moment and one feeling
- the user has supplied a short recap plus one confusion point
- the host has a minimally grounded premise and the user has confirmed at least one remembered anchor

If none of these are true, stay in grounding mode and keep the questions simple.
