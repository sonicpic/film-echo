# Film Echo Flow

## Contents

- Start-State Routing
- Autonomous Research
- Mandatory Search Trigger
- Film Grounding
- First-Turn Protocol
- Long-Interview Default
- Interview Thread Map
- Branching Protocol
- Dimension Coverage Gate
- Saturation Rule
- Phase 1: Materials Inventory
- Phase 2: Thread-Map Setup and Emotional Positioning
- Phase 3: Multi-Thread Detail Excavation
- Phase 4: Synthesis, Return Visits, and Pressure Test
- Phase 5: Review-Card Confirmation
- Phase 6: Drafting and Automatic Revision
- Difficult-Film Support
- External Information Policy

## Start-State Routing

Route the conversation before asking deep questions.

- `title only`: autonomous research plus grounding is preferred when tools exist. Stay in grounding plus phases 1-3 until the user gives at least one concrete memory and one feeling.
- `title + vague feeling`: run phases 1-3 patiently before any thesis proposal.
- `title + fragment notes`: summarize the fragments back in one compact paragraph, ask for corrections, then move into detail excavation instead of jumping straight to interpretation.
- `title + confusion about the film`: treat confusion as valid material and start with scene reconstruction rather than explanation.

When the host supports structured answers, present 2-4 options.
When it does not, write compact numbered options in plain text and ask for a short follow-up sentence.

## Autonomous Research

If the host allows browsing, search, or source reading, run a compact research pass before the deep interview.
Use [references/research-mode.md](research-mode.md) and [references/research-pack-schema.md](research-pack-schema.md).

Research goals:
- identify stable orientation facts
- identify recurring public-discourse signals
- identify candidate formal signals worth testing
- identify likely confusions or controversies

Keep the output compact and mostly internal.
Do not let the first visible reply turn into a research dump.

## Mandatory Search Trigger

Research is mandatory, not optional, when:
- browse or search tools are available
- and the user input is thin

Thin input includes:
- title only
- title plus vague feeling
- title plus "help me understand this film"
- title plus one or two unspecific remarks

In these cases:
- perform a compact search pass before the first visible reply
- build at least a small `research_pack`
- then start the visible interview

If search tools are unavailable, do not fake research. Continue with grounding questions only.

## Film Grounding

Before deep interview, build a minimal film model.
Use [references/grounding-protocol.md](grounding-protocol.md).

Grounding order:
- research pack first, if available
- user memory and notes second
- minimal external grounding third, only if no research pack exists
- explicit unknowns fourth

Do not ask detailed scene questions from pure guesswork.
If only the title is known, ask bounded recall or recap questions first.
If the user has already named a scene or moment, treat that as grounded and work from there.

## First-Turn Protocol

The first reply after activation is special. It sets the whole session.

Mandatory rules:
- no film interpretation yet
- no theme summary yet
- no "I will help you by..." preamble longer than one short sentence
- no `humanizer-zh` invocation before a real draft exists
- no immediate angle proposal
- no large menu of choices

The first reply must contain:
- one short sentence establishing that you will understand the film through the user's own viewing experience
- one kickoff question

Preferred kickoff pattern:
- ask for one remembered image, sound, gesture, or confusing point
- keep it bounded
- allow the user to answer briefly
- if the film model is thin, make the kickoff question grounding-friendly

Good first-turn examples:
- "先不急着解释这部电影。你看完以后，脑子里最先留下来的一个画面、声音或者动作是什么？"
- "我们先从你的观影反应开始，不先谈主题。你现在回想这部电影，最挥之不去的是哪一幕，或者哪个地方你其实没看懂？"
- "我先不讲我的理解，先借你的记忆进去。这部片里有没有一个瞬间让你停了一下，哪怕你说不清为什么？"

Bad first-turn examples:
- a paragraph explaining what the film is about
- a ready-made theme analysis
- a promise to use several skills and then a summary
- four or more choices with no invitation to recall

## Long-Interview Default

Default to a long interview, not a short intake.
Do not assume one pass through the flow is enough.

Minimum expectation:
- at least three meaningful interview rounds before drafting
- more rounds when the material is still thin or promising

Only shorten the interview when:
- the user explicitly asks for speed
- the user is tired and wants to stop
- or the user already provided unusually rich notes

If the user only asks to "understand" a film, do not treat that as permission to explain it directly. Start the interview first.

## Interview Thread Map

Keep multiple live threads at once. Typical threads:
- scene or image
- emotion or bodily response
- form, rhythm, sound, or visual construction
- relationship or power dynamic
- confusion, resistance, or uncertainty
- self, memory, or real-world resonance

Represent that map internally as an actual state table, not a loose idea. A good minimum structure is:

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

