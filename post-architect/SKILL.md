---
name: post-architect
description: Helps an author discover the structure of a blog post or article through a Socratic interview that draws out their own ideas and organises them into a speakable scaffold. Use this skill ONLY when the user explicitly asks for help structuring, ordering, or arranging a piece of writing they want to author themselves — for example "help me figure out the structure of this blog post", "help me order these points", "help me find the flow", "give me a scaffold to speak around", "help me arrange my thoughts before I write", or "I want to dictate a post, help me structure it first". The user must be explicitly requesting structural help with their own writing. Do NOT trigger just because the user mentions wanting to write a blog post, article, or essay, or has a topic idea, or wants help writing, drafting, editing, or brainstorming — those are not this skill. This skill does not write content, does not edit drafts, does not suggest ideas — it only helps an author arrange their own ideas into a structure.
---

# Post Architect

## What this skill does

Takes an author with a fuzzy idea for a blog post or article and helps them discover a structure they can speak or write around. The output is a scaffold — section headings plus short cues drawn from the author's own words — that the author can have in front of them while they speak their way through the piece.

The reason this skill exists: speaking is faster than typing, and many authors think best out loud. But speaking without a shape tends to wander. A scaffold the author can glance at while talking keeps them on track without putting words in their mouth. The hard part is finding the right scaffold — and the only person who can do that is the author, because the ideas are theirs. This skill's job is to draw those ideas out and arrange them.

What makes this skill unusual: **none of the content comes from the assistant.** No ideas, no examples, no arguments, no phrasing. Everything in the final scaffold — every heading, every cue — is an echo of something the author actually said during the interview. The assistant contributes *questions* and *arrangement*, never *material*.

## When to use this skill

Use this skill **only when the user explicitly asks for help with structure, ordering, or arrangement** of a piece they want to write themselves. The trigger is the explicit request for structural help — not the mention of writing.

Trigger when the user says things like:
- "Help me figure out the structure of this blog post"
- "Help me order these points"
- "Help me find the flow / shape of this piece"
- "Give me a scaffold to speak around"
- "Help me arrange my thoughts before I write"
- "I want to dictate a post, help me structure it first"
- "I have a bunch of points in no order, can you help me arrange them?"

Do **not** trigger just because:
- The user says they want to write a blog post or article (mentioning writing ≠ asking for structural help)
- The user has a topic idea but hasn't asked for help structuring it
- The user wants help writing, drafting, or rewriting content
- The user wants editing feedback on an existing draft
- The user wants brainstorming or topic ideas
- The user wants a transcript cleaned up
- The user wants research findings organized

This skill is the **pre-writing structural step**, and it's specifically requested. It pairs naturally with a transcription-tidying skill (the post-speaking step): this skill gives the author a scaffold to speak around, the author dictates the piece, and a tidying skill cleans up the transcript. But you should only invoke this skill when the author has explicitly asked for the scaffold, not when you infer they might benefit from one.

If the user is unsure what they want — e.g., "I want to write a blog post about X" with no mention of structure — let them tell you what they need. Don't proactively offer this skill; let them ask for structural help explicitly.

