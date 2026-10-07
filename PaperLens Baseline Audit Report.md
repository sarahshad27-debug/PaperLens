**Baseline Audit Report**

AI Prompt Engineering & Chatbot Application  |  PaperLens  |  Week 1

**1\. Purpose and Methodology**  
This audit aims to document how students currently engage with research papers, identify the tools available for the project, and evaluate the capabilities of a standard chatbot without prompt engineering. The findings will serve as benchmarks that PaperLens must surpass.   
\- Method 1: Conduct stakeholder interviews with 5-8 student readers.   
\- Method 2: Measure manual summary timing on two research papers.   
\- Method 3: Perform a generic chatbot test using the same two papers.   
\- Method 4: Review the existing technical toolset.   
   
**2\. Current Workflow Audit**  
The following steps outline the typical manual process. The identified pain points are hypotheses that will be validated or refuted through the interviews.

| Step | Typical approach today | Likely pain point (hypothesis) |
| :---- | :---- | :---- |
| 1\. Find and open paper | Search, download PDF | Unsure whether the paper is relevant before investing time |
| 2\. Skim | Read abstract, intro, conclusion | Abstracts omit limitations and data details |
| 3\. Extract key facts | Highlight and take notes by hand | Slow; notes are inconsistent between papers |
| 4\. Understand jargon | Search terms online | Breaks reading flow; context is lost |
| 5\. Summarize or compare | Write own summary | Time-consuming; easy to misremember results |
| 6\. Ask questions | General chatbot or classmates | Answers may not be grounded in the paper and can include invented details |

# **3\. Technical toolset audit**

| Tool | Role in project | Strength | Risk/limitation | Decision |
| :---- | :---- | :---- | :---- | :---- |
| Python | Backend logic, PDF text extraction, scripting | Rich libraries (pypdf, pandas) | Scanned PDFs yield no text | Use; warn on empty extraction |
| OpenAI API | Summaries, Q\&A, structured JSON output | Strict JSON schema enforcement | Cost, API key handling, possible hallucination | Use small model, temp 0, key in .env |
| Streamlit | Chat and summary interface | Fast prototype, built-in chat widgets | Reruns on interaction; limited custom design | Use with session state |
| Prompt templates | Versioned prompts (v1-v3) in JSON files | Enables controlled A/B comparison | Prompt drift if unversioned | Version every change |
| JSON / Pandas | Schema, logging, evaluation tables | Easy aggregation and export | Low | Use |

# 

# **4\. Baseline measurements**

## **4.1 Manual summary timing**

Pick 2 papers of different lengths. Time how long it takes to produce the 8 PaperLens fields by hand.

| Paper | Pages | Minutes to complete 8 fields | Notes |
| :---- | :---- | :---- | :---- |
| The Black Box Problem: AI Decision-Making in Critical Infrastructure and Its Implications  | \[27 \] | \[220 \] | The terminology was kind of hard to read cause it was too direct. |
| A Quantum Probability Approach to Improving Human-AI Decision-Making | \[16 \] | \[170 \] | The briefs and methodologies were confusing. |

## **4.2 Generic chatbot test (no prompt engineering)**

Paste each paper into a general chatbot with the single instruction 'Summarize this paper'. Record results and compare to your own manual summary.

| Paper | Seconds to respond | Fields covered (of 8\) | Unsupported or wrong statements | Same format each time? |
| :---- | :---- | :---- | :---- | :---- |
| The Black Box Problem: AI Decision-Making in Critical Infrastructure and Its Implications | \[120\] | \[5\] | \[None \] | \[Yes\] |
| A Quantum Probability Approach to Improving Human-AI Decision-Making | \[90\] | \[7\] | \[1\] | \[Yes\] |

## **4.3 Stakeholder interviews**

Suggested questions (10 minutes each):

* How often do you read research papers, and for what purpose?

* How long does it take you to understand one paper?

* What is the hardest part: finding key results, jargon, methods, or something else?

* Have you used an AI chatbot for papers? What went wrong?

* What would make you trust a summary tool? What would make you stop using it?

* Which fields matter most: problem, method, dataset, results, limitations?

Summary of results (complete after interviews):

| Metric | Result |
| :---- | :---- |
| Number of interviewees | \[9\] |
| Average time to understand one paper | \[6-7 days\] |
| Top 3 pain points | 1\) Hard to know what gaps it covers 2\) Confusing methodologies and incorrect citations 3\) Not easy to pinpoint the solution  |
| Most requested fields | \[Key points, problem Statements, and gaps \] |
| Main trust requirement | \[Reliability of the content being right \] |

# **5\. Findings and implications**

| Finding | Implication for design |
| :---- | :---- |
| Generic chatbots give unstructured, unverified output (to be confirmed by test 4.2) | Fixed JSON schema and 'Not stated' rule in the prompt |
| Manual summarizing is slow (to be quantified in 4.1) | Time-saved KPI with a measured baseline |
| Trust is the main adoption barrier (to be confirmed by interviews) | Grounded Q\&A that refuses to answer beyond the paper; hallucination KPI |

# **6\. Conclusion and next steps**

The baseline gives PaperLens three comparison points: manual effort, generic chatbot quality, and the v1 prompt. Week 2 designs the framework and templates to beat these baselines.

* Update the KPI sheet with measured baselines.

* Get the charter approved by the domain lead.

* Begin Week 2: framework design, templates, and test scenario log.