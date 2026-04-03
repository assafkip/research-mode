# Research Mode for Claude Code

Anti-hallucination toggle for Claude Code. Activates citation constraints from [Anthropic's documentation](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) that force Claude to cite sources, say "I don't know" when unsure, and ground responses in direct quotes.

> **Using [Kipi Founder OS](https://github.com/assafkip/kipi-system)?** Research mode is already built into kipi-core. Just run `/q-research <topic>`. No extra install needed.

## Install

Works in Claude Code CLI, the macOS desktop app, and the VS Code extension. Open Claude Code and run these two commands:

**Step 1 -- Add the marketplace:**
```
/plugin marketplace add assafkip/research-mode
```

**Step 2 -- Install the plugin:**
```
/plugin install research-mode@assafkip-research-mode
```

That's it. To confirm it installed, run `/plugin` and check that `research-mode` appears in your list.

**Alternative -- install as a standalone skill:**
If you prefer not to use the plugin system, clone this repo and copy the `SKILL.md` file into your project's `.claude/skills/research-mode/` directory.

## Use

```
/research-mode:research
```

Or with a topic:

```
/research-mode:research what caused the Change Healthcare breach
```

Say "exit research mode" to turn it off.

## What it does

Three constraints activate simultaneously:

1. **Say "I don't know"** -- no guessing, no inferring. If there's no credible source, Claude says so.
2. **Cite everything** -- every claim must reference a file, URL, paper, or named source. Unsourced claims get retracted.
3. **Quote first, then analyze** -- responses are grounded in word-for-word quotes from source material, not paraphrased summaries.

## Source cascade (keeps token costs low)

Sources are checked in order. Claude stops at the first level that answers the question:

1. **Local files** (Grep + Read) -- zero cost, most reliable
2. **WebSearch snippets** -- cite the snippet directly, skip downloading full pages
3. **WebFetch** -- only when the snippet is ambiguous or user needs full quotes
4. **Scholar Gateway** -- for academic papers, if available

Token budget: 5 WebSearch, 3 WebFetch max per question. If the limit is hit, Claude summarizes what it found and asks before going deeper.

## What it doesn't do

- Not always-on. It's a toggle. Turn it on for research, off for creative work.
- Not slow. Claude still uses tools in parallel and works efficiently.
- Not restrictive on new ideas. You can synthesize across sources, but inputs must be grounded.

## Why

LLMs hallucinate. When you're doing research that matters, you need guardrails that force citation discipline. This plugin packages Anthropic's own recommendations into a one-command toggle.

## Troubleshooting

**"Plugin not found" after Step 1:** Make sure you typed the marketplace command exactly as shown. The marketplace name is `assafkip/research-mode` (GitHub username/repo).

**Command doesn't appear after install:** Run `/reload-plugins` to refresh, or restart Claude Code.

**Want to scope it to one project only:** Add `--scope project` to the install command in Step 2.

## Built by

[Assaf Kipnis](https://github.com/assafkip) -- built while running GTM, investor outreach, and content ops for [KTLYST](https://ktlystlabs.com) entirely through Claude Code. When your AI assistant is writing your pitch decks, researching competitors, and drafting investor briefs, hallucinated facts aren't a minor annoyance. They're a credibility risk. This toggle exists because I needed it.

Questions or feedback: assaf@ktlystlabs.com
