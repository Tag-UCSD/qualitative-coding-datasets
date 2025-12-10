# Do the Shuffle - Music Listening Study Dataset

## Overview
This dataset contains qualitative analysis of open-ended survey responses about music listening experiences. Participants were asked about randomly selected tracks from their personal music libraries and described their relationships with these songs.

## Qualitative Method

**Method:** Thematic Analysis
**Approach:** Inductive with hierarchical coding
**Coding Cycles:** Multiple cycles resulting in 3-level hierarchical structure
**Domain:** Music Psychology / Consumer Behavior
**Research Focus:** Understanding personal relationships with music
**Study Design:** "Shuffled Play" - participants discussed randomly selected tracks from their libraries

The analysis employed rigorous hierarchical thematic analysis with:
- **Inter-rater reliability testing** (reported in associated paper PMC7004375)
- **Multiple coders** with consensus process
- **Rich multi-dimensional coding** covering musical, emotional, social, and contextual aspects
- **Average 6.81 codes per response** indicating detailed, nuanced analysis

### Hierarchical Coding Structure

The dataset uses a **3-level hierarchical coding scheme** with 74 specific codes organized into higher-order categories:

**Level 1: 4 Higher-Order Themes**
1. **Associations** - Connections to people, places, times, events
2. **Characteristics** - Musical and sonic properties
3. **Evaluations** - Judgments and assessments
4. **Responses Induced** - Emotional and behavioral reactions

**Level 2: 14 Intermediate Categories**
- Examples: Musical Features, Contextual Associations, Affective Responses, etc.

**Level 3: 74 Specific Codes** (most granular level)

### Top 10 Most Applied Codes
1. **Positive** (505 responses) - Positive evaluations
2. **No relationship** (403 responses) - No connection to the song
3. **Artist** (344 responses) - References to the performing artist
4. **Musical Expressive Characteristics** (297 responses) - Expressive qualities of the music
5. **Album** (208 responses) - References to the album
6. **Musical Meaning** (180 responses) - Meaning conveyed by the music
7. **Time or Stage in Life** (163 responses) - Associations with life periods
8. **Lyrics** (146 responses) - References to song lyrics
9. **Beat** (134 responses) - Rhythmic elements
10. **Genre** (126 responses) - Musical genre references

## Main CSV Files Structure

### shuffle_music_coded_LONG.csv
**Format:** One row per text-code pair (5,417 rows)
**Use case:** Best for analyzing specific coded excerpts and understanding what text justified each code

**Columns:**
- `participant_id` - Participant number (1-397)
- `track_id` - Track identifier (unique within each participant)
- `full_response_text` - Complete open-ended response to questions about the track
- `code_level3` - The Level 3 qualitative code applied (one of 74 codes)
- `coded_text_excerpt` - The specific portion of text that was coded with this code

**Example row:**
```
participant_id: 1
track_id: a
full_response_text: "My teenage years. I downloaded the whole album as I like the band..."
code_level3: "Time or Stage in Life"
coded_text_excerpt: "My teenage years / It reminds me of the period in my life..."
```

**Note:** The same response can have multiple rows (one per code applied). Average: 6.81 codes per response.

### shuffle_music_coded_WIDE.csv
**Format:** One row per response with binary code indicators (796 rows)
**Use case:** Best for statistical analysis, calculating code frequencies, or examining code co-occurrence patterns

**Structure:** Each of the 74 Level 3 codes has its own column with binary values (1 = code applied, 0 = not applied)

**Additional context columns:**
- `participant_id`
- `track_id`
- `full_response_text`

## Original Data Files Structure

### original_data/All Data Reorg_5.11.19.xlsx
**Format:** Microsoft Excel workbook
**Content:** Complete dataset including:
- Raw survey responses
- Demographic information
- Track metadata
- Detailed coding sheets
- Hierarchical code structure documentation

This is the primary source file from the original research project.

### original_data/QUAL THEMES_ Reorg_22.02.19.xlsx
**Format:** Microsoft Excel workbook
**Content:** Thematic coding structure and definitions
- Code definitions and operational criteria
- Hierarchical relationships between codes
- Examples of coded text for each theme
- Coding decision documentation

## Unlabeled Data Structure

### unlabeled_data/shuffle_music_unlabeled.csv
**Format:** CSV with unique responses without codes
**Rows:** 784 unique participant-track combinations

**Columns:**
- `participant_id` - Participant number
- `track_id` - Track identifier
- `full_response_text` - Complete open-ended response (unlabeled)

**Use case:** Input data for LLM-driven qualitative coding attempts

## How to Use This Dataset for LLM Qualitative Coding Comparison

### Step 1: Prepare Code Definitions
Extract the 74 Level 3 code definitions from the original Excel files or from the human-coded data. You may want to:
- Start with all 74 codes, OR
- Focus on the top 10-20 most frequent codes, OR
- Select codes from a specific Level 1 theme (e.g., just "Associations" codes)

