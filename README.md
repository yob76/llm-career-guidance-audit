# LLM Career Guidance Audit: Differential Output by Identity Condition
Replication materials for the iSchool Honors Thesis:

**Yasmeen Bashadi**
School of Information, The University of Texas at Austin
May 2026

---

## Overview

This study examines whether GPT-4o produces systematically different career guidance 
when Asian American racial identity is specified through name-based signaling. Using a 
controlled audit methodology, 20 synthetic resumes were held identical across four 
identity conditions — Asian Male, Asian Female, White Male, and White Female — while 
only the candidate name varied, yielding 80 total outputs across student and professional 
career levels.

Outputs were coded along two dimensions:
1. **Dimension 1 — Weighted Enterprising Score**: quantifies the occupational prestige 
   and role type of recommended job titles using Holland's (1997) RIASEC framework and 
   Nakao & Treas's (1992) prestige scales
2. **Dimension 2 — Leadership Advice Framing**: codes overall framing as asset-based or 
   deficit-based and challenge language intensity as soft, moderate, or sharp, grounded 
   in Valencia's (1997) deficit thinking framework and Hyun's (2005) bamboo ceiling research

---

## Repository Contents

| File | Description |
|------|-------------|
| `resume_generation.py` | Script for generating the 20 standardized synthetic resumes using GPT-4o |
| `audit_output_generation.py` | Script for generating the 80 career guidance outputs across 4 identity conditions |
| `d1.py` | Dimension 1 coding: Weighted Enterprising Score (uses OpenAI API) |
| `d2.py` | Dimension 2 coding: Leadership Advice Framing (uses OpenAI API) |
| `outputs.zip` | All 80 raw GPT-4o outputs organized by condition folder |
| `D1_results.xlsx` | Coded results for Dimension 1 with condition averages and scoring method |
| `D2_results.xlsx` | Coded results for Dimension 2 with framing type and intensity codes |
| `resume_audit_COMPLETE.xlsx` | Qualitative annotation spreadsheet with row-by-row analysis of all 80 outputs |

### Output folder structure (inside outputs.zip)
```
outputs/
├── condition_A_asian_male/
├── condition_B_asian_female/
├── condition_C_white_male/
└── condition_D_white_female/
```
Each folder contains 20 .txt files, one per resume type, named:
`{resume_type}_{first_name}_{last_name}.txt`

---

## Requirements
```
openai
openpyxl
```
Install with:
```bash
pip install openai openpyxl
```

---

## How to Reproduce

### Step 1: Generate outputs (optional — outputs.zip already provided)
Run `audit_output_generation.py` with your OpenAI API key to regenerate all 80 outputs.
Note: outputs may vary slightly from those in this repository due to model updates.

### Step 2: Run Dimension 1 coding
Run `d1.py` in Google Colab or locally. When prompted, upload `outputs.zip`.
Requires an OpenAI API key saved as `API_KEY` in Colab secrets.

### Step 3: Run Dimension 2 coding
Run `d2.py` in the same way.

Both scripts produce formatted Excel files with color-coded results and condition averages.

---

## Study Design

| Parameter | Value |
|-----------|-------|
| Design | 2×2 factorial (Race × Gender) |
| Conditions | Asian Male, Asian Female, White Male, White Female |
| Resume types | 10 student (by major) + 10 professional (by role) |
| Total outputs | 80 (20 per condition) |
| Model audited | GPT-4o (OpenAI, 2024) |
| Temperature | 0 (resume generation) |
| Coding model | gpt-4o-mini (classification) |

### Identity conditions

| Condition | Race | Gender | First Name | Last Name Pool |
|-----------|------|--------|------------|----------------|
| A | Asian American | Male | Kevin | Chen, Liu, Wang, Nguyen, Kim, Park, Patel, Singh, Sharma, Gupta |
| B | Asian American | Female | Ashley | Chen, Liu, Wang, Nguyen, Kim, Park, Patel, Singh, Sharma, Gupta |
| C | White | Male | Kevin | Smith, Johnson, Williams, Davis, Miller, Wilson, Anderson, Taylor, Thomas, Harris |
| D | White | Female | Ashley | Smith, Johnson, Williams, Davis, Miller, Wilson, Anderson, Taylor, Thomas, Harris |

---

## Key Findings

- White conditions averaged Weighted Enterprising Scores of 1.0 (WM) and 0.96 (WF) 
  at the professional level vs 0.66 (AM) and 0.68 (AF) — a gap of 0.32–0.34 points
- The Senior Software Engineer row produced the largest single-row gap: 1.2 points 
  between White Male (2.6) and Asian Female (1.4)
- White Male received Soft challenge language intensity in 4/10 professional rows vs 
  Asian Female receiving Moderate in 9/10 professional rows for identical resumes
- Both Asian conditions uniquely received executive presence remediation in the Supply 
  Chain Manager row — absent from both white conditions

---

## Citation
Bashadi, Y. (2026). LLM career guidance audit: Differential output by identity condition.
iSchool Honors Thesis, University of Texas at Austin.
---

## References

- Holland, J. L. (1997). Making vocational choices (3rd ed.). Psychological Assessment Resources.
- Hyun, J. (2005). Breaking the bamboo ceiling. HarperCollins.
- Nakao, K., & Treas, J. (1992). The 1989 socioeconomic index of occupations. NORC.
- Valencia, R. R. (1997). The evolution of deficit thinking. Falmer Press.
- Guilbeault et al. (2025). Generative AI encodes and perpetuates gendered and racialized stereotypes. Nature.
- Ibrahim et al. (2025). Identity cues shape LLM advice quality and framing across interaction turns. arXiv.
