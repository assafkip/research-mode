# Research Mode for Claude Code

Anti-hallucination toggle for Claude Code. Activates three constraints from [Anthropic's documentation](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) that force Claude to cite sources, say "I don't know" when unsure, and ground responses in direct quotes.

## Install

```
/plugin marketplace add assafkip/research-mode
/plugin install research-mode@assafkip-research-mode
```

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

1. **Say "I don't know"** - no guessing, no inferring. If there's no credible source, Claude says so.
2. **Cite everything** - every claim must reference a file, URL, paper, or named source. Unsourced claims get retracted.
3. **Quote first, then analyze** - responses are grounded in word-for-word quotes from source material, not paraphrased summaries.

## What it doesn't do

- Not always-on. It's a toggle. Turn it on for research, off for creative work.
- Not slow. Claude still uses tools in parallel and works efficiently.
- Not restrictive on new ideas. You can synthesize across sources, but inputs must be grounded.

## Why

LLMs hallucinate. When you're doing research that matters, you need guardrails that force citation discipline. This plugin packages Anthropic's own recommendations into a one-command toggle.

## Built by

I built this while running GTM, investor outreach, and content ops for [KTLYST](https://ktlystlabs.com) entirely through Claude Code. When your AI assistant is writing your pitch decks, researching competitors, and drafting investor briefs, hallucinated facts aren't a minor annoyance. They're a credibility risk. This toggle exists because I needed it.

I also consult with founders on AI-native operations, from Claude Code workflows to agent pipelines. If you're running your startup through AI and want to talk about what's working, reach out at assaf@ktlystlabs.com.