### Step 2: Set Up Your Coding Task
1. Use `unlabeled_data/shuffle_music_unlabeled.csv` as input
2. Provide the LLM with:
   - The full_response_text
   - Code definitions
   - Instructions to identify relevant text excerpts for each code
   - Guidance that multiple codes can apply to the same response

### Step 3: Generate LLM Codings
Have your LLM produce output matching `shuffle_music_coded_LONG.csv` format:
```csv
participant_id,track_id,full_response_text,code_level3,coded_text_excerpt
```

### Step 4: Compare Results

**Quantitative Metrics:**
- **Code frequency comparison:** Does LLM apply codes with similar distribution?
- **Codes per response:** Humans averaged 6.81; does LLM match this richness?
- **Inter-rater agreement:** Calculate Cohen's Kappa or Krippendorff's Alpha
- **Precision/Recall:** For each of the 74 codes
- **Code co-occurrence patterns:** Do certain codes appear together for LLM as they did for humans?

**Qualitative Analysis:**
- **Excerpt selection:** Does LLM identify the same text spans as humans?
- **Multi-dimensional coding:** Can LLM recognize that responses contain multiple themes?
- **Boundary cases:** How does LLM handle ambiguous responses?
- **Hierarchical relationships:** Does LLM understand parent-child code relationships?

### Step 5: Advanced Analyses

**Hierarchical Coding Assessment:**
- Can LLM learn the 3-level hierarchy and apply codes consistently?
- Compare LLM performance at Level 3 vs. if you aggregate to Level 2 or Level 1
- Do LLM errors respect the hierarchy (e.g., confusing sibling codes vs. unrelated codes)?

**Code Confusion Analysis:**
```python
import pandas as pd
from sklearn.metrics import confusion_matrix
import seaborn as sns

# Load data
human = pd.read_csv('shuffle_music_coded_WIDE.csv')
llm = pd.read_csv('your_llm_coded_WIDE.csv')

# Get code columns (exclude metadata columns)
code_cols = [col for col in human.columns if col not in
             ['participant_id', 'track_id', 'full_response_text']]

# For each code, compare
for code in code_cols[:10]:  # Top 10 codes
    cm = confusion_matrix(human[code], llm[code])
    print(f"\n{code}:")
    print(f"  Precision: {cm[1,1]/(cm[1,1]+cm[0,1]):.3f}")
    print(f"  Recall: {cm[1,1]/(cm[1,1]+cm[1,0]):.3f}")
```

### Step 6: Key Evaluation Questions

1. **Richness:** Does LLM capture the multi-dimensionality of responses?
   - Humans found an average of 6.81 distinct themes per response
   - Under-coding suggests missing nuance; over-coding suggests false positives

2. **Distribution:** Does LLM replicate the natural frequency distribution?
   - Some codes are rare (< 20 occurrences), others very common (> 400)
   - Check if LLM shows similar patterns

3. **Contextual Sensitivity:** Can LLM distinguish context-dependent meanings?
   - Example: "Positive" vs "Musical Meaning" vs "Emotion"
   - These can overlap but represent different analytical dimensions

4. **Excerpt Grounding:** Does LLM identify appropriate text evidence?
   - Compare coded_text_excerpt between human and LLM
   - Are excerpts similar in length and specificity?

5. **Domain Knowledge:** Does LLM understand music-specific terminology?
   - Codes like "Beat," "Vocals," "Genre," "Album" require music domain knowledge

## Dataset Statistics

- **Total responses:** 796 (some responses from 397 participants, 784 unique participant-track pairs)
- **Total text-to-code mappings:** 5,417
- **Average codes per response:** 6.81
- **Unique codes (Level 3):** 74
- **Hierarchical levels:** 3 (4 themes → 14 categories → 74 specific codes)
- **Study participants:** 397 people
- **Music tracks discussed:** 784 tracks

### Response Characteristics
- Responses range from brief ("No relationship") to detailed multi-sentence descriptions
- High variability in response length and complexity
- Mix of emotional, analytical, and descriptive content
- References to personal history, musical features, social contexts

## Citation & Source

**Source:** https://miguelmolina.me/dotheshuffle/
**Associated Paper:** PMC7004375
**Research Method:** "Shuffled Play" music listening study
**Domain:** Music Psychology, Consumer Behavior, Human-Computer Interaction

## Notes & Considerations

- **High-quality gold standard:** Multiple coders with inter-rater reliability testing
- **Rich coding depth:** Average 6.81 codes per response indicates thorough analysis
- **Hierarchical structure:** Offers multiple levels of granularity for evaluation
- **Ecological validity:** Real users discussing their actual music collections
- **Challenge for LLMs:** Requires understanding of:
  - Music terminology and concepts
  - Emotional and psychological language
  - Personal narrative interpretation
  - Multi-dimensional thematic thinking

## Coding Quality

**Rating:** ⭐⭐⭐⭐⭐ Exceptional

- Rigorous multi-coder process with consensus
- Inter-rater reliability reported in published paper
- 3-level hierarchical structure well-documented
- Very high coding density (6.81 codes per response)
- Clear operational definitions for all 74 codes
- Excellent for benchmarking LLM qualitative coding capabilities
