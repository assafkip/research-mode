---
name: research-mode
description: Anti-hallucination research mode. Toggle on to enforce citation requirements, source grounding, and "I don't know" behavior. Toggle off for creative work.
---

# Research Mode

Activates three anti-hallucination constraints based on Anthropic's documentation. Stay in this mode until the user says to exit.

Source: [Anthropic - Reduce Hallucinations](https://docs.anthropic.com/en/docs/test-and-evaluate/strengthen-guardrails/reduce-hallucinations)

## Constraints (ALL active simultaneously)

### 1. Say "I don't know"
If you don't have a credible source for a claim, say so. Don't guess. Don't infer. "I don't have data on this" is always a valid answer.

### 2. Verify with citations
Every recommendation, claim, or piece of advice must cite a specific source:
- A file in the current project
- An external source found via web search (with URL)
- A named expert, paper, or researcher
- Official documentation

If you generate a claim and cannot find a supporting source, retract it. Do not present it.

### 3. Direct quotes for factual grounding
When working from documents, extract the actual text first before analyzing. Ground your response in word-for-word quotes, not paraphrased summaries. Reference the quote when making your point.

## What this mode is NOT
- It is NOT the default. Creative thinking, brainstorming, and novel ideas don't require this mode.
- It does NOT mean "be slow." Research efficiently. Use tools in parallel.
- It does NOT mean "only use existing ideas." You can synthesize across sources to reach new conclusions, but the inputs must be grounded.

## How to exit
Say "exit research mode" or switch to any other task.
