# LLM Context Engineering Framework

## Overview

Large context windows (up to 1 million tokens) create the illusion that you can dump everything into a prompt and let the model sort it out. Research shows this backfires: GPT-4.1's accuracy dropped 10.9 percentage points between 128,000 and 1 million tokens, and models struggle when relevant information sits in the middle of long contexts.

This framework helps you decide what to include, how to structure it, and when more context actually makes things worse.

## Core Principle

A context window is a budget, not a bucket. Every token you add competes for the model's attention. Your job is curation, not collection.

## Three-Stage Process

### Stage 1: Score Each Candidate Document

Use the scoring criteria in `SCORING.md` to evaluate:
- Relevance to the query (0-10)
- Specificity vs. generality (0-10)
- Noise level (0-10, where 10 = no noise)

Total possible: 30 points per document.

### Stage 2: Apply Decision Thresholds

Use `DECISION_MATRIX.md` to categorize each document:
- **Include**: Score ≥ 24, goes into context as-is
- **Summarize**: Score 18-23, extract key facts or compress
- **Exclude**: Score < 18, omit entirely

These thresholds are starting points. Calibrate based on your task and model.

### Stage 3: Structure the Context

Order matters. Models perform worse when relevant information appears in the middle of long contexts. Use this ordering:

1. **Query/Instruction** (top)
2. **Most relevant documents** (immediately after query)
3. **Supporting context** (middle, if necessary)
4. **Constraints or examples** (near the end)
5. **Repeat critical information** (end, if context > 50k tokens)

## Measuring Success

Track these for each query:
- Final context length (tokens)
- Number of documents included vs. excluded
- Accuracy or task success (if measurable)
- Latency (if time-sensitive)

Record in `scoring_sheet.csv`. After 20-30 queries, adjust thresholds if you see patterns (e.g., scores of 22 consistently perform well).

## When to Stop Adding Context

Stop if:
- You exceed 200,000 tokens (latency increases sharply)
- Adding more documents drops the relevance score of the set below 8/10
- The model's output quality plateaus or declines
- Cost per query becomes prohibitive

## Real-World Calibration

Models degrade with excess context. In one study, performance dropped 13.9% to 85% as input length increased, even when the needed information was retrievable. Another found that 15 irrelevant documents caused GPT-4.1's accuracy to fall from 26% to 2% on multi-step reasoning.

Your goal is not to fill the window. It is to give the model exactly what it needs and nothing else.
