# How Scrum Adds Value to Achieving Software Quality Dataset

## Overview
This dataset contains qualitative analysis of 39 semi-structured interviews with Scrum practitioners exploring how the Scrum methodology contributes to achieving software quality. This is an exceptionally well-documented dataset with both first and second cycle coding.

## Qualitative Method

**Method:** Inductive Thematic Analysis
**Approach:** Two-cycle coding process (First Cycle → Second Cycle Pattern Coding)
**Coding Cycles:** Both first and second cycle codes available
**Domain:** Organizational Studies, Software Engineering
**Participants:** 39 Scrum practitioners
**Research Questions:**
- **RQ1:** How do Scrum practitioners define software quality?
- **RQ2:** How does Scrum contribute to achieving software quality?

### Methodological Rigor

This dataset is **exceptionally well-documented** with:
- **Detailed codebook** with operational definitions
- **Clear hierarchical structure** mapping first cycle codes to second cycle themes
- **Multiple coding types** employed (In Vivo, Descriptive, Process, Causation, Value)
- **Extensive documentation** of coding rationale and decision-making
- **Transparent research process** including interview guides and analysis files

### First Cycle Coding

First cycle coding involved detailed line-by-line analysis using multiple coding strategies:

**Coding Types Used:**
1. **In Vivo Coding** - Using participants' own words as codes
2. **Descriptive Coding** - Summarizing topics in short phrases
3. **Process Coding** - Capturing actions using gerunds (-ing words)
4. **Causation Coding** - Identifying cause-effect relationships
5. **Value Coding** - Capturing beliefs, attitudes, and values

**Result:** 89 unique first cycle codes applied to 326 text chunks

**Examples of First Cycle Codes:**
- "Quality is a subjective concept" (In Vivo)
- "Continuous improvements" (In Vivo)
- "Quality assurance" (Descriptive)
- "Internal quality" (In Vivo)
- "Conformity to business needs" (In Vivo)

### Second Cycle Coding

Second cycle coding identified higher-level patterns and themes across first cycle codes:

**Result:** 15 second cycle pattern codes

**Pattern Codes (Second Cycle Themes):**
- External quality
- Internal quality
- Process quality
- Continuous improvement
- Team collaboration
- Transparency
- Self-organization
- And others...

These patterns represent the major themes answering the research questions about how Scrum practitioners conceptualize and achieve software quality.

## Main CSV Files Structure

### scrum_quality_coded_data.csv
**Format:** One row per coded text chunk (595 rows)
**Use case:** Complete dataset showing both first and second cycle codes

**Columns (updated):**
- `research_question` - Which RQ this excerpt addresses (RQ1 or RQ2)
- `document ID` - Participant identifier (Participant 1-39)
- `text_chunk` - The interview excerpt that was coded
- `code_1` - First-cycle code applied by the authors
- `code_1_type` - Coding type used by the authors (In Vivo, Descriptive, Process, Causation, Value, etc.)
- `code_2` - Second-cycle pattern code
- `code_2_type` - Pattern code indicator
- `theme` - Mirrors the pattern code for convenience

**Note on second-cycle mapping:** The “Pattern Codes” tabs in the RQ1/RQ2 second-cycle Excel files only enumerate a subset of the first-cycle codes. To ensure every row carries a pattern code, missing mappings were filled using deterministic heuristics:
- RQ1: external- vs. internal-quality keywords were used when a first-cycle code was not explicitly listed under a pattern.
- RQ2: keyword buckets (testing, transparency, accountability/ownership, collaboration/knowledge sharing, feedback, iteration/modularity, inspection/adaptation, caring about quality) were applied when an exact or near-exact match to the pattern sheet was absent.

If tighter alignment guidance becomes available, remap `code_2`/`theme` directly from the provided second-cycle sheets and overwrite the heuristic assignments.

## Original Data Files Structure

### original_data/6624064/ (Zenodo Dataset)

This folder contains the complete research data package:

**Analysis Files:**
- `Data Analysis - First Cycle - RQ1 - Final.xlsx` - Complete first cycle coding for RQ1
- `Data Analysis - First Cycle - RQ2 - Final.xlsx` - Complete first cycle coding for RQ2
- `Data Analysis - Second Cycle - RQ1 - Final.xlsx` - Pattern coding for RQ1
- `Data Analysis - Second Cycle - RQ2 - Final.xlsx` - Pattern coding for RQ2

