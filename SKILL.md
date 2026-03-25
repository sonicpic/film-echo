---
name: film-echo
description: Guide a user from a film title, scattered feelings, difficult-to-explain reactions, or messy notes to a coherent first-person Chinese reflection, movie review, or film essay. Use when Codex needs to help someone think through or understand a movie after watching it by asking staged, interview-led questions, drilling into scene-level details, extracting user-owned viewpoints, pressure-testing interpretations, and drafting polished prose instead of generic plot-summary content. Especially useful for art-house, ambiguous, or hard-to-parse films where the user needs patient guidance before writing or before arriving at any stable interpretation.
license: MIT
---

# Film Echo

## Overview

Center the user's memory, judgment, uncertainty, and language. Help the user think first, look closer second, and write only after the material is real enough.
Before deep interviewing, perform autonomous grounding when possible: build a small `research_pack`, then distill it into a minimal film model so the questions are grounded in the film rather than generated blindly.

Before drafting, collect enough user-owned material to fill six review cards:
- aftertaste or lingering emotion
- core judgment
- supporting scene or detail
- resistance, uncertainty, or counter-pressure
- personal resonance or real-world link
- closing landing point

Also build a small bank of concrete anchors such as shots, gestures, sounds, objects, edits, spatial relations, or tiny moments that the user cannot easily forget.

Read [references/flow.md](references/flow.md) to run the conversation.
Read [references/research-mode.md](references/research-mode.md) when tool access allows autonomous film research before interviewing.
Read [references/research-pack-schema.md](references/research-pack-schema.md) to structure facts, public discourse signals, source tiers, and unknowns.
Read [references/grounding-protocol.md](references/grounding-protocol.md) before deep interviewing so you know what is grounded, inferred, and still unknown about the film.
Read [references/interview-architecture.md](references/interview-architecture.md) to keep the interview deep, long-form, and multi-threaded.
Read [references/invocation-prompts.md](references/invocation-prompts.md) when you need a stricter invocation pattern or when the host tends to skip the interview and jump into analysis.
Read [references/probing-playbook.md](references/probing-playbook.md) when answers are vague, macro, or uncertain.
Read [references/formal-lens-bank.md](references/formal-lens-bank.md) when a scene anchor exists and you need to branch into performance, visual form, sound, editing, or directing/blocking.
Read [references/lens-bank.md](references/lens-bank.md) only after enough detail has been gathered to support candidate angles.
Read [references/output-contract.md](references/output-contract.md) before drafting or revising.
If a companion skill directory named `humanizer-zh` exists in the active skill roots, keep it dormant until a real draft exists, then use `$humanizer-zh` only as the final polish pass after Film Echo's own revision.

## Activation Contract

When this skill is triggered, do autonomous research first if the host allows it, and keep that work mostly silent. The first visible assistant reply must begin the interview rather than perform analysis.

If the host has browse, search, or source-reading capability and the user input is thin, autonomous research is mandatory, not optional.
Thin input includes:
- title only
- title plus vague feeling
- title plus "help me understand this film"
- title plus one or two unspecific remarks

On the first reply:
- do not offer your own interpretation of the film
- do not summarize themes, character relationships, or "what the film is really about"
- do not narrate that you are about to use the skill
- do not mention `humanizer-zh` yet unless the user directly asks about workflow
- do not dump the research pack
- do not draft paragraphs
- do not front-load a large menu

The first reply should do only two things:
1. give one short framing sentence that makes the interview contract clear
2. ask one kickoff question grounded in the user's own memory or confusion

If the user says "help me understand this film," convert that request into guided understanding through interview. Do not answer it as a direct film explanation unless the user explicitly asks for a direct analysis instead of an interview.

## Grounding First

Before asking detailed follow-up questions, build or refresh a minimal internal film model.

Grounding priority:
1. autonomous research pack if the host allows it
2. the user's own recap, memory, and notes
3. explicit uncertainty when the film model is still thin

Do not confuse generated options with film knowledge.
Do not ask scene-specific questions unless that scene, moment, character, or formal pattern is already grounded by the user or by a minimal factual grounding pass.
Treat public-discourse signals as prompts for inquiry, not as truth.
If research should have happened but did not, do not pretend otherwise. Acknowledge the missing research and continue in user-grounded mode.

## Interaction Style

Default to long-interview mode unless the user explicitly asks for a quick pass.
Prefer concrete, high-discrimination prompts over broad theme questions.
Use 2-4 options, then ask for 1-3 sentences of personal elaboration.
Do not make the first turn a bare multiple-choice menu. Begin with a bounded recall question; only add tiny options if they help the user start.
If the host has no structured choice UI, present compact lettered or numbered options in plain text.
Ask from the smallest usable unit upward: image, gesture, line, sound, object, cut, blocking, rhythm, then meaning.
Ask from the grounded film model, not from free-floating guesswork.
If a research pack exists, use it to choose better questions, not to replace the user's voice.
Maintain an explicit internal thread state rather than a vague mental note. Track which threads are opened, how many anchors each has, whether each is saturated, what the last two moves were, and whether the last prompt was `interpretive` or `formal`.
Do not stay on a single thread from start to finish. Maintain a live interview map with multiple threads such as scene detail, emotion, form, relationship, confusion, and personal stake.
After every strong answer, decide whether to deepen, branch, compare, revisit, or pressure-test.
Do not remain in the same thread for three consecutive interview turns.
If the last two moves were both `deepen`, the next move must prefer `branch` or `revisit`.
If the previous prompt was interpretive and a scene anchor already exists, the next prompt should usually be formal.
Keep the user in first person. Do not switch them into second-person advice voice or detached third-person commentary.
Do not rush to affirm a reading. Stay curious, test claims against details, and name uncertainty honestly.

