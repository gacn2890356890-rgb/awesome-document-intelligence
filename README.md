# Awesome Document Intelligence

> A curated hub for document parsing, document understanding, visual document intelligence, and agentic reasoning.

This repository accompanies the survey **From Pixels to Knowledge: A Survey of Document Parsing, Understanding, and Agentic Reasoning**. It follows the curated-list style of [Awesome VLA](https://github.com/yueen-ma/awesome-vla), while organizing the document field around a structured knowledge substrate:

**pixels → visual primitives → structural relations → semantic intent → grounded actions**

The repository is intended as a living index. Entries are linked to public papers, official project pages, benchmark pages, or source repositories whenever possible. The bibliography shipped with the survey is preserved under [`references/survey-references.bib`](references/survey-references.bib).

## Contents

- [Definitions](#definitions)
- [Taxonomy](#taxonomy)
- [Timeline](#timeline)
- [Papers and surveys](#papers-and-surveys)
- [Datasets and benchmarks](#datasets-and-benchmarks)
- [Evaluation](#evaluation)
- [Tools and implementations](#tools-and-implementations)
- [World models and document agents](#world-models-and-document-agents)
- [Survey figures](#survey-figures)
- [Contributing](#contributing)
- [Citation](#citation)

## Definitions

### Document parsing

Recovering machine-readable content and structure from document images or rendered pages, including text, regions, tables, formulas, reading order, and serialized outputs.

### Document understanding

Assigning semantic roles and relations to the recovered elements: forms, key-value pairs, references, arguments, charts, tables, and document-level questions.

### Document intelligence

An end-to-end capability that combines perception, structure recovery, semantic reasoning, retrieval, verification, and task execution over documents.

### Document world model

A structured, stateful representation of a document that supports entity and relation tracking, prediction of missing or inconsistent structure, active inspection, and grounded interaction. This is a research framing used by the survey; it should not be read as a claim that a single standard implementation already exists.

## Taxonomy

### 1. Perception interface: pixels to primitives

- Preprocessing and restoration: dewarping, denoising, deskewing, binarization, illumination correction.
- Layout analysis: region detection, segmentation, reading-order cues, hierarchy.
- OCR and text recognition: printed, handwritten, multilingual, scene, and dense text.
- Formula and symbol recognition: image-to-markup, LaTeX, chemistry, music, historical scripts.

### 2. Structural mechanisms: primitives to coherent documents

- Reading order and hierarchy reconstruction.
- Table detection, cell structure, and relational graphs.
- Cross-page linking and document-level serialization.
- OCR-free and VLM-based structured generation.
- Hybrid systems that combine lightweight structure detection with high-fidelity recognition.

### 3. Semantic understanding and action

- Visual question answering and information extraction.
- Chart, table, and form reasoning.
- Retrieval-augmented document analysis.
- Verification, citation grounding, and self-correction.
- Tool-using and multi-agent document workflows.

### 4. Capability ladder

- **L1 — Rule/template parsing:** fixed schemas and engineered heuristics.
- **L2 — Specific-element perception:** strong recognition of a defined symbol or element family.
- **L2.5 — Relational parsing:** joint reasoning over text, tables, formulas, and spatial relations.
- **L3 — Universal parsing:** one adaptable system across document types and output formats.
- **L4 — Open-world symbol reasoning:** transfer to unfamiliar symbol systems and emergent document conventions.

## Timeline

| Period | Dominant direction | Representative resources |
| --- | --- | --- |
| 2015–2019 | CNN/RNN OCR, layout detection, table structure | [CRNN](https://arxiv.org/abs/1507.05717), [PubLayNet](https://arxiv.org/abs/1908.07836), [TableBank](https://arxiv.org/abs/1903.01949) |
| 2020–2021 | Multimodal document pretraining and document VQA | [LayoutLM](https://doi.org/10.1145/3394486.3403172), [DocVQA](https://arxiv.org/abs/2007.00398), [LayoutLMv2](https://aclanthology.org/2021.findings-acl.201/) |
| 2022–2023 | OCR-free generation and document foundation models | [Donut](https://arxiv.org/abs/2111.15664), [Nougat](https://arxiv.org/abs/2308.13418), [Pix2Struct](https://proceedings.mlr.press/v202/kantorov-23a.html) |
| 2024–2025 | General VLMs, structured parsing, efficiency, and agents | [DocLLM](https://aclanthology.org/2024.acl-long.463/), [Docling](https://github.com/docling-project/docling), [olmOCR](https://github.com/allenai/olmocr) |
| 2025–2026 | Decoupled hybrids, visual token efficiency, and interactive intelligence | See the curated lists in [`docs/resources.md`](docs/resources.md) and the survey figures in [`figures/`](figures/). |

## Papers and surveys

The first curated reading path is in [`docs/reading-list.md`](docs/reading-list.md). It is grouped by problem boundary rather than by model family:

1. document image analysis and layout;
2. OCR and structured recognition;
3. multimodal document understanding;
4. tables, formulas, charts, and forms;
5. efficient visual representations;
6. agents, world models, and grounded reasoning.

The full survey bibliography is available as a machine-readable BibTeX file in [`references/survey-references.bib`](references/survey-references.bib).

## Datasets and benchmarks

See [`docs/datasets.md`](docs/datasets.md) for task definitions, public links, annotations, and selection risks. The main benchmark families are:

- layout and region detection;
- OCR and text recognition;
- table and formula structure;
- visually rich document understanding;
- document question answering and chart reasoning;
- end-to-end page parsing and document conversion;
- long-document, multilingual, and out-of-distribution evaluation.

## Evaluation

See [`docs/evaluation.md`](docs/evaluation.md). A responsible evaluation should report more than a single score:

- perception fidelity: CER/WER, IoU, mAP, symbol accuracy;
- structural fidelity: TEDS, normalized edit distance, tree/graph consistency, reading-order accuracy;
- semantic grounding: ANLS, exact match/F1, citation or evidence correctness;
- robustness: resolution, scan quality, language, format, length, and unseen-layout stress tests;
- systems: latency, memory, token count, cost, throughput, and failure recovery;
- agentic behavior: tool success, verification success, correction rate, grounded action accuracy, and abstention/calibration.

## Tools and implementations

The resource map in [`docs/resources.md`](docs/resources.md) separates open-source converters, OCR engines, layout analyzers, VLMs, retrieval systems, and agent frameworks. A tool is listed as a resource, not as an endorsement; check its license, maintenance status, model-card limitations, and data terms before deployment.

## World models and document agents

The survey's world-model extension is documented in [`docs/world-models-and-agents.md`](docs/world-models-and-agents.md). The key design questions are:

1. What is the typed state of a document page or document set?
2. Which relations are observed, inferred, or uncertain?
3. How can a system predict missing structure and detect contradictions?
4. When should an agent zoom, retrieve, call OCR, render a page, or ask for verification?
5. How should grounded reasoning be evaluated separately from fluent generation?

## Survey figures

All ten figures from the submitted survey version are included without redrawing:

| Figure | Topic | File |
| --- | --- | --- |
| 1 | Document intelligence overview | [`fig01-document-intelligence-overview.png`](figures/fig01-document-intelligence-overview.png) |
| 2 | PRISMA search and selection | [`fig02-prisma-flow.png`](figures/fig02-prisma-flow.png) |
| 3 | Paradigm evolution | [`fig03-paradigm-evolution.png`](figures/fig03-paradigm-evolution.png) |
| 4 | Representative VLM paradigms | [`fig04-vlm-paradigms.png`](figures/fig04-vlm-paradigms.png) |
| 5 | Modular pipeline vs. end-to-end VLM | [`fig05-pipeline-vs-e2e.png`](figures/fig05-pipeline-vs-e2e.png) |
| 6 | Paradigm trade-offs | [`fig06-paradigm-tradeoffs.png`](figures/fig06-paradigm-tradeoffs.png) |
| 7 | Efficient document analysis | [`fig07-efficient-analysis.png`](figures/fig07-efficient-analysis.png) |
| 8 | Vision-as-Text | [`fig08-vision-as-text.png`](figures/fig08-vision-as-text.png) |
| 9 | Technology roadmap | [`fig09-technology-roadmap.png`](figures/fig09-technology-roadmap.png) |
| 10 | L1–L4 capability hierarchy | [`fig10-capability-hierarchy.png`](figures/fig10-capability-hierarchy.png) |

## Contributing

Please open a pull request with:

- paper title, authors, year, and stable public link;
- task category and whether a dataset, codebase, or benchmark is released;
- license or access restrictions when known;
- a one-sentence reason the resource belongs in the taxonomy.

Do not add private manuscripts, unpublished results, personal data, or benchmark numbers that cannot be traced to a public source. See [`CONTRIBUTING.md`](CONTRIBUTING.md).

## Citation

```bibtex
@article{luo2026pixels,
  title   = {From Pixels to Knowledge: A Survey of Document Parsing, Understanding, and Agentic Reasoning},
  author  = {Luo, Jia},
  journal = {Artificial Intelligence Review},
  year    = {2026},
  note    = {Survey repository accompanying the manuscript}
}
```

The repository organization is inspired by [Awesome VLA](https://github.com/yueen-ma/awesome-vla). It is an independent document-intelligence resource and is not affiliated with that project.