**Interview Transcripts:**
- `Participant 1 - Interview_A.pdf` through `Participant 39 - Interview_A.pdf`
- Individual interview transcripts for all 39 participants
- `Focus Group 1 - Interview A.pdf` - Focus group transcript
- `Focus Group 2 - Interview A.pdf` - Focus group transcript
- `Focus Group Slides.pdf` - Materials used in focus groups

**Structure:**
The Excel analysis files contain:
- Full interview excerpts
- First cycle codes with code type annotations
- Second cycle pattern codes
- Hierarchical mapping between codes and themes
- Detailed coding memos and rationale

### original_data/s10664-022-10208-4.pdf

The published research paper providing:
- Complete methodology description
- Research questions and theoretical framework
- Findings and discussion
- Codebook with operational definitions
- Examples of coded data

## Unlabeled Data Structure

### unlabeled_data/scrum_quality_unlabeled.csv
**Format:** Text chunks without codes
**Rows:** 248 unique text chunks

**Columns:**
- `research_question` - RQ1 or RQ2
- `participant` - Participant identifier
- `text_chunk` - Interview excerpt (unlabeled)

**Use case:** Input for LLM-driven qualitative coding

## How to Use This Dataset for LLM Qualitative Coding Comparison

### Step 1: Choose Your Coding Approach

This dataset offers multiple levels of complexity for evaluation:

**Option A: First Cycle Coding Only**
- Task: Apply the 89 first cycle codes to text chunks
- Challenge: Requires understanding different coding types
- Benefit: Tests LLM's ability to do detailed line-by-line coding

**Option B: Second Cycle Pattern Coding Only**
- Task: Apply the 15 pattern codes to text chunks
- Challenge: Requires higher-level thematic thinking
- Benefit: Tests LLM's ability to identify broader themes

**Option C: Both Cycles**
- Task: Generate both first and second cycle codes
- Challenge: Most complex, requires hierarchical thinking
- Benefit: Full evaluation of multi-cycle qualitative analysis

**Option D: Coding Type Classification**
- Task: Given a code, classify it as In Vivo, Descriptive, Process, Causation, or Value
- Challenge: Requires understanding coding methodology
- Benefit: Tests LLM's meta-knowledge of qualitative methods

### Step 2: Prepare Code Definitions

Extract code definitions from:
1. The published paper (s10664-022-10208-4.pdf)
2. The Excel analysis files in original_data/6624064/
3. The main CSV file (examine examples of each code)

Provide the LLM with:
- Code labels
- Operational definitions
- Example coded excerpts
- Guidance on coding types (if doing Option A or D)

### Step 3: Set Up Your LLM Coding Task

Use `unlabeled_data/scrum_quality_unlabeled.csv` as input.

**Prompt structure for First Cycle Coding:**
```
You are a qualitative researcher coding interview data about Scrum and software quality.

Research Questions:
- RQ1: How do Scrum practitioners define software quality?
- RQ2: How does Scrum contribute to achieving software quality?

Coding Types to Use:
- In Vivo: Use participants' exact words
- Descriptive: Summarize topics
- Process: Capture actions (-ing words)
- Causation: Identify cause-effect
- Value: Capture beliefs/values

For each text chunk, provide:
1. The most appropriate code
2. The coding type used
3. Brief justification

Text chunk: [insert from unlabeled data]
```

### Step 4: Compare Results

**Quantitative Comparison:**

```python
import pandas as pd
from sklearn.metrics import cohen_kappa_score, classification_report

# Load data
human = pd.read_csv('scrum_quality_coded_data.csv')
llm = pd.read_csv('your_llm_coded_data.csv')

# Remove header rows
human = human[human['text_chunk'] != 'Data chunk']
llm = llm[llm['text_chunk'] != 'Data chunk']

# Merge on text_chunk
merged = human.merge(llm, on='text_chunk', suffixes=('_human', '_llm'))

# Compare first cycle codes
print("First Cycle Code Agreement:")
exact_match = (merged['first_cycle_code_human'] == merged['first_cycle_code_llm']).mean()
print(f"Exact match rate: {exact_match:.2%}")

# Compare coding types
print("\nCoding Type Agreement:")
type_kappa = cohen_kappa_score(merged['code_type_human'], merged['code_type_llm'])
print(f"Cohen's Kappa: {type_kappa:.3f}")
```

