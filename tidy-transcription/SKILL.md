---
name: tidy-transcription
description: Cleans up verbatim transcribed text (speech-to-text output) into coherent written prose while preserving the author's original words and voice as closely as possible. Use this skill whenever the user provides a raw transcription of spoken text and wants it tidied, cleaned up, turned into a blog post, article, or coherent document, or mentions a transcript, dictation, voice memo, or speech-to-text output that needs polishing. Also use it when the user says they "wrote this by speaking it" or "dictated this" or asks to "clean up", "tidy", "polish", or "fix" transcribed, dictated, or speech-to-text content. Trigger even when the user doesn't use the word "transcription" but the text shows clear signs of being spoken (filler words like um/uh, run-on sentences, false starts, repetition).
---

# Tidy Transcription

## What this skill does

Takes verbatim transcribed speech and turns it into clean, readable written prose while keeping the author's words and voice intact. The goal is a document the author would recognize as *their own* — same ideas, same phrasing, same voice — just with the speech artifacts removed and the grammar smoothed out. Think of it as editing a first draft, not rewriting it.

The reason this matters: people dictate blog posts, essays, and documents because speaking is faster than typing. The output is genuinely their voice. A heavy edit would lose that. So the skill walks a careful line — it removes the noise of speech, but keeps the signal of the author's intent and style.

## When to use this skill

Use this whenever the user provides text that is clearly the output of speech-to-text transcription and wants it cleaned up. Signs that text is transcribed:

- Filler words: "um", "uh", "er", "ah", "like" (when used as filler), "you know", "I mean", "sort of", "kind of" (when used as filler)
- Run-on sentences held together with "and" or "so"
- False starts: "I went to, I went to the store yesterday"
- Repeated words for emphasis that aren't intentional: "so so so what happened was"
- Sentence fragments that were complete thoughts in speech but need punctuation in writing
- Missing punctuation, capitalization, or paragraph breaks
- Words that are homophones of what was meant (there/their, your/you're) — transcription errors

If the text is already clean written prose, this skill isn't needed. If the user wrote it by typing, don't apply this skill — they may have typed it carefully and don't want it changed.

## How to tidy the text

### The guiding principle

The author's words are the point. Edit *minimally* — only change what needs changing to make it read well. Don't improve their vocabulary, don't formalize their tone, don't restructure their arguments. Every change should be defensible: "this is obviously what they meant to say."

### What to do

**Remove filler words.** "Um", "uh", "er", "ah", "like" (when filler), "you know", "I mean", "sort of", "kind of" (when filler) — these are speech artifacts. The author didn't choose them; they just happened. Drop them silently.

**Collapse false starts and stutters.** "I went to, I went to the store" → "I went to the store." "The the the problem is" → "The problem is." These are speech errors, not authorial choices. The author meant the clean version.

**Fix grammar and agreement.** Subject-verb agreement, pronoun agreement, tense consistency, article usage. "They was going" → "They were going." This is the moderate cleanup level — fix what's clearly wrong, don't rewrite what's stylistic.

**Smooth run-on sentences.** Speech runs on with "and" and "so" where writing would use periods or semicolons. Break these into sentences. But don't break the author's logic — just the punctuation.

**Fix obvious transcription errors.** Wrong homophones ("there" when "their" was meant), words that sound similar but don't fit ("definitely" vs "defiantly"), missing words that were clearly dropped. Use the context to infer what was meant.

**Punctuate properly.** Add periods, commas, question marks, and capitalization that match the meaning. Speech doesn't have punctuation; writing does.

**Add paragraph breaks.** Break at natural topic shifts. This makes the document readable. Use your judgment about where the author's flow has natural breaks — usually when they move to a new idea, example, or argument.

**Suggest a title.** If the document doesn't have one, propose a title that captures what it's about. Mark it clearly as a suggestion (e.g., put it at the top with a note that the user can change it).

### What NOT to do

**Don't change the author's word choices.** If they said "stuff," don't write "items." If they said "gonna," keep "gonna" or, at most, write "going to" — but be consistent and don't upgrade to fancier synonyms. Their vocabulary is their voice.

**Don't formalize the tone.** If they're conversational, keep it conversational. This is a blog post or essay in their voice, not an academic paper. Contractions are fine. Casual phrasing is fine.

**Don't restructure their argument.** Don't reorder paragraphs, merge points, or "improve" their logic. Their structure is their structure. You're tidying, not editing for argument quality.

**Don't add headings within the body** unless the author clearly indicated a section break (e.g., they said "OK, now moving on to X" or there's an obvious shift that a heading would clarify). Otherwise, let the paragraphs flow.

**Don't add content.** No new sentences, no clarifying examples, no transitions that weren't there. If something is unclear, leave it unclear — that's the author's call to make.

**Don't remove content** unless it's pure filler or false start. If they repeated themselves for emphasis, even accidentally, keep it. If they went on a tangent, that's their choice.

