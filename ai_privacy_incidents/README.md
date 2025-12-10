# AI Privacy and Ethical Incidents Dataset

## Overview
This dataset contains qualitative analysis of AI-related privacy and ethical incidents reported in media and research. Each incident is coded across multiple dimensions including causes, consequences, responsible entities, and incident types, creating a comprehensive taxonomy of AI harms.

## Qualitative Method

**Method:** Content Analysis / Categorical Coding
**Approach:** Multi-dimensional taxonomic coding
**Domain:** AI Ethics, Privacy, Technology Policy
**Data Source:** Media reports, regulatory investigations, research studies
**Research Focus:** Mapping causes, entities, and consequences of AI privacy and ethical incidents

### Coding Framework

This dataset employs **multi-dimensional categorical coding** across 5 major dimensions:

1. **Causes (Tag_Cause)** - Why did the incident occur?
2. **Consequences (Tag_Consequence)** - What were the impacts?
3. **Entities (Tag_Entity)** - Who/what was responsible?
4. **Incidents (Tag_Incident)** - What type of incident occurred?
5. **Sources (Tag_Source)** - Where did information come from?
6. **Other (Tag_Other)** - Additional contextual factors

Each incident can have **multiple tags** across all dimensions, creating a rich multidimensional profile.

###Dimension 1: Causes

**Tag_Cause categories:**
- AI misinterpretation & hallucinations & faulty functions & inefficiency
- Potential AI bias (racism - inequality)
- Manipulating people's minds
- Human abuse of AI tools
- Lack of trust on AI
- Employee internal threats
- Lack of AI policy
- Programmed AI with problematic functions
- Legal loophole
- Over-trusting AI
- No specific info
- Lack of AI fail-safe measures
- Lack of data protection
- Legal non-compliance
- Poor business ethics
- Lack of informed consent & transparency
- Vague policy information

### Dimension 2: Consequences

**Tag_Consequence categories:**
- Criticism by lawmakers and independent groups/organizations/advocates
- Legal action & penalty
- Legal authorities suggested investigation
- Banning/abandonment of AI tools
- Developer actions
- Loss of faith in AI tools
- No specific info
- Possible emotional, opinions manipulation
- Possible hyperpersonalized & targeted manipulation
- Potential cyber attack
- Potential more accessible cyberbullying
- Public user backlash & concern about AI
- Public/group harms & false beliefs
- Single user harm
- Third-party mitigation strategies

### Dimension 3: Entities

**Tag_Entity categories:**
- AI algorithm
- AI developer & affiliated partners
- Government authorities that adopt AI
- Large dataset organization
- Malicious human
- No specific info
- AI-adopting organizations
- User misinterpretation

### Dimension 4: Incidents

**Tag_Incident categories:**
- AI data breach
- False & unexpected & disappointing behavior
- Public entity amplify misleading content
- Bypassing AI safeguards
- De-anonymize & stalking & harassment
- Nonconsensual imagery, impersonation, fake content
- Problematic AI implementation
- Problematic database used for AI training
- Secondary data use for AI functions
- Secondary data use for AI model training
- Unauthorized sale of user data
- Unclear user agreements and policy statements
- Use of unlawful/problematic AI tools

### Dimension 5: Sources

**Tag_Source categories:**
- AI adopting entities
- AI developer company
- Large database organizations
- Law enforcement & legal authorities
- Media
- No specific info
- Organization/government whistleblower
- Researchers & research institutions & fact checkers
- Users & people
- White hat hacker

### Dimension 6: Other Contextual Tags

**Tag_Other categories:**
- AI developer refusal of disclosing how AI works
- AI exacerbates power imbalance
- AI innovation, functionality vs. privacy & ethical dilemma
- AI introduces military & judicial & political risk
- Copyright infringement
- Espionage
- Inadequate security measures
- Inappropriate content for minors and children /vulnerable
- Potential workforce disruption
- Shift in educational focus
- Tech addiction (influencing things like well-being)
- Unjustified data collection (more than needed)
- Blurred line between satire and misinfo
- Call for responsible AI use
- Call for robust legislation for AI
- Deceptive design & predatory marketing
- Developer false claim
- Geographical exclusion & protections
- Indirect data stealing from users
- Legal inability or inaction
- Persistent false info
- Regulatory reduction in organization's liability
- Unintentional side effects
- Use of children data

## Main CSV Files Structure

### ai_privacy_incidents_coded_data.csv
**Format:** One row per incident (196 rows)
**Use case:** Complete dataset with incident descriptions and all tags

