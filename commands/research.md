# Research Mode

Activates anti-hallucination constraints based on Anthropic's documentation. Stay in this mode until the user says to exit.

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

## Source lookup order (ENFORCED -- follow this cascade)

Check sources in this order. Stop at the first level that answers the question.

**Level 1 -- Local files (zero cost):** Use Grep and Read to search the current project first. If the claim is about this project, local files ARE the citation.

**Level 2 -- WebSearch snippets only (low cost):** Run WebSearch. The result snippets usually contain the key fact. Cite as: "According to [Source Name] ([URL]): [snippet text]". DO NOT call WebFetch unless the snippet is ambiguous or incomplete.

**Level 3 -- WebFetch for direct quotes (high cost, use sparingly):** Only fetch full pages when the snippet is ambiguous, the user explicitly asked for full text, or you need a specific number/date/detail the snippet doesn't include.

**Level 4 -- Scholar Gateway (for academic claims):** For academic papers or research findings, use Scholar Gateway MCP if available.

### Token budget
- Maximum 5 WebSearch calls per research question
- Maximum 3 WebFetch calls per research question
- If you hit the limit: summarize what you found, list what remains unverified, and ask if you should go deeper
- Parallel searches are fine. Serial retry loops are not.

## What this mode is NOT
- It is NOT the default. Creative work doesn't require this mode.
- It does NOT mean "be slow." Research efficiently. Use tools in parallel.
- It does NOT mean "only use existing ideas." Synthesize across sources, but inputs must be grounded.

## How to exit
Say "exit research mode" or switch to any other task.

## Arguments
$ARGUMENTS - optional topic to research. If provided, begin researching immediately.
