# no-fluff

Enforces brevity and directness in Claude's responses. Kills sycophancy, preamble, filler hedges, format inflation, and trailing questions.

## Why

Claude answers most questions well. It also answers a lot of questions you didn't ask. Ask for a fact, get the fact plus its history, its context, its edge cases, and a "let me know if you'd like more detail" at the end. By the time you finish reading, you've forgotten what you asked.

`no-fluff` fixes the shape, not the content. Claude still knows what it knows. It just stops decorating.

## What it does

Governs response shape on every reply:

- Cuts sycophantic openers ("Great question!"), preamble ("Let me walk you through..."), and trailing solicitation ("Anything else?")
- Matches answer length to question shape (yes/no → one sentence; factual lookup → one to two)
- Strips filler patterns ("It's important to note," "essentially," "hope this helps")
- Defaults to prose. No bullet lists, numbered lists, bold sprinkling, emoji, or headers unless the content genuinely needs them
- Opens up when you ask it to ("explain," "detail," "walk me through," "write me a...")

## What it does not do

- Does not shorten creative writing. A requested poem, story, or essay lives at its natural length.
- Does not remove genuine caveats (medical, legal, financial, safety). Empty hedges go, real warnings stay.
- Does not apply to emotional support conversations. Warmth outranks brevity.
- Does not refuse to expand when asked. Brevity is the default, not a wall.

## Install

Copy the `no-fluff` folder into your Claude skills directory.

Personal (all projects):
```bash
cp -r no-fluff ~/.claude/skills/
```

Project-specific:
```bash
cp -r no-fluff .claude/skills/
```

Skill loads automatically on next conversation.

## Test

After installing, run these prompts. Compare against expected shape:

| Prompt | Expected shape |
|---|---|
| What's the capital of Peru? | One word or one short sentence. |
| Is Python dynamically typed? | One sentence, no history lesson. |
| How do I reverse a list in Python? | The code, one line of context. |
| Explain how HTTPS works. | Two to three sentences. No headers, no bullets. |
| Write me a short poem about winter. | Full poem. No apology, no framing, no "hope you like it." |

If Claude opens with "Great question!" or ends with "Let me know if you'd like more detail," the skill did not load. Check the path and restart the conversation.

## Structure

```
no-fluff/
├── SKILL.md
└── README.md
```

Single-file skill. No scripts, no references, no assets.

## License

MIT