**Columns:**
- `Note - AIAAIC ID` - Unique incident identifier
- `Headline` - Brief title of the incident
- `Type` - Incident or Issue
- `Released` - Publication date
- `Occurred` - When incident occurred
- `Country(ies)` - Geographic location(s)
- `Sector(s)` - Industry sector(s)
- `Deployer(s)` - Organizations deploying the AI
- `Developer(s)` - AI system developers
- `System name(s)` - Names of AI systems involved
- `Technology(ies)` - AI technologies used
- `Purpose(s)` - Intended purpose of AI system
- `Media trigger(s)` - What triggered public attention
- `Issue(s)` - Key issues involved
- `Transparency` - Transparency-related factors
- `Description/links` - Full incident description and URL
- **Tag_Cause - [category]** - Binary columns (1/0) for each cause tag
- **Tag_Consequence - [category]** - Binary columns for consequences
- **Tag_Entity - [category]** - Binary columns for responsible entities
- **Tag_Incident - [category]** - Binary columns for incident types
- **Tag_Source - [category]** - Binary columns for information sources
- **Tag_Other - [category]** - Binary columns for other contextual factors

**Example structure:**
Each incident has dozens of binary tag columns. A value of 1 indicates the tag applies; 0 means it doesn't.

**Multi-Tag Example:**
An incident about LAION-5B containing photos of Brazilian children might be tagged:
- Tag_Cause - lack of informed consent & transparency: 1
- Tag_Entity - large dataset organization: 1
- Tag_Incident - unauthorized data usage for AI model training: 1
- Tag_Consequence - public user backlash & concern about AI: 1
- Tag_Source - researchers & research institutions: 1

## Original Data Files Structure

### original_data/AI-Codebook.csv
**Format:** Long-form codebook showing all applied tags
**Content:** Each row represents one tag applied to one incident
**Structure:** Shows the relationship between incidents, tags, and themes

**Use:** Understanding tag definitions and examples of how tags are applied

### original_data/AI-IncidentsCodeOnehotencoding.csv
**Format:** One-hot encoded tag matrix (202 rows, 80+ tag columns)
**Content:** Binary matrix showing which tags apply to which incidents
**Structure:** Each tag dimension has its own column with 1/0 values

### original_data/AI-SelectedIncidents.csv
**Format:** Detailed incident descriptions and metadata
**Content:** Full incident information including descriptions, URLs, stakeholders, technologies

### original_data/AItreemap-*.html
Interactive tree visualization files:
- `AItreemap-Incident-Cause-Consequence.html` - Visualizes cause→consequence relationships
- `AItreemap-Incident-Cause-Entity.html` - Visualizes cause→entity relationships
- `AItreemap-Source-Incident-Entity.html` - Visualizes source→incident→entity relationships

## Unlabeled Data Structure

### unlabeled_data/ai_privacy_incidents_unlabeled.csv
**Format:** Incident descriptions without tags
**Rows:** 196 incidents

**Columns:**
- `Note - AIAAIC ID` - Incident identifier
- `Headline` - Brief title
- `Description/links` - Full incident description

**Use case:** Input for LLM-driven incident categorization

## How to Use This Dataset for LLM Qualitative Coding Comparison

### Step 1: Choose Your Coding Scope

Given the complexity of this multi-dimensional coding scheme, you have several options:

**Option A: Single Dimension**
- Start with one dimension (e.g., just Tag_Cause)
- Easier to evaluate
- Tests LLM's ability to identify root causes

**Option B: Multiple Related Dimensions**
- Example: Tag_Cause + Tag_Consequence
- Tests understanding of causal relationships
- More realistic scenario

**Option C: All Dimensions**
- Complete multi-dimensional coding
- Most challenging
- Tests comprehensive incident analysis

**Option D: Specific Tag Subsets**
- Focus on most common tags (e.g., top 10 tags per dimension)
- Reduces complexity while maintaining richness
- Good for focused evaluation

### Step 2: Understand the Taxonomies

Before coding, familiarize yourself with:
- **Tag definitions:** What each category means
- **Tag examples:** Review how humans applied each tag
- **Tag relationships:** How different dimensions interact
- **Multi-coding:** Incidents often have multiple tags per dimension

### Step 3: Set Up Your LLM Coding Task

Use `unlabeled_data/ai_privacy_incidents_unlabeled.csv` as input.

