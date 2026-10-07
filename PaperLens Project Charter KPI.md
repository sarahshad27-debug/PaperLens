**Project Charter & KPI Document**

AI Prompt Engineering & Chatbot Application  

Project: PaperLens (Research Paper Assistant)

| Item | Detail |
| :---- | :---- |
| Prepared by | Sarah Shad |
| Project duration | 4 weeks   |
| Tools | Python, OpenAI API, Streamlit, Prompt Templates, JSON / Pandas |
| Version/status | v1.0 \- Draft for approval |

# **1\. Problem statement**

# Reading academic papers can be a slow and challenging process for students. The content is often dense, with essential information such as the problem, method, data, results, and limitations scattered throughout multiple pages. Additionally, general-purpose chatbots may introduce inaccuracies by fabricating details not present in the original paper. Therefore, students need a reliable, efficient way to quickly grasp a paper's key concepts.

# **2\. Project goal**

## Develop PaperLens: a Streamlit-based chatbot designed to transform a research paper (either in PDF format or as pasted text) into a structured JSON summary that includes eight specified fields. Additionally, it should be capable of addressing follow-up questions using the content from the paper itself. The quality of the summaries will be evaluated by comparing three versions of the prompt against a gold-standard test set.

## **Objectives**

* Design and version-control prompt templates (v1 baseline, v2 rules, v3 rules \+ example \+ strict JSON schema).

* Deliver a working prototype with a summary view, grounded Q\&A chat, and JSON export.

* Prove improvement with data: accuracy, valid-JSON rate, hallucination rate, and latency per prompt version.

* Document the process as SOPs so another student can maintain and extend the tool.

# **3\. Scope**

## **In scope**

* PDF and pasted-text input; character cap for long papers.

* Structured summary: title, research problem, method, dataset, key results, limitations, contribution type, plain-language summary.

* Grounded follow-up Q\&A chat; per-run logging of latency and tokens.

* Evaluation script, gold set of 5-10 papers, pilot test with 5+ users.

## **Out of scope**

* Multi-paper comparison, citation graph, model fine-tuning, user accounts, scanned-PDF OCR.

# **4\. Stakeholders and users**

| Group | Role in project | Involvement |
| :---- | :---- | :---- |
| Student readers (peers, chapter members) | Primary users | Interviews in Week 1; pilot testing in Week 3 |
| Project owner (Sarah) | Designer, developer, analyst | All deliverables |

# **5\. KPIs and success metrics**

All targets below are proposed and become final on approval of this charter. Baselines are measured in the Baseline Audit and the Week 3 evaluation.

| KPI | Target | Baseline source | How measured | When |
| :---- | :---- | :---- | :---- | :---- |
| Stakeholder alignment and scope approval | 100% | n/a | Signed approval below | Week 1 |
| Field accuracy (v3 on gold set) | \>= 80% | v1 score | eval/run\_eval.py keyword scoring | Week 3 |
| Accuracy gain, v1 to v3 | \>= \+15 points | v1 score | eval/summary.csv | Week 3 |
| Valid JSON rate | 100% | v1 rate | eval/run\_eval.py | Week 3 |
| Hallucination rate | \<= 5% of fields | Generic chatbot test | Manual check of 10 outputs against paper | Week 3 |
| Average response time | \< 15 seconds | n/a | Logged latency per run | Week 3 |
| User satisfaction | \>= 4 / 5 (5+ testers) | n/a | Short feedback form | Week 3 |
| Time saved vs manual summary | \>= 50% reduction | Manual timing in audit | Stopwatch comparison on 2 papers | Week 3-4 |

# **6\. Deliverables and timeline**

| Week | Focus | Deliverables | Approval metric |
| :---- | :---- | :---- | :---- |
| 1 | Scope and baseline | Baseline audit report, charter and KPI document, workspace setup | 100% stakeholder alignment |
| 2 | Framework and workflow design | Core framework draft, standardized templates, test scenario log | Framework approved, no critical gaps |
| 3 | Execution and tool integration | Integrated workflows, pilot data, SLA and QA checklist | Pilot metrics \>= 80% |
| 4 | SOPs and presentation | Final SOPs, executive deck, 3-5 min demo video, case study | 100% deliverable approval |

# **7\. Risks and mitigations**

| Risk | Impact | Mitigation |
| :---- | :---- | :---- |
| Model invents details not in the paper | High | 'Not stated' rule, grounded Q\&A, hallucination KPI, strict JSON schema |
| Long PDFs exceed model input limits | Medium | Character cap now; chunking as a stretch goal |
| Scanned PDFs contain no extractable text | Medium | Detect empty extraction and show a clear warning |
| API cost or access problems | Medium | Small model, temperature 0, input cap; provider is configurable |
| Behind schedule | High | Weekly checkpoint on master sheet; cut stretch goals first |

# **8\. Workspace structure**

* Code repository: app.py, extractor.py, prompts/, eval/, docs/.

* Master sheet (PaperLens\_Master\_Tracker.xlsx): Dashboard, Tasks, KPIs, Interviews, Papers, Risks.

* Documents folder: charter, baseline audit, test scenario log, SOPs, final case study, demo video.

