# Replication Package for `Code Review Comprehension: Reviewing Strategies Seen Through Code Comprehension Theories`

## Abstract

Modern code review is an integral part of the development process of many software projects. However, there is only a superficial knowledge of the cognitive aspects that enable reviewers to analyze the code and provide feedback. Understanding the code change under review is the most needed competence of reviewers as well as their main challenge.
Thus, we observed and interviewed ten experienced reviewers performing 25 reviews from their review queue. We use Letovsky's model of code comprehension to perform an in-depth theory-driven thematic analysis to understand how reviewers use code comprehension to navigate the change and provide feedback.

We observed that code comprehension is indeed central to performing code review. We contribute an extension of Letovsky's model---the Code Review Comprehension Model---and describe that code review, like code comprehension, is driven by opportunistic strategies. These strategies usually start with a context-building phase and continue with code inspection that consists of code reading, testing, and discussion management. Developers form a mental model of the changeset under review as an extension of their mental model of the software system and use their mental models of expected and ideal solutions to understand and evaluate the proposed changes. These insights into cognitive processes of reviewers contributes to actionable guidelines to build more human-centric code review tools and reviewing practices.


## Structure
```
README.md

Study-Design/
    interview_structure.pdf
    demographics_survey.pdf
    participant_consent.pdf

Data-Analysis/

    codes/
    coding_schema_2
    coding_schema_theory-driven.png
    codebook.pdf
    codes.docx

    co_author_review_1/
        coded_transcript_P4R1.pdf
        coauthor_notes_P4R1.txt
        ...
    co_author_review_2/
        coded_transcript_P2R2.pdf
        coauthor_notes_P2R2.txt

    transcripts/
        P1R1.rtf
        P1R2.rtf
        ...
```

## Contents of the Replication Package

### `Study-Design`
Contains documents that outline the study’s methodology and design:
- `interview_structure.pdf`: Structure and sample questions for the interview sessions.
- `demographics_survey.pdf`: Survey capturing demographic data of participants.
- `participant_consent.pdf`: Consent form signed by study participants.

### `Data-Analysis`
Contains raw and coded data used in the analysis.

- `codes/`:file used for qualitative analysis.
    - `coding_schema_2`: The coding schema created based on Piglet's model of cognitive devlopment and Letovsky's comprehension model.
	- `coding_schema_theory-driven.png`:The initial coding schema created based off Letovsky's comprehension model and other theories as reported in the paper.
	- `codebook.pdf`: A complete list of codes created in the analysis

- `co_author_review_1/`: Documents from the first co-author review, including coded transcripts and reviewer notes.

- `co_author_review_2/`: Documents from the second co-author review, including coded transcripts, reviewer notes, and coding schema for knowledge and mental models.

- `transcripts/`: Raw transcripts from code review sessions (e.g., `P1R1.rtf` for Participant 1, Review 1).