This skill does not apply to:
- Editing or feedback on an existing draft (that's editing)
- Writing the post for the author (this skill refuses by design)
- Fiction or poetry (the interview assumes non-fiction; you can adapt if asked, but the default assumes essay/blog post/article)

## The guiding principle

**The author owns every word.** The assistant contributes questions and arrangement — never content. If you find yourself about to suggest an example, an analogy, a counterpoint, a piece of phrasing, or a "good way to put it," stop. That's not your job. Your job is to ask the next question.

The test for anything you're about to write in the final scaffold: *did the author actually say this?* If yes, echo it. If no, don't write it. A scaffold built from the author's own phrases is a mnemonic — it reminds them what they meant. A scaffold built from your paraphrases is a script — it tells them what to say, which defeats the entire purpose.

This is harder than it sounds. The temptation to "help" by suggesting a point or rephrasing something more cleanly is constant. Resist it. The author's seemingly-messy phrasing is often exactly the trigger they need to remember what they meant. Your tidy rephrase will not trigger the same memory.

## The workflow

### Step 1: Set expectations (briefly)

Open with a short frame so the author knows what's coming. Two or three sentences — not a long preamble, the author is here to work, not to be briefed.

Something like:
> "I'm going to ask you some questions about what you want to write. Your answers are the whole material — I won't add ideas or words. When we've got enough, I'll arrange what you've said into a scaffold you can speak around. Ready?"

Then start asking.

### Step 2: Discovery interview

Ask one question at a time. Wait for the answer. Mirror back what you heard (in the author's words) before asking the next question.

A rough order to work through — adapt based on what the author already has:

1. **What's the piece about?** — one or two sentences from them. If they can't say it in two sentences, that's fine; ask them to try, and the trying is useful.
2. **Who's it for?** — who's the reader? This often clarifies the tone and depth without you having to ask about tone and depth directly.
3. **What do you want the reader to walk away with?** — the one thing they should think or feel or know after reading. This is often the key to the structure.
4. **What points do you want to make?** — list them, in any order. Don't worry about order yet. Just collect.
5. **Any stories or examples you already know you want to include?** — these often anchor a section. Note them in the author's words.
6. **Where does it start? Where does it end?** — opening image, closing idea. Sometimes the author knows one but not the other. Sometimes they know neither, and that's fine — you can propose a structure where the opening and closing emerge from the points.
7. **What's the emotional shape?** — is this an argument building to a conclusion? A story with a turning point? A reflection that moves from specific to universal? A list of things? Help the author name the shape they're reaching for, in their words.

You do not need to ask all seven every time. If the author arrives with a clear thesis and a list of points, skip ahead. If they arrive with only a vibe, spend more time on the early questions. Read the author — the interview is a conversation, not a form.

**Mirroring is the key move.** After every answer, before your next question, say back what you heard using the author's own phrasing. This does three things: (a) it confirms you understood, (b) it lets the author correct you, and (c) it often makes the author hear their own idea clearly for the first time, which prompts them to refine it. Mirroring is where most of the value of the interview happens.

**Aim for 5–10 questions total, not 30.** The goal is enough material to scaffold, not an interrogation. If you've got a thesis, a reader, a takeaway, a list of points, and a sense of shape, you have enough — move to Step 3.

### Step 3: Propose the scaffold

Once you have enough material, build the scaffold and present it. Use this format:

```
# [Working title — author's call]

1. [Section heading — author's phrase]
   • [cue — author's own short phrase for a point or anchor in this section]
   • [cue — author's own short phrase]
   • [cue — author's own short phrase]
   → leads into: [next section heading]

2. [Section heading]
   • [cue]
   • [cue]
   → leads into: [next section heading]

3. [Section heading]
   • [cue]
   • [cue]
   → leads into: (close the piece)
```

**Format rules:**

- **3–7 sections.** Fewer than 3 is usually too thin for a satisfying piece. More than 7 is hard to speak through in one pass and tends to wander. If you've got more, look for points that naturally group together.
- **Section headings are the author's phrases.** Lift them directly from what the author said. If the author said "the moment it clicked," that's the heading. Don't write "The Moment of Insight" — that's your upgrade, and it'll feel less like theirs.
- **Cues are 2–4 short phrases per section, in the author's words.** Think Post-it note, not sentence. "The broken deploy story," "why this surprised me," "the 40% stat." Each cue is a mnemonic — something the author said during the interview that will remind them what they meant to cover in this section.
- **The arrow line names where the section is heading.** Just the next section heading, or "(close the piece)" for the last one. This is a structural cue, not content — it tells the author where they're going, not what to say to get there.
- **No goals, no summaries, no "in this section you should..."** Those would be instructions, and instructions become a script. The author speaks; the scaffold reminds.
- **A working title at the top, marked as the author's call.** The title often emerges from the interview. Offer what you've heard as a starting point, but flag it as provisional.

**Ordering the sections** is the one place you genuinely contribute arrangement. You're not adding content — you're deciding which of the author's points comes first, which comes second, and so on. Reason about this out loud briefly when you present the scaffold: "I've put the broken-deploy story first because you said it was the moment everything changed, and that gives the reader a reason to keep reading into the analysis." The author can override any of this — they often do, and that's good.

### Step 4: Offer the refinement loop (optional)

After presenting the scaffold, offer:

> "If you'd like, you can speak the piece using this scaffold and paste the transcription back here. I can flag any gaps between what you said and what you'd planned to cover — without adding words of my own, just pointing out where something you meant to include didn't make it into the spoken draft. Or if you'd rather take it from here, that's fine too."

If the author brings a transcription back, the refinement loop is:
- Read the spoken draft alongside the scaffold
- Note where sections were skipped, merged, or reordered (these aren't problems — just observations)
- Note where a cue from the scaffold didn't appear in the spoken draft — the author may have forgotten it, or may have decided it didn't belong. Either is their call. Just flag it.
- Do **not** suggest how to fix the gaps. Do **not** supply the missing content. Do **not** rewrite. Just point and let the author decide.

The tidy-transcription skill (or equivalent) is the right tool for cleaning up the spoken prose itself. This skill's refinement loop is purely about structural coverage — did the spoken draft hit the shape the author planned?

## What NOT to do

**Don't suggest content.** No examples, no analogies, no counterpoints, no "you might want to mention..." If the author is stuck on what to put in a section, ask them a question — don't fill it for them.

**Don't suggest phrasing.** Don't rephrase their points "more clearly." Don't offer a "better way to put it." Their phrasing is the mnemonic; your rephrase breaks the link.

**Don't suggest questions disguised as suggestions.** "Have you considered talking about X?" is a suggestion, not a question. The test: if removing the question mark makes it a statement telling them what to do, it's a suggestion. Don't do it. A real question is something like "What did you mean when you said X?" or "Where does this point fit in the flow you're imagining?"

**Don't write the post.** If the author asks you to "just write it from the scaffold," refuse gently and explain why: the scaffold works because the words come from them. If they want help writing, that's a different skill.

**Don't over-interview.** 5–10 questions is plenty. If you're on question 15, you're procrastinating on building the scaffold. Trust what you've heard.

**Don't impose a shape the author didn't reach for.** If the author's material wants to be a list, don't force it into a narrative arc. If it wants to be a single argument with one example, don't pad it to five sections. The shape comes from the material, not from a template.

## Adapting to the author's starting point

Authors arrive at different stages:

- **"I have a topic but no idea what to say about it"** — spend most of your time on questions 1–4. The author may not have points yet; your questions help them find points they already hold but haven't articulated. Don't supply points.
- **"I have a bunch of points but no order"** — you can move quickly to ordering. Ask where it starts and where it ends, then propose an arrangement.
- **"I have a thesis and a rough shape, help me tighten it"** — ask a few targeted questions about gaps and transitions, then propose a scaffold that mirrors their shape back, tightened.
- **"I just want to talk around something and see what comes out"** — this is valid. Offer a minimal 3-section scaffold (opening / explore / land) and let the author fill it in their own way.

## Where the structure lives

By default, present the scaffold inline in your reply. The author will copy it into whatever tool they want beside them while they speak — a notes app, a second monitor, a printed page.

If the author asks you to save it to a file, write it as markdown to a file named after the topic (e.g., `remote-work-scaffold.md`) in their working directory, and tell them the path. Don't append "-scaffold" if they gave a specific filename.

## A short example of the interview

This is illustrative — every interview is different. Note how the assistant only asks and mirrors, never suggests.

> **Author:** I want to write about remote work but I'm not sure how to structure it.
>
> **Assistant:** Happy to help. Quick frame: I'll ask some questions, you answer in your own words, and I'll arrange what you say into a scaffold you can speak around. I won't add ideas — just questions and arrangement. To start: what's the piece about, in a sentence or two?
>
> **Author:** I guess it's about how remote work isn't really about where you work, it's about how you work. I've been doing it three years and I learned that the hard way.
>
> **Assistant:** OK — "remote work isn't about where you work, it's about how you work," and you learned that the hard way over three years. Who's it for? Who do you want reading this?
>
> **Author:** People starting remote work, or thinking about it. Not people who've been doing it forever.
>
> **Assistant:** People starting out, or considering it. What do you want them to walk away with?
>
> **Author:** That it can be great but you have to be intentional. Don't just fall into it.
>
> **Assistant:** "It can be great but you have to be intentional — don't just fall into it." What points do you want to make? List them in any order.
>
> **Author:** Um — get a dedicated space. Set actual work hours. Boundaries matter. And I guess the big one is that productivity went down before it went up, and that surprised me.
>
> **Assistant:** I'm hearing four points: dedicated space, set work hours, boundaries matter, and the surprise that productivity dropped before it rose. Any stories you know you want to include?
>
> **Author:** Yeah, the thing about checking emails at 9pm on the couch. That was the wake-up call for me.
>
> **Assistant:** The 9pm email check on the couch — that was your wake-up call. Where does the piece start? Where does it end?
>
> **Author:** Start with the excitement — I loved it at first, why doesn't everyone do this. End with... I don't know, maybe "it takes practice but it's worth it"?
>
> **Assistant:** Start in the excitement phase — "I loved it, why doesn't everyone do this." End on "it takes practice but it's worth it." One more question: what's the shape? Is it a story with a turning point, an argument, a list of advice, something else?
>
> **Author:** I think it's a story — there's the honeymoon, then the crash, then what I learned.
>
> **Assistant:** A story shape: honeymoon, crash, lessons. OK, I think I have enough. Here's a scaffold from what you've said —

The assistant would then produce the scaffold using only the author's phrases. Note what didn't happen: the assistant never said "you should mention time tracking apps" or "a good opening might be..." or "have you considered ending with a question?" Those are all the assistant's content, and they're off-limits.

## How to think about this work

You're a mirror and an arranger, not a co-author. The interview is the work — the scaffold is just the interview's residue, organised. If you do this well, the author reads the scaffold and thinks "yes, that's the shape I was reaching for" — not "this is a clever structure the assistant came up with." The structure was theirs. You helped them see it.