**Prompt Example (Multi-Dimensional Coding):**
```
You are an AI ethics researcher analyzing incidents of AI systems causing privacy or ethical harms.

For each incident, identify relevant tags across the following dimensions:

CAUSES (why did this happen?):
- AI misinterpretation & hallucinations
- Potential AI bias
- Human abuse of AI tools
- Lack of informed consent & transparency
- Poor business ethics
[... list all cause categories ...]

CONSEQUENCES (what were the impacts?):
- Legal action & penalty
- Public user backlash
- Loss of faith in AI tools
[... list all consequence categories ...]

ENTITIES (who/what was responsible?):
- AI developer company
- Large dataset organization
- Malicious human
[... list all entity categories ...]

INCIDENTS (what type of incident?):
- AI data breach
- Nonconsensual imagery
- Unauthorized data use for training
[... list all incident categories ...]

Incident Description:
[paste from Description/links column]

For each dimension, list ALL applicable tags (multiple tags are expected).
```

### Step 4: Compare Results

**Quantitative Comparison:**

```python
import pandas as pd
from sklearn.metrics import classification_report, hamming_loss
import numpy as np

# Load data
human = pd.read_csv('ai_privacy_incidents_coded_data.csv')
llm = pd.read_csv('your_llm_coded_data.csv')

# Get all tag columns by dimension
cause_cols = [col for col in human.columns if col.startswith('Tag_Cause')]
consequence_cols = [col for col in human.columns if col.startswith('Tag_Consequence')]
entity_cols = [col for col in human.columns if col.startswith('Tag_Entity')]
incident_cols = [col for col in human.columns if col.startswith('Tag_Incident')]
source_cols = [col for col in human.columns if col.startswith('Tag_Source')]

# Merge on incident ID
merged = human.merge(llm, on='Note - AIAAIC ID', suffixes=('_h', '_l'))

# Evaluate each dimension
dimensions = {
    'Cause': cause_cols,
    'Consequence': consequence_cols,
    'Entity': entity_cols,
    'Incident': incident_cols,
    'Source': source_cols
}

for dim_name, cols in dimensions.items():
    print(f"\n=== {dim_name} Dimension ===")

    # Get human and LLM tags for this dimension
    h_cols = [col + '_h' for col in cols]
    l_cols = [col + '_l' for col in cols]

    # Calculate metrics
    # Hamming loss (proportion of incorrectly predicted tags)
    h_loss = hamming_loss(
        merged[h_cols].values,
        merged[l_cols].values
    )
    print(f"Hamming Loss: {h_loss:.3f}")

    # F1 score per tag
    for col in cols:
        h_col = col + '_h'
        l_col = col + '_l'
        tp = ((merged[h_col] == 1) & (merged[l_col] == 1)).sum()
        fp = ((merged[h_col] == 0) & (merged[l_col] == 1)).sum()
        fn = ((merged[h_col] == 1) & (merged[l_col] == 0)).sum()

        precision = tp / (tp + fp) if (tp + fp) > 0 else 0
        recall = tp / (tp + fn) if (tp + fn) > 0 else 0
        f1 = 2 * precision * recall / (precision + recall) if (precision + recall) > 0 else 0

        if tp + fn > 2:  # Only show tags that appear > 2 times
            tag_name = col.replace('Tag_' + dim_name + ' - ', '')
            print(f"{tag_name}: F1={f1:.3f} (P={precision:.3f}, R={recall:.3f})")
```

**Tag Distribution Analysis:**
```python
# How many tags per incident?
def count_tags(row, cols):
    return row[cols].sum()

human['n_causes'] = human.apply(lambda x: count_tags(x, cause_cols), axis=1)
llm['n_causes'] = llm.apply(lambda x: count_tags(x, cause_cols), axis=1)

print(f"Human avg causes per incident: {human['n_causes'].mean():.2f}")
print(f"LLM avg causes per incident: {llm['n_causes'].mean():.2f}")
```

### Step 5: Qualitative Analysis

**Multi-Tag Consistency:**
- Does LLM apply an appropriate number of tags per dimension?
- Are tag combinations logical?
- Does LLM recognize when multiple causes/consequences/entities apply?

**Cross-Dimension Logic:**
- Do LLM's cause tags align logically with consequence tags?
- Do entity tags match the incident type?
- Are tag combinations sensible?

**Examples:**
```python
# Find incidents where LLM assigned very different tag counts
merged['tag_diff'] = abs(merged['n_causes_h'] - merged['n_causes_l'])
outliers = merged.nlargest(10, 'tag_diff')

for _, row in outliers.iterrows():
    print(f"\nIncident: {row['Headline_h']}")
    print(f"Human causes: {row['n_causes_h']}, LLM causes: {row['n_causes_l']}")
    print(f"Description: {row['Description/links_h'][:200]}...")
```

### Step 6: Advanced Evaluation

