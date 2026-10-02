---
name: "ste-write"
description: "Write anything — explanations, summaries, emails, messages, status updates, docs, READMEs, PR descriptions, rewrites — in simplified technical English (ASD-STE100 style, ~80% strict), with ASCII diagrams in chat/console or SVG in docs, and an interactive HTML page offer for large explanatory topics. Use for write, draft, explain, summarize, reply, document, rewrite, 写, 讲解, 总结, 回复."
---

# STE Write

People spend more and more of their time reading what a model wrote. Reading is now the bottleneck, not writing. This skill makes every piece of writing cheap to read, whatever its type, in three ways:

1. **Write in ASD-STE100 style.** STE is the controlled language built for aerospace maintenance manuals. It forces short sentences, one meaning per word, active voice, and one instruction per sentence. Text in this style reads fast and is hard to misunderstand.
2. **Draw diagrams** when the content has a shape. A flow, a tree, a table, or a chart is parsed faster than a paragraph that says the same thing.
3. **Offer an interactive HTML page** when an explanatory topic is large enough to deserve one.

The goal is a reader who understands on the first pass. Accuracy comes first: a short sentence that drops a qualifier is wrong, not simple.

## Part 1 — Writing rules (apply to every type)

Aim for about 80% of the full specification. Keep the rules that make text clear. Drop the rules that only make sense for a maintenance manual (the 900-word dictionary, UPPERCASE keywords, strict WARNING/CAUTION blocks). Use the reader's own technical terms freely — "gradient", "mutex", "p99 latency" are fine when the reader knows them.

### Sentences

| Rule | Limit | Why |
|---|---|---|
| Instruction sentence | ≤ 20 words | One action, read once, done |
| Descriptive sentence | ≤ 25 words | Longer sentences hide the subject |
| Instructions per sentence | 1 (except truly simultaneous actions) | "Do A and B" hides the order |
| Noun cluster | ≤ 3 words | "model training job queue config" needs unpacking |
| Paragraph | ≤ 6 sentences, one topic | A new topic gets a new paragraph |

### Voice and verb forms

- Use the active voice. "The scheduler starts the job", not "The job is started by the scheduler".
- Use the command form for instructions and asks. "Close the file", not "The file should be closed" or "You'll want to close the file".
- Use simple tenses: simple present, simple past, simple future, infinitive, past participle as an adjective ("the closed file").
- Avoid progressive (-ing) and perfect forms unless the -ing word is part of a fixed name ("landing gear", "load balancing").
- Use the passive only in descriptive text, and only when the actor is unknown or does not matter.

### Words

- Use the same word for the same thing every time. Do not vary for style. If it is a "node" in paragraph one, it is a "node" in paragraph nine.
- One word, one meaning. Do not use "close" to mean "near" and "shut" in the same text.
- Keep articles and determiners: "the", "a", "this". Telegraphic text is harder to read, not easier.
- Replace long words with short approved ones:

| Avoid | Use | Avoid | Use |
|---|---|---|---|
| commence, initiate | start | utilize, leverage | use |
| ensure | make sure | terminate | stop |
| prior to | before | subsequently | then, after |
| in order to | to | in the event that | if |
| approximately | about | a number of | some, several |
| sufficient | enough | numerous | many |
| additional | more | perform | do |
| indicate, demonstrate | show | require | need |
| obtain | get | modify | change |
| facilitate | help | implement | do, build, add |
| replenish | fill | regarding | about |
| reach out, touch base, circle back | contact, talk, follow up | at your earliest convenience | by <date> |

### Tone: STE removes filler, not warmth

An email or message in STE is still friendly. Keep one short greeting and one short sign-off. Say "Thanks for the quick review." Do not say "I hope this email finds you well" or "Just wanted to reach out to see if". Hedge only when the uncertainty is real, then state it plainly: "I am not sure the fix covers the retry path. I will check by Friday." Do not soften an ask into a question when it is an ask.

### Risk and order

When an action is dangerous or order matters, give the command first, then the reason, as two sentences:

> Do not run the migration before the backup finishes. The migration drops the old table.

### Chinese

