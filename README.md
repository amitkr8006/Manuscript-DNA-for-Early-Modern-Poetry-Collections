# STEMMA Hackathon: Manuscript DNA for Early Modern Poetry Collections

## Overview
This repository captures a hackathon prototype that explores whether early modern manuscript miscellanies have detectable “semantic fingerprints” (or “DNA”) that reflect collectors’ interests and curatorial tendencies. Using bibliographical metadata plus selected lines from a large corpus of early modern poetry transcriptions, we build collection-level profiles and compare manuscripts to surface similarity, thematic concentration, and anomalies.

## Hackathon Challenge
Given a dataset containing bibliographical metadata and selected lines from nearly 160,000 transcriptions of early modern poetry, identify an interesting pattern or anomaly that warrants further scholarly investigation.

## Research Questions
- How do collections reflect their collectors’ interests, preferences, and tendencies?
- How similar or different are manuscript collections in topical composition?
- Can we detect outliers (single-genre/single-purpose collections) or strong thematic clusters across miscellanies?

## Data Constraints (Important)
The dataset does not contain full poems. Semantic content is limited to:
- Title and/or heading (often redundant; sometimes cataloguer-generated)
- First line (present for most entries)
- Second and penultimate lines (less frequent)
- Last line (far fewer than first lines)
A subset of entries contains no text across these fields, and headings may include personal names or cataloguer description that can skew semantic comparisons.

## Approach (Hackathon Prototype Pipeline)
### 1) Idea Iteration
We explored multiple directions quickly (headings agency, sentiment analysis) and converged on embedding-based semantic similarity as the most defensible path under time and data constraints.

### 2) Snippet Construction
To reduce redundancy, we used title only when heading was missing. We also tested removing headings because headings/titles often contain personal names that distort semantic similarity.

### 3) Embedding-Based “Manuscript DNA”
- Created embedding vectors from concatenated text (title/heading + selected lines).
- Aggregated poem-level vectors into manuscript-level profiles (“DNA”).
- Compared manuscript profiles using cosine similarity and cluster inspection.
- Used 2D projections for communication while acknowledging they compress high-dimensional structure.

### 4) Sampling Strategy
We identified high-volume manuscripts, removed near single-author collections, and focused on a curated set of key miscellanies plus a known special case manuscript for comparison.

## Key Findings (Patterns / Anomalies)
- **Outlier detection:** Yale Osborn MS fb 217 emerged as a strong semantic outlier, consistent with its single-genre composition (epigrams). This supports the idea that genre concentration produces measurable fingerprints.
- **Devotional cluster signal:** We observed a cluster dominated by Psalms, indicating the approach can detect homogeneous sub-genres within broader miscellanies.
- **Metadata noise matters:** Headings and personal names can dominate similarity signals; results improved after removing headings and applying basic preprocessing (stopwords/lemmatization).

## Limitations Observed
- 2D projections are visually useful but reductive compared to true high-dimensional similarity.
- LLM-based theme generation struggled with metaphor and early modern language; controlled thematic lexicons were more reliable.
- Missingness is uneven across line positions; which lines are present can influence results.

## Future Work
- Separate “names” from “content” (NER + stopwording) to reduce distortion while preserving scholarly signals.
- Expand beyond a single theme (religion) to multiple controlled thematic signatures to generate richer manuscript DNA cards.
- Validate fingerprints against known bibliographic/codicological metadata for interpretability and scholarly use.
