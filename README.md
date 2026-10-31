<!--
  github.com/asilkanvar96 profile README (draft).
  Structure: a naturalist's field notebook. A frontispiece, then one plate per group, then that group's projects.
  Plate prompts and style guide: assets/PROMPTS.md. Images are JPGs in assets/; rule.svg is the divider.
  Every plate's meaning is repeated as text under it, so nothing lives only inside an image.

  Before publishing:
  - pheno-pilot stays private while the follow-up stage runs; add its link only when it is public.
  - fin-comp: one-line description and whether it can be named publicly (TODO from Asilkan).
  - Memory/RAG/harness repos get links only once they exist.
  - The invoice case study link goes in only when that repo exists.
  - Never name the invoice client here. The personal agent itself is not mentioned.
-->

<p align="center">
  <img src="assets/frontispiece.jpg" width="100%" alt="Frontispiece: an open field notebook seen from above. On the left page five small agent specimens, part moth and part instrument with glass bodies and a faint inner light, are drawn in a row with pencil measurement lines. On the right page one specimen is sketched in flight over a meadow. A pencil, a hand lens and a pressed leaf lie across the pages.">
</p>

<p align="center">
  <i><b>Frontispiece.</b> Field notes on artificial agents.</i>
</p>

# İ. Asilkan Var

I study how LLM agents behave when their experience contradicts what they already believe, and I build the memory and production systems they run on.

My research question right now is whether agents learn where they are wrong, and whether that changes what they do. At work I build and run an LLM invoice-matching system for a retail client, which keeps me close to what breaks once a model meets real data. My MBA thesis used a language model to score company annual reports.

[LinkedIn](https://www.linkedin.com/in/asilkanvar) · varasilkan@gmail.com

**Sections** · [I. Agent behavior](#i-agent-behavior) · [II. Memory and retrieval](#ii-memory-and-retrieval) · [III. LLMs in production](#iii-llms-in-production)

<p align="center"><img src="assets/rule.svg" width="380" alt=""></p>

## I. Agent behavior

<p align="center">
  <img src="assets/plate-behavior.jpg" width="100%" alt="Plate I, The Field: small agent specimens fly across a meadow at dusk, each carrying a tiny compass. Over one patch the needles all point the wrong way. Most agents glow brighter at its edge as if they noticed; only one or two land to look at their compass. An open notebook and a hand lens rest on a folding stool in the foreground.">
</p>

<p align="center">
  <i><b>Plate I. The Field.</b> Most of them noticed the compass was wrong. Few started checking it.<br>
  Controlled experiments on what agents learn from experience, and whether it changes how they act.</i>
</p>

**Pheno: do LLM agents learn where they are wrong?** · in progress, code and data released after the follow-up stage

Ten agents live 60 simulated days in a world where some domains contradict common sense. They are compared against twin, yoked and no-experience control agents. The design is preregistered and everything runs locally (Qwen3.5-27B on MLX).

In the pilot the agents learned where they were wrong (AUROC2 +0.31, 90% CI 0.20–0.42, against a twin noise level of 0.06), but they barely changed their behavior: verification rose only from 9% to 11%. The follow-up stage is running now.

**Fin-Comp: a trading firm run by local agents** · in progress

A simulated trading company whose analyst, researcher, trader and risk teams are local LLM agents (TradingAgents on Qwen through MLX), running every night on a $100,000 paper portfolio of five US stocks. Hard-coded risk rules sit between the agents and every trade. Daily profit and loss gives an objective score, which makes it a testbed for the real question: do agents improve more through automatic self-improvement or through a ledger of lessons a person curates?

**MBA thesis: annual reports and company value** · Istanbul University, 2025

A GPT-4o-mini pipeline with RAG derived a six-metric rubric and scored 27 BIST30 annual reports for 2023. The scores showed no significant relationship with market value change, revenue growth or stock performance (r at most 0.17). The null result taught me more than the pipeline did: a model that writes its own rubric and grades against it needs an outside baseline.

## II. Memory and retrieval

<p align="center">
  <img src="assets/plate-memory.jpg" width="100%" alt="Plate II, The Herbarium: a small room of wooden cabinets with one drawer open on pressed, tagged specimen sheets. On the table, cards are linked by fine red threads like a map of relations, and a specimen agent rests beside a lamp with its light dimmed, as if asleep between sessions.">
</p>

<p align="center">
  <i><b>Plate II. The Herbarium.</b> What is not pressed, labeled and dated is not remembered.<br>
  What an agent keeps between sessions, and how it finds it again.</i>
</p>

| Project | Status |
|---|---|
| **Memory engine**: a schema-first wiki memory that keeps world knowledge apart from the agent's own working notes, with a timeline of how each page changed | in progress |
| **Retrieval with an eval set**: hybrid keyword and vector search, reranking, permission filtering and citations, measured against a published question set | planned |
| **Agent harness**: a small local agent loop that uses the memory engine and records what it did and why | planned |
| **Company memory**: the three pieces above put together as an end-to-end product for internal documents | planned |
| **[claude-github-wf](https://github.com/asilkanvar96/claude-github-wf)**: a Claude Code skill that runs branch, commit, push and PR from chat, in English or Turkish | public |

## III. LLMs in production

<!-- TODO: plate-production.jpg not generated yet; restore this block when it exists.
<p align="center">
  <img src="assets/plate-production.jpg" width="100%" alt="Plate III, The Release: a field station at the edge of a forest in the morning. Most small jars on a sorting table are already sorted into wooden trays; a few uncertain ones sit under a lamp where one specimen agent examines them. An open ledger, a stamp and an ink pad wait for a person to sign off, and tagged specimens fly out toward the trees.">
</p>
-->

<p align="center">
  <i><b>Plate III. The Release.</b> Rules sort most of it. The model looks at what is left, and a person signs off.</i>
</p>

**AI invoice matching** · client work, code is private

A nightly system that matches about 4,000 supplier invoices against 18,000 goods receipts. Exact rules and fuzzy scoring settle most pairs; only 8–9% of invoices reach the LLM, a fine-tuned model served with vLLM on our own GPU. A LangGraph workflow scores candidates, people approve the matches, and approved matches become history for the next suggestions. Prompt prefix caching made scoring 3.2x faster, and about 6x together with parallel requests.

A case study with synthetic data is in preparation.

<p align="center"><img src="assets/rule.svg" width="380" alt=""></p>

## Tools

Python, LangGraph, Pydantic, vLLM, Ollama, MLX, SQL, Oracle, OCI, AWS SageMaker, Linux, pytest, Git

## Older work

<details>
<summary>Earlier learning projects, kept public</summary>

- [Titanic_EDA-ML](https://github.com/asilkanvar96/Titanic_EDA-ML): exploratory analysis and classic ML on the Kaggle Titanic data (2019)
- [MNIST-Digit_Recognizer_CNN_TF_GPU](https://github.com/asilkanvar96/MNIST-Digit_Recognizer_CNN_TF_GPU): CNN digit recognizer trained on GPU with TensorFlow (2020)
- [apriori-heroku](https://github.com/asilkanvar96/apriori-heroku): association rule mining app deployed on Heroku (2022)
- [mlzoomcamp_hws](https://github.com/asilkanvar96/mlzoomcamp_hws): ML Zoomcamp homework (2022)
- [100DaysOfCloud](https://github.com/asilkanvar96/100DaysOfCloud): cloud learning log (2023)

</details>
