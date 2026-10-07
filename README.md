# Zero-shot Classification of Lanna Buddhist Art with CLIP
### Case study: Wat Phra That Lampang Luang, Lampang, Thailand

This repository contains the code, dataset summary and evaluation results for a study of **zero-shot image
classification** of cultural-heritage photographs from Wat Phra That Lampang Luang using
**CLIP** vision-language models (OpenCLIP).

*Note: The raw image dataset is kept private and is not included in this repository for data privacy and ownership reasons.*

---

## Repository structure
.
├── notebooks/
│ └── clip_zeroshot_wat_lampang_luang.ipynb # full pipeline (Google Colab, T4 GPU)
├── results/ # CSV tables, confusion matrices, environment.json
├── requirements.txt
└── README.md

## Main results: zero-shot (`results/zero_shot_all_conditions.csv`)

| Backbone | Prompt | Prompts / class | Top-1 (%) | Top-3 (%) | Macro-F1 |
|---|---|:---:|:---:|:---:|:---:|
| ViT-B-32 | single | 3 | 73.3 | 96.4 | 0.639 |
| ViT-B-32 | generic | 12 | 75.2 | 96.4 | 0.649 |
| ViT-B-32 | context | 12 | 75.8 | 93.9 | 0.638 |
| ViT-B-16 | single | 3 | 68.5 | 94.5 | 0.721 |
| ViT-B-16 | generic | 12 | 72.7 | 95.2 | **0.734** |
| ViT-B-16 | context | 12 | **78.2** | 95.8 | 0.733 |
| ViT-L-14 | single | 3 | 73.9 | **98.2** | 0.668 |
| ViT-L-14 | generic | 12 | 77.0 | **98.2** | 0.716 |
| ViT-L-14 | context | 12 | **79.4** | 97.6 | 0.720 |
| XLM-RoBERTa-base + ViT-B-32 | single | 3 | 70.3 | 93.3 | 0.601 |
| XLM-RoBERTa-base + ViT-B-32 | generic | 12 | 69.7 | 93.9 | 0.597 |
| XLM-RoBERTa-base + ViT-B-32 | context | 12 | 69.7 | 93.9 | 0.598 |
| XLM-RoBERTa-base + ViT-B-32 | TH-mixed | 6 | 77.6 | 93.9 | 0.673 |

## Other result files

| File | Content |
|---|---|
| `table1_dataset.csv` | Number of images per class (Table 1) |
| `per_class_precision_recall_f1.csv` | Per-class precision / recall / F1 |
| `table3_per_class_f1.csv` | Per-class F1 (Table 3) |
| `predictions_per_image.csv` | Per-image predictions of every model |
| `bootstrap_ci.csv` | Bootstrap 95% confidence intervals |
| `mcnemar.csv`, `mcnemar_language_controlled.csv`, `fewshot_mcnemar_per_seed.csv` | Paired significance tests |
| `fewshot_same_test_set.csv` | Zero-shot vs linear probe on the same test set (Table 6) |
| `prompt_language_controlled.csv` | Prompt-language experiment (Table 5) |
| `all_prompts.csv` | Every prompt template used |
| `cm_*.png` | Confusion matrices per backbone |
| `environment.json` | Software / hardware versions |

## Reproduce

1. Open `notebooks/clip_zeroshot_wat_lampang_luang.ipynb` in Google Colab (GPU runtime).
2. Set `DATA_DIR` (images named `CCC_KKK_II.jpg`, `CCC` = class code) and `OUT_DIR` in cell 0.2.
3. Run all cells. The final check cells (A6, B7) compare the results with the numbers reported in the paper.

## License

No license has been specified yet; all rights reserved by the authors until publication.
