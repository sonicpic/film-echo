# Film Echo Invocation Prompts

## Contents

- Core Template
- Chinese Client Template
- Chinese Understanding Template
- Search-First Template
- Chinese Search-First Template
- Understanding-First Template
- Notes-Already-Prepared Template
- Quick Version Template
- Humanizer Add-On
- Usage Notes

Use these prompts when the host tends to ignore Film Echo's interview flow and jump straight into explanation or analysis.

## Core Template

Use this when you want the safest default behavior:

```text
Use $film-echo in strict interview mode.
Do not start with your own interpretation of the film.
Do not summarize themes, character relationships, or what the film is "really about" in the first reply.
Do not begin with a large menu of choices.
Start with one bounded recall question based on my own viewing memory, confusion, or emotional residue.
Keep the conversation as a long-form, multi-round interview.
Keep asking until the material is saturated enough to write.
Only draft after enough detail, contradictions, and personal stakes have been collected.
```

## Search-First Template

Use this when the host supports browsing or search and you want to force research before the interview:

```text
Use $film-echo in strict research-first interview mode.
If browse or search tools are available, you must run a compact search pass before the first visible reply.
Build a small research pack first, then begin the interview.
Do not skip research when I have only provided the film title or a very thin reaction.
Do not show me a research dump first; start the visible conversation with one bounded recall question.
```

## Chinese Client Template

Use this when the current host responds better to direct Chinese instructions:

```text
使用 $film-echo，并严格按照采访式流程执行。
第一条回复不要先讲你对电影的理解，不要总结主题、人物关系或“这部电影真正想说什么”。
第一条回复也不要上来给我一大堆选项。
请先用一句很短的话说明：你会先通过我的观影记忆来理解这部电影。
然后只问我一个有边界的问题，从我的记忆、困惑、情绪残留里切入，比如一个画面、一个声音、一个动作、一个没看懂的地方。
之后保持长时间、多轮、深度采访；不要单线推进，要反复追问、分叉、回访、交叉印证。
在细节、矛盾、形式感、个人关联还不够之前，不要写总结，不要写影评正文。
只有在材料真正饱和之后，才允许进入整理和成稿。
```

## Chinese Search-First Template

Use this when the current host is Chinese-first and you want to force online research before interviewing:

```text
使用 $film-echo，并严格按照“先 research、后采访”的模式执行。
如果当前环境支持联网搜索或网页读取，在我只给出片名、模糊感受，或说“帮我理解这部电影”时，你必须先做一轮简短搜索，建立 research pack，再开始采访。
不要跳过 research，也不要假装自己已经查过。
第一条可见回复不要先输出分析摘要，也不要先把 research 结果整段倒给我。
请在完成 research 后，直接用一个有边界的问题，从我的观影记忆、困惑或情绪残留切入。
```

## Chinese Understanding Template

Use this when the user says they want help "understanding" a film:

```text
使用 $film-echo，帮我“理解”这部电影，但不要立刻进入讲解模式。
我不要你先输出自己的观点，我要你先采访我。
请从我的观影记忆开始，只问我一个问题：一幕画面、一个声音、一个动作、一个人物瞬间，或者一个我没看懂的地方。
然后根据我的回答继续深挖，反复追问细节、形式、情绪、矛盾和变化过的想法。
在采访足够深之前，不要总结这部电影，不要替我下判断。
如果可用，$humanizer-zh 只能在最终成稿和修订完成后再用，不能提前介入采访过程。
```

## Understanding-First Template

Use this when the user says they want to "understand" a film, but you still want Film Echo to interview first:

```text
Use $film-echo to help me understand this film through a deep interview, not through an immediate explanation.
Do not tell me your reading first.
Begin from my own memory: ask me for one scene, one confusing point, or one feeling that stayed with me.
Then keep probing scene details, formal choices, contradictions, and my changing reactions before offering any synthesis.
```

## Notes-Already-Prepared Template

Use this when the user already has many fragments or diary notes:

```text
Use $film-echo.
I already have rough notes, but do not jump straight to writing.
First summarize my fragments back to me, then interview me further from the most charged details.
Revisit and pressure-test my first thoughts instead of treating them as final.
Only write after the interview is deep enough.
```

## Quick Version Template

Use this only when the user truly wants a shorter flow:

```text
Use $film-echo in short mode.
Still begin with one memory-based question instead of direct analysis.
Keep the interview shorter, but do not skip the interview entirely.
Do not draft until you have enough user-owned material to avoid a generic review.
```

## Humanizer Add-On

Append this only when you want the final text polished with the other skill:

```text
If $humanizer-zh is available, do not use it during the interview.
Use it only after Film Echo has completed its own draft and revision pass.
Keep my first-person voice, concrete details, uncertainty, and argumentative tension intact.
```

## Usage Notes

- If the host often defaults to direct explanation, prefer the `Core Template` or `Understanding-First Template`.
- If the host often skips browsing even when tools exist, prefer the `Search-First Template` or `Chinese Search-First Template`.
- If the host is Chinese-first or tends to ignore English control prompts, prefer the `Chinese Client Template` or `Chinese Understanding Template`.
- If you invoke both skills manually, write `$film-echo` first and mention `$humanizer-zh` only as a post-draft step.
- If the first reply still begins with interpretation, interrupt and restate the contract more sharply:

```text
Stop. Do not analyze the film yet.
Use $film-echo in interview mode.
Ask me one bounded question from my own memory or confusion first.
```

Chinese fallback:

```text
停，不要先分析这部电影。
使用 $film-echo 的采访模式。
先根据我的记忆或困惑，只问我一个有边界的问题。
```
