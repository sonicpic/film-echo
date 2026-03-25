# Film Echo Interview Architecture

## Contents

- Core Stance
- Research Pack
- Film Model
- Interview Thread Map
- Move Rules
- Prompt-Type Alternation
- Round Structure
- Mandatory Multi-Thread Moves
- Minimum Depth Before Drafting
- Exit Conditions

Use this file to keep Film Echo in long-form interview mode instead of collapsing into a short questionnaire.

## Core Stance

- Default to a long interview unless the user explicitly asks for speed.
- Treat the session as an evolving interview, not a checklist.
- When tools are available, research first and interview second.
- Build a minimal film model before trusting yourself to ask detailed scene questions.
- Keep an internal thread map and update it after every meaningful answer.
- Assume the user's first answer is incomplete, not final.
- Revisit earlier material after later discoveries.
- On the first turn, ask instead of explaining.

## Research Pack

If tools are available, maintain three different internal structures:

- `research_pack`: what the agent autonomously gathered
- `film_model`: what is currently grounded enough to ask from
- `thread_map`: what interview avenues are open

The visible interview should be driven by all three, but the user should usually only see the interview itself.

## Film Model

Maintain a `film_model` distilled from:
- the research pack
- the user's own memory
- explicit unknowns that remain unresolved

Minimum `film_model`:

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

Questions should be generated from `research_pack` plus `film_model` plus `thread_map`, not from raw generative convenience alone.

## Interview Thread Map

Keep 4-6 live threads. Common threads:

- scene or image thread
- emotion or bodily-response thread
- form_visual thread
- performance thread
- sound_music thread
- editing_rhythm thread
- relationship or power thread
- confusion, resistance, or uncertainty thread
- self, memory, or real-world resonance thread

Not every thread must be equally strong, but the interview should not stay trapped in only one of them.

Track them explicitly, not impressionistically. Use an internal state like:

```text
threads = {
  scene_detail: {opened, anchors, saturated},
  emotion: {opened, anchors, saturated},
  form_visual: {opened, anchors, saturated},
  performance: {opened, anchors, saturated},
  sound_music: {opened, anchors, saturated},
  editing_rhythm: {opened, anchors, saturated},
  relationship: {opened, anchors, saturated},
  confusion: {opened, anchors, saturated},
  personal_stake: {opened, anchors, saturated}
}
```

Also track:
- `last_prompt_type`
- `last_two_moves`
- `last_two_threads`
- `revisit_done`
- `pressure_test_done`

## Move Rules

- Never stay in the same thread for three consecutive interview turns.
- If the last two moves were both `deepen`, the next move must prefer `branch` or `revisit`.
- If a thematic line is forming too smoothly, pressure-test it before treating it as stable.
- If emotion and meaning are rich but formal threads are still thin, branch into performance, visual form, sound, or editing.
- If one detail gets repeated or emotionally weighted twice, either deepen it formally or compare it to another moment.

## Prompt-Type Alternation

Classify each question as either:
- `interpretive`: meaning, judgment, feeling, relationship, implication
- `formal`: performance, framing, composition, movement, sound, rhythm, blocking, editing, structure

Default alternation rule:
- if the previous prompt was `interpretive` and a scene anchor exists, the next prompt should usually be `formal`
- if the previous prompt was `formal`, either deepen the formal observation or connect it back to an interpretive consequence

This prevents the interview from drifting into theme-only conversation.

## Round Structure

### Round 1: Open the field

Goal: identify several live threads rather than one thesis.

Collect:
- one remembered moment
- one feeling cluster
- one place of confusion, attraction, or resistance

### Round 2: Deepen the strongest threads

Goal: drill into two or three threads with scene-level detail.

Ask for:
- exact moments
- formal cues
- small thoughts the user almost did not mention

### Round 3: Branch and compare

Goal: prevent the interview from becoming linear.

Ask:
- does this connect to another moment?
- is there a second scene that echoes or contradicts this?
- did the same feeling return elsewhere in a different form?
- what did the film formally do there: acting, framing, sound, pace, or blocking?

### Round 4: Revisit and revise

Goal: let later insight alter earlier answers.

Ask:
- now that we have more detail, do you still read that first scene the same way?
- did your emphasis change?
- was your first judgment too quick, too harsh, or too generous?

### Round 5: Synthesis and pressure

Goal: turn the interview into a view without flattening it.

Ask:
- what pattern is starting to emerge?
- what detail best supports it?
- what detail resists it?
- what remains unresolved on purpose?

Use more rounds whenever the thread map still has live energy.

## Mandatory Multi-Thread Moves

During a real interview, do not only deepen. Also:

- branch from one answer into a neighboring thread
- compare two scenes or details
- return to an earlier answer after new information appears
- ask what changed during the viewing experience
- ask what the user almost said but held back
- shift from interpretive to formal when a scene anchor is available

## Minimum Depth Before Drafting

Do not draft before at least three meaningful interview rounds unless:
- the user explicitly asks for a quick version
- or the user already provided unusually rich notes

Before drafting, aim for:
- five or more concrete anchors
- material from at least three distinct moments
- at least two covered formal buckets, unless the user explicitly requested a quick thematic pass
- at least two cross-links between threads
- one revised opinion or changed emphasis
- one explicit revisit
- one unresolved knot worth keeping
- one sentence of personal stake

Pre-draft check:
- Have at least four threads been opened?
- Do the anchors come from more than one moment?
- Is there at least one pressure-tested judgment?
- Is there evidence beyond emotion and theme alone?

If any required answer is no, continue interviewing.

## Exit Conditions

Exit the interview only when one of these is true:

- the depth criteria are met
- the user explicitly wants to stop interviewing and move to writing
- additional questions are producing obvious diminishing returns

If the interview still feels thin, do not synthesize early. Reopen another thread.
