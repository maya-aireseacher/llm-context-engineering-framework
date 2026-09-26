# Decision Matrix

After scoring each candidate document, use this matrix to decide how to handle it.

| Total Score | Decision | Action |
|-------------|----------|--------|
| 24-30 | **Include** | Add to context as-is. Place near the top if score ≥ 27. |
| 18-23 | **Summarize** | Extract key facts (1-3 sentences) or use the first and last paragraphs only. Include the summary, not the full text. |
| 0-17 | **Exclude** | Omit entirely. It will distract the model more than it helps. |

## Special Cases

### Redundant Documents (Score ≥ 24)

If two documents score above 24 and cover the same information:
- Include the one with the higher **Specificity** score.
- If tied, include the shorter one.

### Conflicting Information

If two documents score above 24 but contradict each other:
- Include both.
- Add a note in the prompt: "Documents 2 and 5 contain conflicting figures. Use the most recent one."

### Long Documents (> 10,000 tokens)

If a document scores above 24 but is very long:
- Check if you can extract the relevant section (e.g., one chapter, one section).
- If the entire document is needed, consider whether summarizing it would still preserve the key information.

## Adjusting Thresholds

These are starting points. After 20-30 queries, review `scoring_sheet.csv`:
- If documents scoring 22-23 consistently lead to good outcomes, lower the "Include" threshold to 22.
- If documents scoring 18-20 add little value, raise the "Summarize" threshold to 21.

## Example

**Query**: What was the company's Q3 2024 revenue and how does it compare to Q3 2023?

**Candidate Documents**:
1. Q3 2024 earnings report (Relevance: 10, Specificity: 10, Noise: 9) → **Total: 29** → Include
2. Q3 2023 earnings report (Relevance: 9, Specificity: 10, Noise: 9) → **Total: 28** → Include
3. CEO's blog post mentioning growth (Relevance: 5, Specificity: 4, Noise: 6) → **Total: 15** → Exclude
4. Analyst report covering both quarters (Relevance: 9, Specificity: 8, Noise: 7) → **Total: 24** → Include
5. Company history page (Relevance: 2, Specificity: 3, Noise: 5) → **Total: 10** → Exclude

**Final context**: Documents 1, 2, 4, ordered by score.