## How the text gets to you (and how to give it back)

The transcription can arrive two ways. They're not equivalent — the way the text came in determines what the user can do with the result, so match their delivery method.

### 1. The text is pasted into the conversation

This is the "quick one-off" path. Output the tidied text directly in your reply. Don't wrap it in commentary, don't explain what you changed unless asked, don't ask whether they want a file — just give them the cleaned-up document as the body of your message. If they want it saved, they'll say so.

### 2. The text is in a file (txt, md, docx, etc.)

This is the more powerful path, and it's worth gently encouraging when the user has a longer document. The reason: when you tidy a file in place, the user can run `git diff` to see exactly what you changed, line by line. That diff is the audit trail — they can review every edit, revert anything they don't like with `git checkout`, and commit only when they're happy. This matters a lot for a skill whose entire purpose is "change my words as little as possible." A diff lets them verify that.

**Default: edit the file in place.** Read the file, tidy the contents, write the tidied version back to the *same* path. This makes `git diff` work naturally. Do not write to a sibling file, do not append "-tidied" to the name, do not ask "where should I save it?" — just overwrite the original. The user's version control (if any) holds the original; that's the whole point.

**Exception: if the user says they want to keep the original** — phrasing like "keep the original", "don't overwrite", "save it as a new file", "make a copy" — write the tidied version to a sibling instead. Pick a name like `<original-stem>-tidied.<ext>` (e.g., `blog.md` → `blog-tidied.md`). If they don't specify a name, propose one and use it.

**For docx specifically:** preserve the .docx format — write back a real .docx, not markdown. If your tooling can't produce docx, fall back to writing the tidied text as a sibling .md file and tell the user that's what you did.

**After writing the file:** tell the user briefly that you've tidied it in place (or written to a sibling), and that they can `git diff` to review the changes. One line is enough — don't narrate the edits. If they want a summary of what changed, they'll ask.

### Format preservation

Match the format the user gave you. Markdown in → markdown out. Plain text in → plain text out. Docx in → docx out. Don't convert formats unless asked. If the original had no markdown (plain .txt), don't add markdown formatting — just clean the prose and write plain text back.

### Title handling

If the document doesn't have a title and you're adding one, **always mark it as a suggestion**, not as part of the document. Put it at the top in this form:

```
# Suggested title: <your title here> — feel free to change
```

Or, if the file is plain text (not markdown):

```
[Suggested title: <your title here> — feel free to change]
```

This matters because the title is the one place you're *adding* content rather than tidying. Marking it clearly keeps it separable from the author's actual words — they can delete it, change it, or accept it without it feeling like you put words in their mouth. Don't just write a bare `# Title` with no marker; that looks like it was always there.

### Only mention changes if asked

Don't list what you changed unless the user asks for a summary. The diff (or the output itself, for pasted text) speaks for itself. If they want to know what you changed, they'll ask.

## Edge cases

- **Strong emotion or emphasis in speech:** If the author repeats something for emotional effect ("it was awful, just awful"), keep it. That's authorial intent, not a stutter. The test: would removing it change the meaning or feeling? If yes, keep it.

- **Direct quotes or dialogue:** If the author is quoting someone else, clean only obvious transcription errors within the quote. Don't change the quoted person's words beyond fixing clear errors.

- **Technical terms or jargon:** Don't "correct" these. If the transcription has " Kubernetes" or " pedagogical," keep it. If you're unsure whether a word is a real term or a transcription error, leave it and maybe flag it.

- **Numbers and dates:** Fix obvious transcription errors ("too thousand and twenty" → "2020") but be careful — don't assume. If unclear, keep what's there.

- ** profanity:** Keep it. It's the author's voice.

- **The author explicitly says something self-referential** like "um, let me think" or "wait, no, what I mean is" — collapse these into the cleaned-up version. "What I mean is X" usually just becomes "X" or "In other words, X" if it genuinely clarifies.

## A short example

**Input (transcribed):**
> so um I was thinking about this the other day and I think I think the thing about you know remote work is that it's not really about where you work it's about how you work and um so so what happened was I started working from home like three years ago and I was like this is great I love this but then after a while I realized that I was you know I was actually less productive not more

**Output (tidied):**
> # Suggested title: Remote Work — feel free to change
>
> I was thinking about this the other day. I think the thing about remote work is that it's not really about where you work — it's about how you work. I started working from home like three years ago, and at first I thought, "This is great, I love this." But after a while, I realized I was actually less productive, not more.

Note what happened: "um" and "you know" dropped, false starts collapsed, run-on broken into sentences, "like three years ago" kept (it's the author's voice), punctuation added. The author's words and ideas are all there — just cleaned up.

## How to think about this work

You're a careful editor, not a co-author. The document belongs to the author. Your job is to remove the artifacts of speech and let their actual meaning and voice come through clearly. If you do this well, the author reads the result and thinks "yes, that's what I meant" — not "wow, this sounds better than what I said."