**Qualitative Comparison:**

1. **Code Appropriateness:** Do LLM codes capture the same meaning as human codes, even if worded differently?
2. **Coding Type Selection:** Does LLM choose appropriate coding types (In Vivo vs. Descriptive, etc.)?
3. **Granularity:** Are LLM codes at the right level of abstraction?
4. **Domain Understanding:** Does LLM understand Scrum and software engineering terminology?

### Step 5: Advanced Analyses

**Hierarchical Coding Evaluation:**
If testing both cycles, evaluate:
- Can LLM generate appropriate first cycle codes?
- Can LLM then group those codes into second cycle patterns?
- Do LLM's hierarchical relationships make logical sense?

**Coding Type Classification:**
```python
# Evaluate if LLM correctly identifies coding types
from sklearn.metrics import classification_report

print(classification_report(
    merged['code_type_human'],
    merged['code_type_llm'],
    labels=['In Vivo', 'Descriptive Coding', 'Process', 'Causation', 'Value']
))
```

**Research Question Alignment:**
- Do codes for RQ1 focus on definitions of quality?
- Do codes for RQ2 focus on how Scrum achieves quality?
- Can LLM distinguish which RQ a text chunk addresses?

### Step 6: Key Evaluation Questions

1. **In Vivo Coding Accuracy:**
   - Does LLM extract actual participant language for In Vivo codes?
   - Are the exact phrases preserved?

2. **Coding Type Understanding:**
   - Can LLM distinguish when to use In Vivo vs. Descriptive?
   - Does LLM correctly identify Process codes (gerunds)?
   - Can LLM recognize Causation and Value coding opportunities?

3. **Thematic Consistency:**
   - For second cycle: Does LLM group similar first cycle codes together?
   - Are pattern codes meaningful and well-defined?

4. **Domain Knowledge:**
   - Does LLM understand Scrum terminology (retrospectives, sprints, etc.)?
   - Does LLM grasp software quality concepts (internal vs. external quality)?

5. **Methodological Rigor:**
   - Can LLM explain its coding decisions?
   - Does LLM maintain consistency across similar text chunks?

## Dataset Statistics

- **Participants:** 39 Scrum practitioners
- **Coded text chunks:** 326
- **Unique first cycle codes:** 89
- **Second cycle pattern codes:** 15
- **Research questions:** 2 (RQ1 and RQ2)
- **Coding types used:** 5 (In Vivo, Descriptive, Process, Causation, Value)
- **Interview transcripts:** 39 individual + 2 focus groups

## Citation & Source

**DOI:** https://doi.org/10.5281/zenodo.6624064
**Paper:** "How Scrum Adds Value to Achieving Software Quality"
**Published:** Empirical Software Engineering (2022)
**PMID:** 36159897
**Full Citation:** https://pubmed.ncbi.nlm.nih.gov/36159897/

## Notes & Considerations

### Strengths
- **Exceptional documentation:** Extremely detailed codebook with operational definitions
- **Transparency:** Complete analysis files showing coding decisions
- **Multiple coding types:** Tests diverse qualitative coding skills
- **Hierarchical structure:** Both first and second cycle coding available
- **Rich context:** Full interview transcripts provided
- **Methodological guidance:** Paper explains coding justifications and style choices

### Challenges for LLMs
- **Multiple coding types:** Requires understanding when to use each type
- **In Vivo precision:** Must extract exact participant language
- **Domain expertise:** Requires knowledge of Scrum and software engineering
- **Hierarchical thinking:** For second cycle, must abstract from specific to general
- **Research question alignment:** Must understand which excerpts address which RQ

### Best Use Cases
- **Benchmarking multi-cycle coding:** Tests both detailed and thematic coding
- **Coding type classification:** Unique opportunity to evaluate methodological understanding
- **Domain-specific coding:** Tests LLM performance in technical domain
- **Methodological training:** Excellent for teaching qualitative coding principles

## Coding Quality

**Rating:** ⭐⭐⭐⭐⭐ Exceptional

> "Extremely detailed, offers insights on operational definitions, research questions, coding styles, & justifications for coding one way or another. May be useful for alignment on the levels of justification & style"
> — Dataset Review

This is one of the highest-quality qualitative coding datasets available, with:
- Complete transparency in coding decisions
- Both first and second cycle analysis
- Multiple coding type demonstrations
- Extensive documentation and rationale
- Published methodology with peer review