When the user writes in Chinese, apply the same rules in Chinese: 一句一个动作，主动语态，同一事物同一词，每句不超过约 30 字，每段一个主题，先说结论或请求. Keep English technical terms as the user uses them. Match the user's formality (您/你) and keep it consistent.

### Writing in the user's name

When the text will be sent as the user (email, message, PR, reply): add no facts the user did not give. Put unknowns in [brackets] for them to fill. Keep their language, their name, and their sign-off. Match the formality of the thread they are replying to.

## Part 2 — Shape by writing type

The rules above fix the sentences. The shape below fixes the order, so the reader gets the point in the first line. Pick the row that matches; combine rows when a piece is two things (a status email is "email" plus "status update").

| Type | Shape (in order) | Target length | Default visual | HTML offer |
|---|---|---|---|---|
| Explanation, teaching, ELI5 | Answer. Mechanism, one paragraph per idea. One small hand-checkable example. Diagram. Limits or gotchas. | As long as needed | Flow, tree, or table | Yes, if large |
| Summary (paper, article, thread, meeting, transcript) | One-sentence verdict. 3–7 key points, one sentence each. What changed or what to do. Source and date. | ≤ 1/10 of the source | Table or timeline if the source has one | Only if asked |
| Email | Subject line that states the ask or the news. First sentence: the ask or the news. Context ≤ 3 sentences. Next step with owner and date. One-line sign-off. | ≤ 150 words | Small table only when comparing options | Never |
| Chat message (Slack, WeChat, Teams) | The ask or news in sentence one. Context in one or two lines. Question or next step last. | ≤ 60 words | None | Never |
| Status update, weekly report | Headline with state (on track / at risk / blocked). Done. Next. Blocked and asks. Numbers in a table. | ≤ 1 screen | Table; bar chart for quantities | Never |
| Doc, spec, README, how-to, runbook | Purpose in two sentences. Prerequisites. Numbered steps, one action each. How to verify. Troubleshooting. | As long as needed | Flow or architecture diagram | Yes, for long how-tos and references |
| PR description, changelog | What changed. Why. How to test. Risk and rollback. | ≤ 200 words | None, or a before/after table | Never |
| Commit message | Imperative subject ≤ 72 chars. Blank line. Why, not what, in 1–3 sentences. | Short | None | Never |
| Rewrite or tighten the user's text | Keep every fact, number, name, and the user's voice choices. Cut filler. Reorder so the point comes first. Show the main changes in one line if asked. | Shorter than the input | Keep theirs | Never |

Use vertical lists for steps, options, and conditions. Use a table whenever three or more things are compared on the same attributes.

### Example rewrite — instruction

**Before:** It is imperative that the operator ensures the hydraulic reservoir is replenished prior to commencing operation, as insufficient fluid levels may potentially result in damage being caused to the pump.

**After:** Make sure that the hydraulic reservoir is full before you start the operation. A low fluid level can damage the pump.

### Example rewrite — email

**Before:**

> Subject: Quick question
>
> Hi Priya, hope you're doing well! I just wanted to reach out and touch base regarding the eval pipeline, as we've been seeing some flakiness in the nightly runs that could potentially be related to the recent changes that were made to the scheduler, and I was wondering if you might have some time this week to take a look?

**After:**

> Subject: Nightly eval runs fail about 1 in 5 since the scheduler change
>
> Hi Priya,
>
> Can you look at the nightly eval failures this week? Since the scheduler change on Monday, about 1 in 5 runs fails at the collect step. Logs are in [link]. If you can confirm the cause by Thursday, I will own the fix.
>
> Thanks,
> [Your name]

## Part 3 — Diagrams and charts

Add a diagram whenever the content has a shape: a sequence (flow), a hierarchy (tree), a comparison (table), change over time (timeline or line chart), quantities (bar chart), or states and transitions (state diagram). One idea per diagram. Caption each diagram with one sentence that says what to look at.

Do not draw a diagram for a single fact, a two-sentence answer, or a chat message. A diagram that repeats the text adds reading, not understanding.

### Pick the format from the output medium

