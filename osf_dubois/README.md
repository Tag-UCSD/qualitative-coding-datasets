# W.E.B. Du Bois in New York Times Dataset

## Overview
This dataset contains qualitative analysis of New York Times articles that mention W.E.B. Du Bois, spanning from 1918 to 1981. The study analyzes how Du Bois was portrayed and framed in mainstream American media over this time period.

## Qualitative Method

**Method:** Thematic Analysis
**Approach:** Inductive/Reflexive coding
**Coding Cycles:** Second cycle (thematic coding)
**Domain:** Historical/Media Studies
**Research Focus:** Media representation and framing of W.E.B. Du Bois

The analysis employed thematic coding to identify patterns in how the New York Times represented W.E.B. Du Bois across different article types and time periods. Coders identified 9 distinct themes that emerged from the data, focusing on Du Bois's portrayal as a scholar, activist, and historical figure.

### Coding Scheme

The dataset uses 9 qualitative codes:
1. **Scholar** (29 passages) - References to Du Bois as an academic/intellectual
2. **Activist** (28 passages) - References to Du Bois as a social/political activist
3. **Monumental Memorialization** (16 passages) - References to institutions, buildings, or programs named after Du Bois
4. **Mention of Scholarly Work** (26 passages) - Citations or discussions of Du Bois's writings
5. **Social/Political Advocacy** (57 passages) - References to Du Bois's positions on social/political issues
6. **Coalition Building** (10 passages) - References to Du Bois's work in building organizations or movements
7. **Out of the Mouth of Academics** (33 passages) - Du Bois quoted in academic contexts
8. **Out of the Mouth of Activists** (12 passages) - Du Bois quoted in activist contexts
9. **Collective Synecdoche** (27 passages) - Du Bois used as representative of broader movements/ideas

**Note:** Some passages received multiple codes (average: 1.02 codes per passage).

## Main CSV Files Structure

### osf_dubois_human_coded_LONG.csv
**Format:** One row per text-code pair (238 rows)
**Use case:** Best for analyzing which codes were applied to which passages

**Columns:**
- `passage_id` - Unique identifier for each passage (0-232)
- `date` - Publication date of the NYT article
- `article_type` - Type of NYT article (Archives, Opinion, Education, U.S., World, etc.)
- `title` - Full title of the NYT article
- `url` - Direct link to the original NYT article
- `passage_text` - The specific text excerpt that was coded
- `code` - The qualitative code applied to this passage

**Example row:**
```
passage_id: 0
date: 3/22/70
article_type: Archives
title: National Push for School Integration Losing Momentum
passage_text: "Black leaders such as Charles V. Hamilton...expressed by W. E. B. Du Bois in the 1930's."
code: Activist
```

### osf_dubois_human_coded_WIDE.csv
**Format:** One row per passage with binary code indicators (233 rows)
**Use case:** Best for statistical analysis or comparing code co-occurrence

**Structure:** Each of the 9 codes has its own column with binary values (1 = code applied, 0 = not applied)

## Original Data Files Structure

### original_data/osf_passages.csv
**Format:** Unlabeled passages extracted from NYT articles
**Rows:** 233 passages

**Columns:**
- First column: Passage ID number
- `date` - Publication date
- `article_type` - Type of article
- `title` - Article title
- `url` - Link to original article
- `passage` - Full text of the passage

This file contains the raw passages before any coding was applied.

### original_data/osf_gold_standard_coding.csv
**Format:** Detailed coding matrix
Contains the relationship between passages and codes, showing which codes were applied to each passage.

## Unlabeled Data Structure

### unlabeled_data/osf_passages_unlabeled.csv
This is a copy of the original passages file, provided for convenience when comparing LLM-driven coding to the original human coding.

**Same structure as original_data/osf_passages.csv**

## How to Use This Dataset for LLM Qualitative Coding Comparison

### Step 1: Set Up Your Coding Task
1. Use `unlabeled_data/osf_passages_unlabeled.csv` as input to your LLM
2. Provide the LLM with:
   - The passage text (from the `passage` column)
   - The 9 code definitions (see Coding Scheme above)
   - Instructions to apply relevant codes to each passage

### Step 2: Generate LLM Codings
Have your LLM produce output in the same format as `osf_dubois_human_coded_LONG.csv`:
- One row per passage-code pair
- Include: passage_id, passage_text, code

### Step 3: Compare Results

**Quantitative Comparison:**
- Calculate inter-rater agreement (Cohen's Kappa, Krippendorff's Alpha)
- Compare code frequencies (how often each code was applied)
- Analyze code co-occurrence patterns
- Calculate precision, recall, and F1 scores for each code

**Qualitative Comparison:**
- Examine passages where LLM and humans disagreed
- Identify patterns in LLM errors (over-coding, under-coding, specific code confusions)
- Review boundary cases where codes overlap
- Assess whether LLM captures nuanced distinctions (e.g., "Scholar" vs "Mention of Scholarly Work")

### Step 4: Key Evaluation Questions
1. **Code Distribution:** Does the LLM apply codes with similar frequency to humans?
2. **Multi-coding:** Does the LLM recognize when passages warrant multiple codes? (Humans applied 1.02 codes per passage on average)
3. **Contextual Understanding:** Can the LLM distinguish between similar codes based on context?
4. **Historical Context:** Does the LLM understand historical references and time periods (1918-1981)?

### Example Comparison Code (Python)
```python
import pandas as pd
from sklearn.metrics import cohen_kappa_score, classification_report

# Load human-coded data
human_wide = pd.read_csv('osf_dubois_human_coded_WIDE.csv')

# Load your LLM-coded data (convert to same wide format)
llm_wide = pd.read_csv('your_llm_coded_WIDE.csv')

# Calculate agreement for each code
for code in ['Scholar', 'Activist', 'Monumental Memorialization', ...]:
    kappa = cohen_kappa_score(human_wide[code], llm_wide[code])
    print(f"{code}: κ = {kappa:.3f}")
```

## Dataset Statistics

- **Total passages:** 233
- **Total text-to-code mappings:** 238
- **Time range:** 1918-1981
- **Article types:** 16 different types
- **Average codes per passage:** 1.02
- **Source:** OSF project k4fg9

## Citation & Source

**Source Repository:** OSF project k4fg9
**Domain:** Historical Media Studies
**Study Type:** Comparative analysis (human vs LLM coding available in original repository)

## Notes

- This dataset contains only the human-coded data
- The original OSF project also includes LLM-coded data (GPT-4) for comparison
- Some passages have no codes applied
- Binary coding approach (code either applies or doesn't, no intensity ratings)
- High-quality gold standard data suitable for benchmarking
