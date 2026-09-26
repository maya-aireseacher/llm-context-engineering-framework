# LLM Context Engineering Framework

A practical scoring system for deciding what goes into your LLM prompt and how to structure it. If you have a million-token context window, this framework helps you figure out whether you should actually use it.

## Who this is for

Developers building LLM applications who need to decide which documents to include in a prompt, how to order them, and when to stop adding more context.

## How to use it

1. For each candidate document or chunk, score it using `SCORING.md` (relevance, specificity, noise level).
2. Rank documents by total score.
3. Use `DECISION_MATRIX.md` to decide whether to include, summarize, or exclude each one.
4. Structure the final context using the ordering guidance in `FRAMEWORK.md`.
5. Track outcomes in `scoring_sheet.csv` to refine your thresholds over time.

The framework assumes you already have a set of candidate documents. It does not replace retrieval; it sits after retrieval and before prompt assembly.

## Limitations

- Does not account for real-time latency constraints or cost per token.
- Scoring is qualitative; you will need to calibrate thresholds for your domain.
- Designed for question-answering and analysis tasks, not creative generation.
- Does not address structured data or code context specifically.

## Contributing

This is a starting point. Open an issue or PR if you have calibration data, additional scoring dimensions, or domain-specific adaptations.

## Further reading

- [Bigger Context Is Not Always Better: Why Long-Context LLMs Need Context Engineering](https://www.techaimag.com/machine-learning/bigger-context-is-not-always-better-why-long-context-llms-need-context-engineering)
- [GPT-4.1 (openai.com)](https://openai.com/index/gpt-4-1/)
- [How Is LLM Reasoning Distracted by Irrelevant Context? An Analysis Using a Controlled Benchmark (aclanthology.org)](https://aclanthology.org/2025.emnlp-main.674/)
- [Heisenberg Research Labs](https://heisenberginstitute.com/research/)