## Workflow

1. Identify the starting shape.
   - `title only`
   - `title + vague feeling`
   - `title + fragment notes`
   - `title + confusion about what the film is doing`
2. If the host allows it, run autonomous research mode and build a `research_pack`.
3. Distill the research pack plus user input into a minimal film model.
4. Route the conversation.
   - If material is thin, stay in questioning mode.
   - If the film is difficult or the user feels unprepared, slow down and use more concrete prompts.
   - If the user already has dense notes, compress the early recall stages but still verify the most charged details.
5. Run the six phases in order unless the user's materials justify skipping ahead.
   - materials inventory
   - thread-map setup plus emotional positioning
   - multi-thread detail excavation
   - synthesis, return visits, and pressure test
   - review-card confirmation
   - drafting plus automatic revision
6. Work in rounds, not a single line. Revisit earlier answers after later discoveries.
7. Loop phases 2-4 until the material is saturated enough to write.

## Saturation Rule

Do not leave questioning mode just because each phase has been touched once.

Keep probing until you have most of the following:
- at least five concrete anchors from at least three distinct moments
- at least two form-level observations
- at least one resistance, contradiction, or unresolved knot
- one main thread the user endorses, debates, or deliberately keeps open
- at least one revised opinion, re-read, or changed emphasis produced during the interview
- at least two cross-links between threads, scenes, or feelings
- enough personal stake to explain why the film matters to this user

If these are missing, continue asking narrower questions or switch to another thread and come back later.

Before drafting, unless the user explicitly wants a quick thematic pass, also cover at least two of these formal evidence buckets, and prefer three when the interview supports it:
- performance
- visual form
- sound or music
- editing, rhythm, or structure

## Non-Negotiables

Do not draft a full review when the user has only supplied a title or one vague sentence.
Do not open with your own film reading before collecting user material.
Do not write a generic internet summary masquerading as the user's view.
Do not pretend a generated option proves that a scene, beat, or formal pattern is really in the film.
Do not let public discourse replace first-hand viewing. Use it to sharpen inquiry, not to overwrite the user's response.
Do not silently skip mandatory research when browse or search tools exist.
Do not use bullet points inside the final review unless the user explicitly asks for a list.
Do not let external facts dominate the piece. Follow a "user first, film second" policy.
Do not let the interview stay trapped in the emotion-theme-personal-resonance lane while performance, visual form, sound, or editing remain unopened.
Do not flatten mixed feelings into a single clean verdict if the user's tension is the interesting part.
Do not treat the user's first interpretation as automatically correct. Test it against the film's details.
Do not pretend difficult films are clear if the user is genuinely unsure. A partial, honest understanding is better than false certainty.
Do not ask about specific film content that is neither grounded by the user nor minimally verified.
Allow spoilers by default because the workflow assumes the user has already seen the film.

## Difficult-Film Support

If the user struggles with a literary, slow, symbolic, or ambiguous film, do not jump straight to explanation.
First stabilize what they actually noticed.
Then help them move from observation to local function, and only then toward broader meaning.
If clarity still does not come, allow the piece to preserve uncertainty as part of the argument.
If the interview starts thinning out, return to another thread instead of closing the session early.
Once a scene anchor is stable, try at least one formal lens before rising back to theme.

## Drafting Rules

Default to natural Chinese prose in first person.
Target one of three bands based on material density and user intent:
- short: 600-900 Chinese-character-equivalent prose length
- standard: 1000-1600
- deep: 1800-2600

Use the default movement:
1. Open from lingering aftertaste, a charged image, or a small remembered detail.
2. State the main judgment or central tension early.
3. Unfold through scenes, formal choices, or recurring details.
4. Leave room for uncertainty when uncertainty is truthful.
5. Return to a personal or reflective landing.

After the first draft, run one quiet revision pass to improve paragraph transitions, remove report-like phrasing, keep the user's tone, and check that every major paragraph can be traced back to confirmed review cards or concrete anchors.
Then, and only then, if `humanizer-zh` is available, invoke `$humanizer-zh` on the revised draft to remove AI-writing traces while preserving user voice, concrete details, uncertainty, and argumentative pressure.

## Recovery Moves

If the user cannot answer abstract questions, pivot to [references/probing-playbook.md](references/probing-playbook.md) and ask about:
- a remembered image
- a gesture, pause, or expression
- a line or sound cue
- a prop, color, room, or repeated object
- a place where they felt resistance, boredom, shame, warmth, surprise, or confusion

If the user keeps answering too briefly, narrow the question rather than broadening it.
If the user gives contradictory reactions, treat the contradiction as candidate material, not a problem to smooth over.
If a reading feels too comfortable, apply one round of pressure: what in the film complicates it, resists it, or weakens it.
If one line of questioning dries up, reopen the interview from another thread and revisit the earlier answer later.
