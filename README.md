# no-fluff

Keeps Claude's responses on the asked question. Cuts sycophancy, preamble, filler, drift into unasked topics, and trailing solicitation. Length is a consequence, not a target.

## Why

Claude answers most questions well. It also answers a lot of questions you didn't ask. Ask for a fact, get the fact plus its history, its context, its edge cases, and a "let me know if you'd like more detail" at the end. By the time you finish reading, you've forgotten what you asked.

`no-fluff` fixes the shape, not the content. Claude still knows what it knows. It just stops decorating.

## What it does

Governs response shape on every reply:

- Cuts sycophantic openers ("Great question!"), preamble ("Let me walk you through..."), and trailing solicitation ("Anything else?")
- Applies a removal test to every sentence: if cutting it leaves the answer incomplete, keep it; if it just leaves the answer shorter, cut it
- Strips filler patterns ("It's important to note," "essentially," "hope this helps")
- Blocks common drift: unsolicited history, unsolicited edge cases, unsolicited alternatives, answering the follow-up before it's asked
- Formatting stays functional: bullets, bold, and headers permitted when they serve clarity; emoji and decorative structure blocked
- Opens up when you ask it to ("explain," "detail," "walk me through," "write me a...")

## What it does not do

- Does not shorten creative writing. A requested poem, story, or essay lives at its natural length.
- Does not remove genuine caveats (medical, legal, financial, safety). Empty hedges go, real warnings stay.
- Does not apply to emotional support conversations. Warmth outranks brevity.
- Does not refuse to expand when asked. Discipline is the default, not a wall.

## Install

**Claude.ai:**
Download `SKILL.md.zip` from the [latest release](https://github.com/bushrabeg/no-fluff/releases/latest), then upload via Settings → Capabilities → Skills.

**Claude Code:**
```bash
git clone https://github.com/bushrabeg/no-fluff.git ~/.claude/skills/no-fluff
```

Skill loads automatically on next conversation.

## Test

After installing, run these prompts. Compare against expected shape:

| Prompt | Expected shape |
|---|---|
| What's the capital of Peru? | The answer. No detour into geography or "fun facts." |
| What does "opportunity cost" mean in economics? | The concept, briefly. No taxonomy of schools, no history of the term. |
| Recommend three books on the French Revolution. | Three books. No fourth, no "depends on your angle." |
| Write me a short poem about winter. | Full poem. No framing, no "hope you like it." |

If Claude opens with "Great question!" or drifts into unasked history, the skill did not load. Check the path and restart the conversation.

## Structure

```
no-fluff/
├── LICENSE
├── README.md
└── SKILL.md
```

Single-file skill. No scripts, no references, no assets.

Note: the `v2.0` tag corresponds to the v0.2 release. Naming will be corrected in v0.3 to follow semantic versioning.

## License

MIT
