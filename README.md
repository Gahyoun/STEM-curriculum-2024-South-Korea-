# STEM Curriculum (2024, South Korea)

This repository contains the data, code, and methodologies used to analyze interdisciplinarity in South Korea's STEM higher education curricula for 2024. By leveraging natural language processing (NLP) and network science techniques, we quantify interdisciplinary synergy and design optimized curricula for single and dual-discipline programs.

## Repository Structure

```
STEM-curriculum-2024-South-Korea/
├── data/
│   ├── bipartite network data.xlsx             # processed data
├── notebooks/
│   ├── STEM language data proceessing.ipynb    # with Gemini
│   ├── Single major & Double major.ipynb
│   ├── css calculate.ipynb
├── results/
│   ├── single_major.xlsx            
│   ├── double major.zip           
├── README.md            
```

## Overview

The goal of this project is to create a systematic framework to analyze and enhance interdisciplinary connections within STEM education. This involves standardizing raw course data, quantifying department similarities, and designing interdisciplinary curricula. The results provide insights into how interdisciplinary approaches can be systematically implemented in higher education.

## Data Sources

The datasets used in this project are sourced from the publicly available portal operated by the Ministry of Education in South Korea. Key datasets include:

1. **"Curriculum per Educational Unit by School"** (학교별 교육편제단위의 교육과정(2024.03.05.기준)):
   - Provides detailed course data for undergraduate programs across all higher education institutions in South Korea.
   - [View Raw Data](https://academyinfo.go.kr/brd/brd0520/selectDetail.do?ntce_sntc_sno=150&bbs_gubun=rfbr&no=146)

2. **"List of Undergraduate Departments and Majors by School"** (2024년 상반기 기준 학교별 학부/과(전공) 리스트(2024.03.06.기준)):
   - Metadata used to classify departments and educational fields.
   - **"Standard Classification Information"** (표준 분류정보): Defines the categorization of courses and departments into disciplines such as Engineering and Natural Sciences.
   - [View Raw Data](https://academyinfo.go.kr/brd/brd0520/selectDetail.do?ntce_sntc_sno=151&bbs_gubun=rfbr&no=147)

These datasets ensure comprehensive coverage of the STEM educational landscape in South Korea.

## Methodology

### 1. Data Processing and Standardization
- **Tokenization:**
  - Course titles were segmented into tokens using a large language model (LLM), tailored to handle Korean linguistic properties.
  - Example: `"Statistical Physics"` → `{Statistics, Physics}`.

- **Hyperedge Construction:**
  - Courses with shared tokens were grouped into hyperedges to capture semantic relationships.
  - Example: `"Quantum Mechanics"` and `"Quantum Physics"` were identified as semantically identical.

- **Standardization:**
  - Hyperedges were clustered into connected components to create standardized course units. This process reduced 126,437 raw courses to 24,476 standardized courses.

### 2. Department Similarity Analysis
- **Department Similarity Network (DSN):**
  - Departments were represented as nodes, and weighted edges quantified their curriculum similarity using the weighted Jaccard similarity coefficient.
  - Community detection algorithms (Louvain) were applied to analyze structural patterns across disciplines.

### 3. Curriculum Design
- **Single-Discipline Models:**
  - Developed optimized curricula by selecting foundational courses and incrementally adding others based on information-theoretic metrics (e.g., Jensen-Shannon Divergence).

- **Interdisciplinary Models:**
  - Designed dual-discipline curricula by combining seed courses from two fields and iteratively optimizing for both overlap and emergent information.

### 4. Quantifying Interdisciplinarity
- **Curriculum Synergy Score (CSS):**
  - Measures interdisciplinary synergy by balancing shared similarity and emergent information between disciplines.

## How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/STEM-curriculum-2024-South-Korea.git
   cd STEM-curriculum-2024-South-Korea
   ```

2. Install required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```

3. Run Jupyter notebooks for data analysis and visualization:
   ```bash
   jupyter notebook
   ```

4. Explore results and figures in the `results/` directory.

## Results

- Standardized curricula for 2,841 departments across 161 institutions.
- Department similarity network visualizations, revealing core-periphery structures in STEM disciplines.
- Interdisciplinary curriculum models with quantified synergy scores.

## Contributors

- **Gahyoun Gim** (Gyeongsang National University, GNU)
- **Jinhyuk Yun** (Soongsil University)
- **Sang Hoon Lee** (Gyeongsang National University, GNU)
