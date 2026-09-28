# Datasets and benchmarks

Links below are public starting points. Dataset terms, splits, annotation licenses, and evaluation scripts should be checked before use.

| Family | Resource | Main task | Typical outputs | Common metrics | Notes |
| --- | --- | --- | --- | --- | --- |
| Layout | [PubLayNet](https://arxiv.org/abs/1908.07836) | page-region detection | boxes and classes | mAP, IoU | large-scale automatically labeled corpus |
| Layout | [DocBank](https://arxiv.org/abs/2006.01038) | token-level layout analysis | token labels | F1, precision/recall | derived from document sources |
| Layout | [DocLayNet](https://arxiv.org/abs/2206.01062) | human-annotated page layout | boxes and classes | mAP, IoU | diverse page categories |
| OCR | [ICDAR Robust Reading](https://rrc.cvc.uab.es/) | text detection and recognition | text boxes/transcriptions | precision/recall, H-mean, CER/WER | multiple challenges and languages |
| Forms | [FUNSD](https://guillaumejaume.github.io/FUNSD/) | form understanding | entities and relations | F1, relation F1 | small but widely used |
| VQA | [DocVQA](https://arxiv.org/abs/2007.00398) | document visual question answering | answer strings | ANLS, EM/F1 | answer normalization matters |
| VQA | [InfoVQA](https://arxiv.org/abs/2104.12723) | information-seeking document QA | answer strings | ANLS, EM/F1 | tests reasoning beyond direct OCR |
| Tables | [TableBank](https://arxiv.org/abs/1903.01949) | table detection/structure | boxes, HTML structure | mAP, TEDS | synthetic and weakly supervised sources |
| Tables | [PubTables-1M](https://arxiv.org/abs/2110.00061) | table structure and recognition | cells and structure | mAP, TEDS | large-scale table annotations |
| Charts | [ChartQA](https://arxiv.org/abs/2203.10244) | chart QA | answers and reasoning | EM, relaxed accuracy | numerical reasoning is separate from OCR |
| End-to-end | [OmniDocBench](https://arxiv.org/abs/2412.07626) | page/document parsing | structured serialization | NED and task-specific metrics | compare conversions under one protocol |
| Scientific | [Nougat](https://arxiv.org/abs/2308.13418) resources | scientific document conversion | markup | edit distance and downstream structure | formula and citation fidelity are important |

## Recommended split dimensions

Report results by more than a random test split whenever possible:

- document type and layout density;
- scan quality, skew, blur, and handwriting;
- language/script and long-tail symbols;
- page resolution and document length;
- seen versus unseen templates;
- tables, formulas, charts, and cross-page references;
- public versus restricted data and reproducibility conditions.

## Dataset selection cautions

- A high OCR score does not imply correct reading order or table structure.
- A page-level benchmark can hide cross-page and long-document failures.
- Synthetic layouts may not represent real scans, historical documents, or enterprise forms.
- VQA accuracy can be inflated by shortcuts if evidence grounding is not checked.
- Reusing benchmark images for training can invalidate zero-shot comparisons.