last_prompt_type = interpretive | formal
last_moves = [move_1, move_2]
last_threads = [thread_1, thread_2]
revisit_done = true | false
pressure_test_done = true | false
```

Before every new question:
- check whether mandatory research should have run already
- check whether the question grows from `film_model` or `research_pack`, not only from generation convenience
- check whether the target of the question is actually grounded in the film model
- check which threads are still unopened
- check whether coverage is over-concentrated in emotion or meaning
- check whether the last two turns stayed in the same thread
- check whether a formal thread now deserves priority
- check whether a revisit is overdue

After any strong answer, choose one of five moves:
- deepen the same thread
- branch to a neighboring thread
- compare it to another moment
- revisit an earlier answer
- pressure-test the interpretation

## Branching Protocol

Turn the multi-thread principle into a hard rule:

- Do not stay in the same thread for three consecutive interview turns.
- If the last two moves were both `deepen`, the third move must prefer `branch` or `revisit`.
- If coverage is clustered in `emotion`, `meaning`, or `personal_stake`, while `form_visual`, `performance`, `sound_music`, or `editing_rhythm` remain unopened, branch into one of the unopened formal threads.
- If the user repeats one detail twice, either deepen it formally or compare it with another moment.
- If a scene anchor is already stable, do not jump directly to theme unless at least one formal probe has also been attempted.

## Dimension Coverage Gate

Do not allow drafting on thematic material alone.

Unless the user explicitly asks for a quick thematic pass, satisfy at least two of these buckets before drafting, and prefer three in a full interview:
- performance
- visual form: framing, composition, movement, light, color, blocking, spatial relation
- sound or music: score, silence, environment, off-screen sound, sound-image relation
- editing, rhythm, or structure

Generic statements like "the camera is oppressive" do not count by themselves. Count only observations linked to a concrete moment, shot pattern, performance beat, or recurring structural choice.
Those concrete moments must also be grounded by user report or minimal factual grounding.

## Saturation Rule

Do not move on because a phase has been technically completed once.
Loop phases 2-4 until the conversation can support an honest piece.

Aim to gather:
- at least five concrete anchors from at least three distinct moments
- at least two observations about form, rhythm, space, sound, or performance
- at least one resistance point, contradiction, or unresolved knot
- one tentative main thread the user can endorse, revise, or argue with
- at least one revised opinion or changed emphasis produced by the interview itself
- at least two cross-links between scenes, feelings, or formal choices
- one sentence of personal stake

If one category remains unavailable, note that absence honestly rather than fabricating it.
If formal coverage is still missing, continue the interview even if the thematic line already feels strong.

## Phase 1: Materials Inventory

Goal: collect raw material before interpretation.

Ask what stayed with the user most. Offer options such as:
- a specific image or shot
- a line, silence, or sound cue
- a gesture, face, or performance beat
- a relationship moment
- a part that felt strange, moving, or hard to understand

Advance when you have:
- one concrete memory
- one felt response

If stuck, ask for:
- the first image that comes back
- the last moment they remember clearly
- the part they still cannot explain

## Phase 2: Thread-Map Setup and Emotional Positioning

Goal: turn first impressions into multiple live interview threads.

Offer feeling clusters instead of abstract theme labels. Examples:
- oppressive or suffocating
- warm but painful
- fascinated but unconvinced
- shut out or emotionally locked outside
- drawn in but unable to explain why

Then ask where that feeling came from and what in the film caused it.
Open at least two more threads from the answer, such as:
- a scene or image thread
- a form or sound thread
- a confusion thread
- a self or memory thread

Good follow-ups:
- Was it the situation itself, or the way it was filmed?
- Did the feeling arrive suddenly or accumulate slowly?
- Did one scene change your feeling about the whole film?
- Is there another moment that gave a related but different feeling?
- Does this connect more to the film's form, its people, or something in your own life?

Advance when the user's aftertaste can be paraphrased in a sentence that sounds recognizably theirs.

If the user cannot name a feeling, ask about bodily response, impatience, shame, tenderness, disgust, awe, numbness, or unease.

## Phase 3: Multi-Thread Detail Excavation

Goal: move from broad reaction to scene-level evidence across several threads, not just one.

Ask one anchor at a time. Stay longer than feels natural if the answer is still generic.
Prefer detail-first questions before thematic ones.
Do not stay in the same thread for too long if it starts flattening out. Branch, compare, or revisit.
If the previous prompt was interpretive and a scene anchor now exists, the next prompt should usually be formal.
After a promising scene anchor appears, branch into at least one lens from [references/formal-lens-bank.md](references/formal-lens-bank.md) before escalating to high-level interpretation.
If the scene anchor is not yet grounded, ask for confirmation or reconstruction before using formal lenses.

For each promising anchor, use a ladder like this:
1. What exactly happened?
2. What detail caught your attention?
3. What did that detail make you feel or think?
4. What changed right before or right after it?
5. Why does this small moment feel heavier than it looks?
6. What about it still feels unclear?

Probe among:
- camera distance or movement
- framing or blocking
- duration, rhythm, or editing
- silence, music, or off-screen sound
- color, light, texture, or space
- props, repeated objects, or recurring gestures
- who is watching whom
- whether the user trusts what the scene is telling them

Advance when you have either:
- five strong anchors across multiple moments
- or enough material to meet the saturation rule through strong cross-links and a live unresolved knot

If the user stays vague, use [references/probing-playbook.md](references/probing-playbook.md).

## Phase 4: Synthesis, Return Visits, and Pressure Test

Goal: synthesize the interview without flattening it, and revisit earlier material in light of later discoveries.

Do not ask the user to invent the analysis lane from scratch.
Generate exactly three candidate angles when possible.

Angle requirements:
- at least one option must be detail-led or form-led
- at least one option must preserve tension, contradiction, or uncertainty if that is present
- no option should float free from concrete anchors already discussed

Ask the user to pick one, blend two, or rewrite one.
Then revisit at least one earlier answer:
- does it still look the same now?
- did another scene change its meaning?
- did your first reaction hide something you now think matters more?

After a direction is chosen, apply one round of pressure:
- What in the film supports this reading most strongly?
- What in the film resists or complicates it?
- Are we turning atmosphere into symbolism too quickly?
- Is this a real problem in the film, or partly a limit in my own entry point?

Advance when one main thread is chosen, revised, or explicitly left open in a productive way.

If the user rejects all three, restate the raw materials and propose a tighter new set.

Before leaving this phase, ensure at least one explicit revisit has happened. If not, ask one.

## Phase 5: Review-Card Confirmation

Goal: convert the conversation into a stable writing substrate.

Draft and confirm six cards:
- aftertaste
- core judgment
- supporting scene or detail
- resistance, uncertainty, or counter-pressure
- personal resonance or real-world link
- closing landing point

Show the cards in compact form and ask for corrections before writing.

Make sure the supporting material is not one-dimensional. It should draw from more than only mood and theme whenever the interview has enough material.

Advance only after the user has confirmed or revised the cards.

## Phase 6: Drafting and Automatic Revision

Goal: turn confirmed cards into prose the user can revisit or publish.

Before drafting, run this internal check:
- at least four threads opened
- at least two different scene anchors from different moments
- at least one covered formal bucket, and at least two unless quick thematic mode was explicitly requested
- at least one pressure-tested judgment
- at least one explicit revisit
- at least one unresolved knot still preserved

If the answer to any required item is no, continue interviewing.

Choose the length band from material density:
- short: strong feeling plus a small set of anchors
- standard: stable main thread plus enough support to sustain it
- deep: several scenes, layered evidence, or a meaningful contradiction worth carrying

Draft in continuous first-person Chinese prose.
After drafting, run one revision pass for:
- paragraph transitions
- tone fidelity
- specificity
- low "report" smell
- alignment with confirmed cards
- preservation of uncertainty where uncertainty is honest
- resistance to flattery or false closure

After Film Echo's own revision, check whether a skill directory named `humanizer-zh` exists in a normal skill root such as:
- the same skill collection directory as `film-echo`
- `$CODEX_HOME/skills/humanizer-zh`
- `~/.codex/skills/humanizer-zh`

If it exists, invoke `$humanizer-zh` on the revised draft as a final post-process pass.
Use it only to remove AI-writing traces such as formulaic transitions, over-neat structure, canned praise, synthetic summary voice, or slogan-like phrasing.
Do not mention or use it during the interview phases unless the user explicitly asks how the workflow is arranged.
Do not let that pass erase:
- first-person ownership
- confirmed scene details and formal observations
- contradiction, resistance, or ambiguity
- the user's actual sharpness, awkwardness, or uncertainty

If the piece starts sounding encyclopedic, cut facts and return to the user's experience.

## Difficult-Film Support

When the user says they do not understand the film, do not treat that as failure.
Use this ladder:
1. Reconstruct one scene as concretely as possible.
2. Notice what the film is doing formally in that scene.
3. Ask what effect that choice had on the user.
4. Offer 2-3 tentative local readings, not a total explanation.
5. Ask which reading feels least forced.
6. Only then connect it to the whole film if enough evidence exists.

For art-house or ambiguous films, a valid essay can be about:
- what the film withholds
- why a scene remains opaque
- the gap between admiration and understanding
- how confusion itself becomes part of the experience

## External Information Policy

Follow "user first, film second."
Only add light interpretive external support after the user's viewpoint is already stable.
Exception: minimal structural grounding is allowed earlier if it prevents blind questioning.
Keep external additions brief and functional:
- scene clarification
- terminology
- short background fact that strengthens a confirmed point
- a narrowly framed alternative reading when the user is stuck

Public-discourse signals are allowed earlier than interpretive commentary, but only as exploratory prompts rather than conclusions.

Never let outside material become the center of the essay or overrule the user's actual viewing experience.
