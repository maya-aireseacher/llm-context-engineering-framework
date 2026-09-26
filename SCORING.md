# Scoring Criteria

Score each candidate document on three dimensions. Each dimension is 0-10 points.

## 1. Relevance to Query (0-10)

**10 points**: Directly answers the query or provides the exact information needed.
- Example: Query asks for Q3 revenue; document contains Q3 revenue figure.

**7-9 points**: Strongly related but requires inference or combination with other documents.
- Example: Query asks for year-over-year growth; document has Q3 revenue for two years but not the calculation.

**4-6 points**: Tangentially related; provides context but not the answer.
- Example: Query asks about a product feature; document discusses the product's history.

**1-3 points**: Mentions a keyword from the query but does not address the question.
- Example: Query asks about pricing; document mentions the product name but not pricing.

**0 points**: Unrelated.

## 2. Specificity (0-10)

**10 points**: Contains specific, falsifiable facts (numbers, dates, names, measurements).
- Example: "Revenue was $42.3M in Q3 2024."

**7-9 points**: Contains concrete statements but some generality.
- Example: "Revenue increased significantly in Q3."

**4-6 points**: Mix of specific and generic statements.
- Example: "The company performed well, driven by strong product demand."

**1-3 points**: Mostly generic or abstract.
- Example: "We remain committed to growth and innovation."

**0 points**: Entirely boilerplate or vague.

## 3. Noise Level (0-10)

**10 points**: No irrelevant content; every sentence supports the query.

**7-9 points**: Mostly relevant; a few sentences can be ignored.

**4-6 points**: Half the content is off-topic or redundant.

**1-3 points**: Relevant information buried in long, unrelated sections.

**0 points**: Relevant information constitutes less than 10% of the document.

## Total Score

Sum the three dimensions. Maximum: 30 points.

A document scoring 24+ is a strong candidate for inclusion. A document scoring below 18 likely adds more noise than signal.