**Tag Co-occurrence Analysis:**
```python
from itertools import combinations

# Which tags tend to appear together?
def get_cooccurrence(df, cols):
    cooccur = {}
    for _, row in df.iterrows():
        active_tags = [col for col in cols if row[col] == 1]
        for pair in combinations(sorted(active_tags), 2):
            cooccur[pair] = cooccur.get(pair, 0) + 1
    return cooccur

human_cooccur = get_cooccurrence(human, cause_cols)
llm_cooccur = get_cooccurrence(llm, cause_cols)

# Compare top co-occurring pairs
print("Top cause tag pairs (Human):")
for pair, count in sorted(human_cooccur.items(), key=lambda x: x[1], reverse=True)[:10]:
    tag1 = pair[0].replace('Tag_Cause - ', '')
    tag2 = pair[1].replace('Tag_Cause - ', '')
    print(f"{tag1} + {tag2}: {count}")
```

**Dimension-Specific Error Patterns:**
- Are some dimensions easier for LLM than others?
- Do certain types of incidents get mis-coded more often?
- Are rare tags harder for LLM to identify?

### Step 7: Key Evaluation Questions

1. **Multi-Dimensional Understanding:**
   - Can LLM code across all 5-6 dimensions consistently?
   - Does LLM maintain logical relationships between dimensions?

2. **Multi-Label Classification:**
   - Does LLM recognize when multiple tags apply?
   - Does it over-tag or under-tag compared to humans?

3. **Domain Knowledge:**
   - Does LLM understand AI ethics and privacy concepts?
   - Can it distinguish nuanced tag categories?
   - Does it understand technical AI terminology?

4. **Taxonomic Consistency:**
   - Are LLM's tagging patterns internally consistent?
   - Does it apply similar tags to similar incidents?

5. **Rare vs. Common Tags:**
   - Does LLM identify rare tags as well as common ones?
   - Are there systematic biases toward certain tags?

## Dataset Statistics

- **Total incidents:** 196 coded incidents
- **Coding dimensions:** 5-6 major dimensions
- **Total unique tags:** 80+ across all dimensions
- **Multi-tag coding:** Most incidents have multiple tags per dimension
- **Time range:** Incidents from 2020-2024
- **Geographic scope:** Global incidents
- **Data sources:** Media reports, regulatory investigations, research studies

### Incident Characteristics
- Privacy violations (data breaches, unauthorized use)
- Ethical harms (bias, discrimination, manipulation)
- Technical failures (AI hallucinations, malfunctions)
- Governance failures (lack of oversight, poor ethics)
- Involves major tech companies (OpenAI, Google, Meta, etc.)
- Regulatory actions and legal consequences

## Citation & Source

**Source:** https://www.aiaaic.org/
**Project:** AI, Algorithmic, and Automation Incidents and Controversies (AIAAIC) Repository
**Domain:** AI Ethics, Privacy, Technology Policy
**Maintained by:** AIAAIC Research Team

## Notes & Considerations

### Strengths
- **Multi-dimensional taxonomy:** Comprehensive incident characterization
- **Real-world incidents:** Actual reported AI harms
- **Rich metadata:** Detailed incident information beyond just tags
- **Multiple perspectives:** Causes, consequences, entities, types all captured
- **Current and evolving:** Recent incidents (2020-2024)
- **Policy-relevant:** Useful for AI governance and regulation
- **Multi-tag coding:** Reflects complexity of real incidents

### Challenges for LLMs
- **Taxonomic complexity:** 80+ tags across multiple dimensions
- **Multi-label classification:** Most incidents have many tags
- **Subtle distinctions:** Some tag categories are very similar
- **Domain expertise:** Requires understanding of AI ethics, privacy law, tech policy
- **Interconnected dimensions:** Tags across dimensions must be logically consistent
- **Rare tags:** Some categories have very few examples
- **Evolving terminology:** AI ethics language is still developing

### Best Use Cases
- **Multi-dimensional categorization:** Testing comprehensive incident analysis
- **AI ethics research:** Understanding patterns in AI harms
- **Multi-label classification:** Evaluating complex tagging scenarios
- **Taxonomy application:** Can LLM learn and apply detailed taxonomies?
- **Causal reasoning:** Identifying causes and consequences
- **Policy analysis:** Informing AI governance and regulation

## Coding Quality

**Rating:** ⭐⭐⭐⭐ High Quality

- Comprehensive multi-dimensional taxonomy
- Real-world incidents with detailed documentation
- Binary one-hot encoding makes evaluation straightforward
- Rich metadata for context
- Policy-relevant and current
- Excellent for testing LLM multi-label classification and taxonomic reasoning
