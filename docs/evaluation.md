# Evaluation protocols

Document intelligence is a layered problem. The protocol should report where a system succeeds and where information is lost.

## Metric map

| Layer | Task | Metrics | What it measures | Main failure if used alone |
| --- | --- | --- | --- | --- |
| Visual | restoration/dewarping | PSNR, SSIM, OCR-after-restoration | image or downstream readability | visual similarity may not preserve semantics |
| Primitive | detection/segmentation | IoU, mAP, precision, recall, F1 | region and element localization | does not test relations or meaning |
| Text | OCR/recognition | CER, WER, exact match, normalized edit distance | transcription fidelity | can ignore layout and reading order |
| Structure | tables/layout/order | TEDS, tree edit distance, graph F1, reading-order accuracy | structural recovery | one scalar can hide specific element errors |
| Semantic | IE/VQA | ANLS, EM, token F1, relation F1 | answer/entity correctness | fluent but unsupported answers may pass |
| Grounding | retrieval/citations | evidence precision/recall, citation correctness | whether answers point to the right content | not always available in legacy datasets |
| Agentic | tool use/verification | task success, correction rate, grounded action accuracy, abstention | closed-loop behavior | requires explicit trajectories and failure labels |
| Systems | deployment | latency, memory, tokens/page, cost/page, throughput | practical efficiency | hardware and batching change results |

## Minimum reporting card

For every benchmark result, record:

1. dataset version, split, and preprocessing;
2. page resolution and maximum input length;
3. model checkpoint and prompt or decoding settings;
4. whether OCR, layout, retrieval, or external tools are used;
5. exact metric implementation and normalization;
6. hardware, batch size, latency, and token/cost accounting;
7. failure categories and at least one qualitative example;
8. license and data-access constraints.

## Stress tests for a document world model

- **Occlusion and missing structure:** remove a region, page, or cross-reference and test uncertainty-aware recovery.
- **Layout shift:** evaluate unseen templates, rotated pages, multi-column pages, and mixed reading orders.
- **Semantic contradiction:** insert inconsistent values across tables, text, and captions.
- **Long-document state:** test cross-page entity consistency and citation locality.
- **Tool choice:** measure whether an agent chooses zoom, OCR, retrieval, rendering, or abstention appropriately.
- **Cost-quality frontier:** report accuracy against tokens, memory, latency, and monetary cost.
