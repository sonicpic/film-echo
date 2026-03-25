# Film Echo Research Pack Schema

## Contents

- Core Object
- Field Meanings
- Source Tiers
- Confidence Rules
- Interview Use Rules

## Core Object

Maintain a compact internal structure like:

```text
research_pack = {
  film_facts: {
    title,
    year,
    country,
    director,
    runtime,
    premise,
    known_characters,
    broad_structure
  },
  public_discourse_map: {
    recurring_praises,
    recurring_doubts,
    common_confusions,
    recurring_formal_notices,
    controversy_points,
    overused_readings
  },
  candidate_formal_signals: {
    performance,
    visual_form,
    sound_music,
    editing_rhythm,
    directing_blocking
  },
  source_refs,
  unknowns
}
```

## Field Meanings

- `film_facts`: stable orientation facts and broad setup only
- `public_discourse_map`: what reviewers and viewers repeatedly notice, argue about, or get stuck on
- `candidate_formal_signals`: formal dimensions worth testing in interview, not facts to force on the user
- `source_refs`: compact provenance for later trust decisions
- `unknowns`: what still should not be treated as grounded

## Source Tiers

Use source tiers internally:

- `tier_1`: official/basic metadata and highly stable identification facts
- `tier_2`: plot setup or broad orientation from reliable synopsis-like sources
- `tier_3`: long-form criticism or reviews
- `tier_4`: short comments, discussions, and forum-like public chatter
- `tier_user`: the user's own memory, recap, and notes

Facts should mostly come from `tier_1`, `tier_2`, or `tier_user`.
Discussion signals may come from `tier_3` and `tier_4`.

## Confidence Rules

Treat the pack with different confidence levels:

- `stable_fact`
- `discussion_signal`
- `tentative_pattern`
- `unknown`

Do not let `discussion_signal` masquerade as `stable_fact`.
Do not let `tentative_pattern` become a leading question unless phrased tentatively.

## Interview Use Rules

Good use:
- "A lot of viewers seem split on whether the ending feels hopeful or bittersweet. Did you feel a split there too, or not at all?"
- "Some discussion around this film keeps noticing the sound design. In your own viewing, was there any recurring sound or silence that stayed with you?"

Bad use:
- "This film is obviously about X because critics say so."
- "The key scene is Y."
  when Y has not been user-confirmed or stably grounded
