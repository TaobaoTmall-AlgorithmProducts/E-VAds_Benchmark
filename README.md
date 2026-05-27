# 🎬 E-VAds Benchmark

<div align="center">

**E-VAds: An E-commerce Short Videos Understanding Benchmark for MLLMs**
**(ICML 2026)**

[English](README.md) | [中文文档](README_CN.md)

[![arXiv](https://img.shields.io/badge/arXiv-2602.08355-b31b1b.svg)](https://arxiv.org/abs/2602.08355)
[![GitHub](https://img.shields.io/badge/GitHub-E--VAds__Benchmark-black?logo=github)](https://github.com/TaobaoTmall-AlgorithmProducts/E-VAds_Benchmark)
[![Dataset](https://img.shields.io/badge/🤗%20HuggingFace-Dataset-yellow)](https://huggingface.co/datasets/TaobaoTmall-AlgorithmProducts/E-VAds_Benchmark)
[![Project Page](https://img.shields.io/badge/%F0%9F%8C%90%20Project%20Page-E--VAds.github.io-blue?logo=github)](https://tennine2077.github.io/E-VAds.github.io/)
[![Model](https://img.shields.io/badge/🤗%20HuggingFace-E--VAds--R1--Qwen2.5VL-yellow)](https://huggingface.co/TaobaoTmall-AlgorithmProducts/E-VAds-R1-Qwen2.5VL)
[![Model](https://img.shields.io/badge/🤗%20HuggingFace-E--VAds--R1--Qwen3VL-yellow)](https://huggingface.co/TaobaoTmall-AlgorithmProducts/E-VAds-R1-Qwen3VL)

</div>

---

## 📖 Overview

**E-VAds** (E-commerce Video Ads Benchmark) is the first large-scale benchmark specifically designed to evaluate Multimodal Large Language Models (MLLMs) on conversion-oriented e-commerce short video understanding. Unlike general video QA tasks, e-commerce videos present unique challenges with **high-density multimodal signals**, **rapid visual changes**, and **commercial intent reasoning**.

### 🎯 Key Challenges

1. **High Multimodal Information Density**: Models must track rapid visual changes while grounding dense speech and text overlays within short time windows
2. **Conversion-Oriented Content**: Focus on immediate purchase decisions rather than general engagement
3. **Open-Ended Commercial Reasoning**: Questions about persuasion logic and consumer insight are inherently subjective and intent-driven

### 📊 Benchmark Scale

- **3,961 high-quality videos** from Taobao covering diverse product categories
- **19,785 open-ended Q&A pairs** across 5 distinct tasks
- **Two primary dimensions**: Perception and Cognition & Reasoning
- **Multi-modal density**: Significantly higher than mainstream datasets
  - Visual Dynamic Density (Vden): **60.44** (vs. 50.13 in AdsQA)
  - Audio Density (Aden): **5.08** (vs. 2.77 in ActivityNetQA)
  - Textual Density (Oden): **18.66** (vs. 5.05 in AdsQA)

## ✨ Key Features

- 🎯 **Commercial Intent Focus**: First benchmark targeting conversion-oriented e-commerce videos
- 🤖 **Multi-Agent Generation**: QA pairs created through collaborative multi-role agents (Consumer, Expert, Skeptic, Pragmatist, Creative Director)
- 📊 **Hierarchical Task Design**: Questions span from basic perception to complex commercial reasoning
- 🎥 **Dense Multi-Modal Signals**: Integrates time-aligned OCR, ASR, and visual features
- 🔬 **Evidence-Grounded Evaluation**: Strict traceability requirement linking answers to visual, audio, or textual evidence
- 📈 **E-VAds-R1 Model**: RL-based reasoning model achieving **109.2% performance gain** in commercial intent reasoning

## 🏗️ Benchmark Structure

### Task Categories

E-VAds evaluates models across **two dimensions** with **five tasks**:

#### **Dimension 1: Perception**

| Task                          | Description                                                  | Key Focus                                           |
| ----------------------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| **BP**: Basic Perception      | Identify product attributes, visual entities, and salient features | Color, shape, material, price tags, brand names     |
| **CM**: Cross-Modal Detection | Judge consistency between ASR, OCR, and visual cues          | Multi-modal alignment under noise and rapid changes |

#### **Dimension 2: Cognition & Reasoning**

| Task                          | Description                                           | Key Focus                                                 |
| ----------------------------- | ----------------------------------------------------- | --------------------------------------------------------- |
| **ML**: Marketing Logic       | Unpack persuasive structure and conversion strategies | Selling points, pain-point solutions, narrative flow      |
| **CI**: Consumer Insight      | Infer target audience and emotional appeal            | Audience profiling, tone analysis, scene-target alignment |
| **RC**: Regulatory Compliance | Detect violations of advertising regulations          | False claims, misleading statements, ethical risks        |

### Product Categories

E-VAds covers 8 major product domains:

- 👗 Apparel & Bags (15.89%)
- 💄 Beauty & Cosmetics (10.76%)
- 🧴 Personal Care (10.24%)
- 🍎 Food & Healthcare (11.64%)
- 🏠 Home & Furniture (15.27%)
- 🔌 Home Appliances (15.17%)
- 👶 Baby & Pet (12.29%)
- 📦 Others (8.76%)

## 📈 Benchmark Statistics

| Split            | Videos    | QA Pairs   | Avg. Duration | Purpose                |
| ---------------- | --------- | ---------- | ------------- | ---------------------- |
| E-VAds-Train-SFT | 376       | 1,880      | 28.4s         | Supervised fine-tuning |
| E-VAds-Train-RL  | 196       | 980        | 28.4s         | Reinforcement learning |
| E-VAds-Test      | 3,389     | 16,925     | 28.4s         | Evaluation             |
| **Total**        | **3,961** | **19,785** | **28.4s**     | -                      |

### Comparison with Other Benchmarks

| Benchmark         | QA Nums    | Anno Type       | Task Types | Vden ↑    | Aden ↑   | Oden ↑    |
| ----------------- | ---------- | --------------- | ---------- | --------- | -------- | --------- |
| VideoMME-short    | 3,000      | Manual          | MCQs       | 31.65     | 1.16     | 4.32      |
| MVBench           | 4,000      | Manual          | MCQs       | 20.69     | 2.46     | 3.45      |
| ActivityNetQA     | 8,000      | Manual          | Open       | 29.69     | 2.77     | 2.98      |
| EgoSchema         | 5,031      | Auto            | MCQs       | 25.76     | 0.00     | 4.24      |
| AdsQA             | 7,895      | Auto+Manual     | Open       | 50.13     | 0.85     | 5.05      |
| VideoAds          | 1,100      | Manual          | MCQs       | 50.72     | 1.40     | 4.02      |
| **E-VAds (Ours)** | **19,785** | **Auto+Manual** | **Open**   | **60.44** | **5.08** | **18.66** |

## 🚀 E-VAds-R1 Model

E-VAds-R1 is an RL-based reasoning model designed to handle modality-dense videos and complex commercial reasoning.

### Key Components

1. **Two-Stage Training**
   - **SFT Stage**: Align output format and inject basic e-commerce knowledge
   - **RL Stage**: Improve evidence grounding and reasoning consistency

2. **MG-GRPO (Multi-Grained Group Relative Policy Optimization)**
   - Combines strict and relaxed scoring for balanced supervision
   - Formula: `G(x) = 1/3 * [S(x) + R3(x) + R5(x)]`
   - Provides smooth guidance for exploration
   - Creates non-linear incentive for expert-level precision

3. **Evidence-Grounded Rewards**
   - **Reasoning Trace Score** (xt): Quality of thinking process
   - **Answer Score** (xa): Quality of final answer
   - **Format Constraint** (Rfmt): Structural correctness
   - Final Reward: `R = 0.8 * G(xa) + 0.2 * G(xt) + Rfmt`

### Performance

E-VAds-R1 achieves a **109.2% relative improvement** in commercial intent reasoning over strong baseline models with only a few hundred training samples.

## 🎓 Multi-Modal Information Density Framework

We propose three metrics to quantify information density:

### Visual Dynamic Density (Vden)

Measures semantic change rate using DINOv3-Base features:

```
Vden = α * (1/T) * Σ(1 - S̄i)
```

where S̄i is weighted average similarity in temporal neighborhood

### Audio Density (Aden)

Word count of ASR normalized by duration:

```
Aden = |ASR_transcript| / Duration
```

### Textual Density (Oden)

Word count of OCR normalized by duration:

```
Oden = |OCR_text| / Duration
```

## 🏗️ Directory Structure

E-VAdsBench/
├── evaluation/
│ ├── eval_qwen3vl_8b.py # Main evaluation script
│ ├── eval_qwen3vl_8b.sh # Shell script for quick execution
│ └── results/ # Output directory (auto-created)
├── videos/ # Video source files
├── annotations/ # Parquet annotation files
└── README.md


## 🚀 Quick Start

### Prerequisites

Install required packages

```bash
pip install torch transformers pandas tqdm qwen-vl-utils openai
```
### Usage

1. Data Preparation

Ensure your data is organized as follows:

- **Videos**: All `.mp4`, `.avi`, etc., files should be in a single folder (default: `../videos`).
- **Annotations**: The benchmark data (questions, answers, metadata) should be in `.parquet` format (default: `../annotations`).

2. Running Evaluation (Shell Script)

   The easiest way to run the evaluation is using the provided shell script. Edit `eval_qwen3vl_8b.sh` to configure your API keys and paths, then run:

   ```shell
   cd evaluation
   bash eval_qwen3vl_8b.sh
   ```

3. Running Manually (Python)

   You can also run the Python script directly with custom arguments:
   
   ```shell
   python eval_qwen3vl_8b.py \
       --model_name "Qwen/Qwen3-VL-8B-Instruct" \
       --video_dir "../videos" \
       --annotation_dir "../annotations" \
       --parquet_name "EVAds_TEST.parquet" \
       --output_dir "./results" \
       --use_llm_judge \
       --judge_api_key "YOUR_API_KEY" \
       --judge_base_url "YOUR_BASE_URL"
   ```

### Arguments

| Argument           | Default              | Description                                                  |
| :----------------- | :------------------- | :----------------------------------------------------------- |
| `--video_dir`      | `../videos`          | Path to the directory containing video files.                |
| `--annotation_dir` | `../annotations`     | Path to the directory containing Parquet annotation files.   |
| `--parquet_name`   | `EVAds_TEST.parquet` | Specific annotation file to evaluate. If not set, loads all parquet files in the dir. |
| `--output_dir`     | `./results`          | Directory where results (`.csv`, `.json`) will be saved.     |
| `--model_name`     | `Qwen/Qwen3-VL...`   | HuggingFace model ID or local path to the Qwen-VL model.     |
| `--use_llm_judge`  | `False`              | Flag to enable automated scoring using an LLM (e.g., GPT-4 or Qwen-Plus). |
| `--judge_api_key`  | `""`                 | API Key for the Judge LLM.                                   |
| `--judge_base_url` | `""`                 | Base URL for the Judge LLM (compatible with OpenAI SDK).     |

## ⚖️ Evaluation Metrics

The script employs a sophisticated prompt to evaluate the model's output based on **Question**, **Reference Answer**, **Metadata (OCR/ASR)**, and **Clues**.

The Judge assigns a score from **0 to 1.0**, which is mapped to three metrics:

1. **Score R5 (Fine-grained)**: 5-level scoring.
   - `1.0`: **Perfect Match**. Accurate, covers key points, aligns with evidence, professional insight.
   - `0.75`: **Accurate but Generic**. Correct core answer but lacks depth or specific commercial logic.
   - `0.5`: **Partially Correct**. Captures ~50% of key points or missing background facts.
   - `0.25`: **Logical Break**. Hallucination or right evidence/wrong conclusion.
   - `0.0`: **Incorrect**. Contradicts facts or fails to answer.
2. **Score R3 (Relaxed)**: 3-level scoring for broader acceptance.
   - Mapped from R5: `1.0 -> 1.0`, `0.75 -> 0.5`, `0.25 -> 0`.
3. **Score R2 (Strict)**: Binary scoring.
   - Only `1.0` counts as correct.

## 📄 Output

The script generates the following files in the `output_dir`:

- **`final_results.csv`**: Contains detailed rows for every sample, including the question, reference answer, model prediction, and Judge scores.
- **`final_results.json`**: JSON format of the results.
- **`failed_videos.txt`**: A list of video IDs that could not be found or processed.
- **`results_checkpoint_X.csv`**: Intermediate results saved every 10 samples to prevent data loss.

### Console Summary

At the end of execution, the script prints a summary:

```text
==================================================
Evaluation Summary
==================================================
Total samples: 1000
Successfully processed: 998
Failed: 2

Average Score (R5): 0.785
Average Score (R3): 0.650
Average Score (R2): 0.450
```

---

## 📜 Citation

If you find E-VAds useful for your research, please cite our paper:

```bibtex
@misc{liu2026evadsecommerceshortvideos,
      title={E-VAds: An E-commerce Short Videos Understanding Benchmark for MLLMs}, 
      author={Xianjie Liu and Yiman Hu and Liang Wu and Ping Hu and Yixiong Zou and Jian Xu and Bo Zheng},
      year={2026},
      eprint={2602.08355},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2602.08355}, 
}
```

---

<div align="center">

**⭐ If you find E-VAds useful for your research, please star this repository! ⭐**

</div>