| Medium | Format |
|---|---|
| Chat reply, terminal, console, markdown file, commit, PR, code comment | ASCII in a fenced code block |
| Doc, artifact page, HTML, slide, anything rendered | Inline SVG |
| Email or messaging app | No ASCII art (proportional fonts break it). Use a table or a numbered list. |
| A comparison on fixed attributes, in any medium | Table |

When the medium is unknown, use ASCII; it degrades to readable text everywhere.

### ASCII rules

- Put the diagram in a fenced code block so the font is monospace.
- Keep width ≤ 80 columns. Wrap labels rather than widen the box.
- Use box-drawing characters (`┌ ─ ┐ │ └ ┘ ├ ┤ ┬ ┴ ┼`) and arrows (`→ ← ↑ ↓ ▶`). Plain `+--+` and `-->` are acceptable when the target may not render Unicode.
- Label every box and every arrow that is not obvious.
- Check alignment before you send: every vertical line must sit in the same column on every row. Count characters; misaligned ASCII is worse than no diagram.

Templates:

```
Flow                         Tree                    Bar chart
┌────────┐   ┌────────┐      root                    A ████████████ 12
│ client │──▶│ server │      ├── child 1             B ██████ 6
└────────┘   └───┬────┘      │   └── leaf            C ███ 3
                 ▼           └── child 2
             ┌────────┐
             │  db    │      Timeline
             └────────┘      2019 ──●──── 2022 ──●──── now
                                  v1          v2
```

### SVG rules

- Inline the SVG. Set a `viewBox`; do not fix pixel width, so it scales to the container.
- Text only; no raster images, no external fonts.
- Font size ≥ 12 in viewBox units. Labels sit beside shapes, not on top of busy lines.
- Use `currentColor` for strokes and text, and a small palette of 2–4 fills, so the diagram works in light and dark themes.
- Keep each SVG small (under ~150 lines). Split a large picture into two diagrams.
- If an `artifact-diagramming` or `dataviz` skill is available, load it before drawing for colour, mark, and layout rules.

### Charts

For numbers, choose by question: bar for "how much per category", line for "how does it change", table for "exact values". Always put units on the axis or in the caption. Round to the precision the reader needs, not the precision you have.

## Part 4 — Interactive HTML page

A web page is the strongest format for explanatory content: sections with navigation, diagrams that animate, parameters the reader can change. Build one when:

- the user asks for HTML, a page, a site, or "something interactive", or
- the piece is an explanation, doc, or reference (see the HTML column in Part 2) with three or more sections or two or more diagrams, or the topic has a parameter worth playing with (a learning rate, a queue depth, a tax bracket).

If the user did not ask and the topic qualifies, give the normal STE text first and end with one line: "Do you want this as an interactive HTML page?" Do not offer for emails, messages, commits, PRs, status updates, or short summaries; those are read once and sent.

When you build the page:

- One self-contained HTML file: inline CSS and JS, data: URIs for any image, no external requests except fonts.
- Reuse the STE text and the SVG diagrams. The page is the same content with more room, not a new explanation.
- Add interaction that teaches: a step-through for a process, a slider for a parameter, hover notes on a diagram, a toggle between "before" and "after". Skip decoration that does not teach.
- Make it work at phone width and in dark mode.
- If an `Artifact` tool and an `artifact-design` skill are available, load the skill, then publish the page with the tool so the user can reopen and share it. Otherwise deliver the file.

## Self-check before you send

- Is the ask, the news, or the answer in the first sentence?
- Any sentence over 20 words (instruction) or 25 words (description)? Split it.
- Any passive voice in an instruction or ask? Any -ing or perfect verb? Change it.
- Any word from the "Avoid" column, or any filler opener? Remove it.
- Did the same thing get two names? Pick one.
- Did a short sentence lose a condition, number, unit, or exception that changes the meaning? Put it back.
- Writing as the user: did I add a fact they did not give? Bracket it instead.
- Does every diagram have a caption, and do its vertical lines align? Is the format right for the medium?
- Is this an explanation or doc big enough to offer an HTML page? If yes, offer in one line. If it is an email or message, do not offer.