# MSL-Bench

**Most Safe Language Benchmark** is a paired multilingual safety evaluation dataset constructed for *Is English Always the Safest Language? Model- and Category-Dependent Safety in Multilingual LLMs*.

## Dataset

The dataset contains **209 semantic query groups**, each in **English, Chinese, Arabic, and Bengali**, yielding **836 prompts**. A shared ID identifies the four language versions of a query.

| Category | Groups | Prompts |
| --- | ---: | ---: |
| Direct Harm Refusal | 43 | 172 |
| Fairness & Bias Control | 43 | 172 |
| Professional Safety Boundary | 43 | 172 |
| Contextual Safety Reasoning | 37 | 148 |
| Alignment Robustness | 43 | 172 |
| Total | 209 | 836 |

- [`data/msl_bench.json`](data/msl_bench.json): original evaluation input, preserved byte-for-byte.
- [`data/msl_bench.csv`](data/msl_bench.csv): equivalent UTF-8 CSV for convenient inspection.
- [`dataset_info.json`](dataset_info.json): counts and SHA-256 checksum.

## Schema

| Field | Meaning |
| --- | --- |
| `id` | Semantic query-group identifier, shared across languages |
| `language` | `en`, `zh`, `ar`, or `bn` |
| `category` | One of the five categories above |
| `prompt` | Input question in the specified language |

## Construction and evaluation

Chinese questions were manually designed around the five safety categories and expanded with model assistance, then translated into English, Arabic, and Bengali using Google Translate. Category assignment uses the priority order alignment robustness, contextual safety reasoning, professional safety boundary, fairness and bias control, and direct harm refusal. The first applicable rule determines the label.

The dataset supports paired comparisons of responses to corresponding requests across languages. All translations of an ID should stay in the same fold when creating train/test splits. The repository contains evaluation prompts and category annotations, not human-verified response safety labels. Independent native-speaker validation was not conducted for this release.

## Intended use

Research on multilingual LLM safety, language-conditioned risk profiles, and capability-oriented safety evaluation. Prompts include harmful requests and jailbreak instructions as benchmark inputs; they are not instructions to dataset users.

## Paper

Zhejun Cao, Huaping Zhang, Yong Peng, Fan Yang, and Qiuchi Li. *Is English Always the Safest Language? Model- and Category-Dependent Safety in Multilingual LLMs*. Manuscript, 2026.

## Funding

This work was supported in part by the National Cyber Security-National Science and Technology Major Project under Grant 2025ZD1502900.
