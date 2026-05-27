# 🎬 E-VAds Benchmark

<div align="center">

**E-VAds: 面向多模态大模型的电商短视频理解基准**
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

## 📖 项目概述

**E-VAds** (E-commerce Video Ads Benchmark，电商视频广告基准) 是首个专门设计用于评估多模态大语言模型（MLLMs）在转化导向型电商短视频理解能力的大规模基准测试。与通用视频问答任务不同，电商视频呈现出独特的挑战：**高密度多模态信号**、**快速视觉变化**和**商业意图推理**。

### 🎯 核心挑战

1. **高多模态信息密度**：模型必须在短时间窗口内追踪快速的视觉变化，同时定位密集的语音和文字线索
2. **转化导向内容**：聚焦于促成即时购买决策，而非通用的内容互动
3. **开放式商业推理**：关于说服逻辑和消费者洞察的问题本质上是主观的、意图驱动的

### 📊 基准规模

- **3,961个高质量视频**，来自淘宝，覆盖多样化产品类别
- **19,785个开放式问答对**，跨越5个不同任务
- **两大核心维度**：感知（Perception）和认知推理（Cognition & Reasoning）
- **多模态密度**：显著高于主流数据集
  - 视觉动态密度 (Vden): 60.44
  - 音频密度 (Aden): 5.08
  - 文本密度 (Oden): 18.66

## ✨ 核心特性

- 🎯 **商业意图聚焦**：首个针对转化导向型电商视频的基准测试
- 🤖 **多智能体生成**：通过多角色协作智能体（消费者、专家、怀疑者、实用主义者、创意总监）创建问答对
- 📊 **分层任务设计**：问题难度从基础感知到复杂商业推理逐级递增
- 🎥 **密集多模态信号**：整合时间对齐的OCR文本、ASR语音和视觉特征
- 🔬 **证据驱动评估**：严格的可追溯性要求，将答案与视觉、音频或文本证据关联
- 📈 **E-VAds-R1模型**：基于强化学习的推理模型，在商业意图推理上实现了**109.2%的性能提升**

## 🏗️ 基准结构

### 任务分类

E-VAds 通过**两大维度**评估模型，包含**五个任务**：

#### **维度1：感知能力**

| 任务 | 描述 | 重点关注 |
|------|------|----------|
| **BP**: 基础感知 | 识别产品属性、视觉实体和显著特征 | 颜色、形状、材质、价格标签、品牌名称 |
| **CM**: 跨模态检测 | 判断ASR、OCR和视觉线索之间的一致性 | 噪声环境下的多模态对齐和快速变化 |

#### **维度2：认知与推理**

| 任务 | 描述 | 重点关注 |
|------|------|----------|
| **ML**: 营销逻辑 | 解析说服结构和转化策略 | 卖点提炼、痛点解决方案、叙事流程 |
| **CI**: 消费者洞察 | 推断目标受众和情感共鸣 | 受众画像、语调分析、场景与目标对齐 |
| **RC**: 合规性 | 检测违反广告法规的行为 | 虚假声明、误导性陈述、伦理风险 |

### 产品类别

E-VAds 覆盖8个主要产品领域：

- 👗 服装包包 (15.89%)
- 💄 美妆 (10.76%)
- 🧴 个护 (10.24%)
- 🍎 食品保健 (11.64%)
- 🏠 家居家具 (15.27%)
- 🔌 家电 (15.17%)
- 👶 母婴宠物 (12.29%)
- 📦 其他 (8.76%)

## 📈 基准统计

| 数据集划分 | 视频数 | 问答对数 | 平均时长 | 用途 |
|-----------|--------|----------|----------|------|
| E-VAds-Train-SFT | 376 | 1,880 | 28.4秒 | 监督微调 |
| E-VAds-Train-RL | 196 | 980 | 28.4秒 | 强化学习 |
| E-VAds-Test | 3,389 | 16,925 | 28.4秒 | 评估测试 |
| **总计** | **3,961** | **19,785** | **28.4秒** | - |

### 与其他基准的对比

| 基准测试 | 问答数 | 标注类型 | 任务类型 | Vden ↑ | Aden ↑ | Oden ↑ |
|---------|--------|----------|----------|--------|--------|--------|
| VideoMME-short | 3,000 | 人工 | 选择题 | 31.65 | 1.16 | 4.32 |
| MVBench | 4,000 | 人工 | 选择题 | 20.69 | 2.46 | 3.45 |
| ActivityNetQA | 8,000 | 人工 | 开放式 | 29.69 | 2.77 | 2.98 |
| EgoSchema | 5,031 | 自动 | 选择题 | 25.76 | 0.00 | 4.24 |
| AdsQA | 7,895 | 自动+人工 | 开放式 | 50.13 | 0.85 | 5.05 |
| VideoAds | 1,100 | 人工 | 选择题 | 50.72 | 1.40 | 4.02 |
| **E-VAds (本文)** | **19,785** | **自动+人工** | **开放式** | **60.44** | **5.08** | **18.66** |

## 🚀 E-VAds-R1 模型

E-VAds-R1 是一个基于强化学习的推理模型，专为处理模态密集型视频和复杂商业推理而设计。

### 核心组件

1. **两阶段训练**
   - **SFT阶段**：对齐输出格式并注入基础电商知识
   - **RL阶段**：改进证据定位和推理一致性

2. **MG-GRPO（多粒度组相对策略优化）**
   - 结合严格和宽松评分以实现平衡监督
   - 公式：`G(x) = 1/3 * [S(x) + R3(x) + R5(x)]`
   - 为探索提供平滑指导
   - 为专家级精度创建非线性激励

3. **证据驱动奖励**
   - **推理轨迹得分** (xt)：思考过程的质量
   - **答案得分** (xa)：最终答案的质量
   - **格式约束** (Rfmt)：结构正确性
   - 最终奖励：`R = 0.8 * G(xa) + 0.2 * G(xt) + Rfmt`

### 性能表现

E-VAds-R1 仅用几百个训练样本，就在商业意图推理上相比强基线模型实现了**109.2%的相对提升**。

## 🎓 多模态信息密度框架

我们提出三个指标来量化信息密度：

### 视觉动态密度 (Vden)

使用DINOv3-Base特征测量语义变化率：
```
Vden = α * (1/T) * Σ(1 - S̄i)
```
其中 S̄i 是时间邻域内的加权平均相似度

### 音频密度 (Aden)

ASR词数按时长归一化：
```
Aden = |ASR转录文本| / 视频时长
```

### 文本密度 (Oden)

OCR词数按时长归一化：
```
Oden = |OCR文本| / 视频时长
```

## 📂 项目结构

```
E-VAdsBench/
├── evaluation/
│   ├── eval_qwen3vl_8b.py    # 主评测脚本
│   ├── eval_qwen3vl_8b.sh    # 快速执行的 Shell 脚本
│   └── results/              # 输出目录 (自动创建)
├── videos/                   # 视频源文件
├── annotations/              # Parquet 格式标注文件
└── README.md
```

## 🚀 快速开始

### 环境准备

安装所需的依赖包：

```bash
pip install torch transformers pandas tqdm qwen-vl-utils openai
```

### 使用方法

1. **数据准备**

   确保您的数据按以下方式组织：

   - **Videos**: 所有 `.mp4`, `.avi` 等视频文件应放在同一个文件夹中（默认路径：`../videos`）。
   - **Annotations**: 基准测试数据（问题、答案、元数据）应为 `.parquet` 格式（默认路径：`../annotations`）。

2. **运行评测 (Shell 脚本)**

   运行评测最简单的方法是使用提供的 Shell 脚本。编辑 `eval_qwen3vl_8b.sh` 配置您的 API 密钥和路径，然后运行：

   ```shell
   cd evaluation
   bash eval_qwen3vl_8b.sh
   ```

3. **手动运行 (Python)**

   您也可以直接使用 Python 脚本运行，并自定义参数：

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

### 参数说明

| 参数               | 默认值               | 描述                                                         |
| :----------------- | :------------------- | :----------------------------------------------------------- |
| `--video_dir`      | `../videos`          | 包含视频文件的目录路径。                                     |
| `--annotation_dir` | `../annotations`     | 包含 Parquet 标注文件的目录路径。                            |
| `--parquet_name`   | `EVAds_TEST.parquet` | 指定要评估的 Parquet 文件名。如果未设置，则加载目录中的所有 parquet 文件。 |
| `--output_dir`     | `./results`          | 结果（`.csv`, `.json`）保存的目录。                          |
| `--model_name`     | `Qwen/Qwen3-VL...`   | HuggingFace 模型 ID 或 Qwen-VL 模型的本地路径。              |
| `--use_llm_judge`  | `False`              | 启用使用 LLM（如 GPT-4 或 Qwen-Plus）进行自动评分的标志。    |
| `--judge_api_key`  | `""`                 | Judge LLM 的 API 密钥。                                      |
| `--judge_base_url` | `""`                 | Judge LLM 的 Base URL（兼容 OpenAI SDK）。                   |

## ⚖️ 评估指标

该脚本使用精心设计的提示词（Prompt），基于 **问题**、**参考答案**、**元数据 (OCR/ASR)** 和 **线索** 对模型的输出进行评估。

Judge（裁判模型）会给出一个 **0 到 1.0** 的分数，该分数会被映射到三个指标中：

1. **R5 分数 (细粒度)**：5 级评分标准。
   - `1.0`: **完美匹配 (Perfect Match)**。准确，涵盖关键点，与证据一致，具有专业洞察力。
   - `0.75`: **准确但笼统 (Accurate but Generic)**。核心答案正确，但缺乏深度或具体的商业逻辑。
   - `0.5`: **部分正确 (Partially Correct)**。捕捉到约 50% 的关键点，或缺少背景事实。
   - `0.25`: **逻辑断裂 (Logical Break)**。出现幻觉，或者引用的证据正确但结论错误。
   - `0.0`: **错误 (Incorrect)**。与事实相悖或未能回答问题。
2. **R3 分数 (宽松)**：3 级评分标准，用于更广泛的接受度。
   - 从 R5 映射而来：`1.0 -> 1.0`, `0.75 -> 0.5`, `0.25 -> 0`。
3. **R2 分数 (严格)**：二元评分标准。
   - 只有 `1.0` 才算正确。

## 📄 输出内容 (Output)

脚本将在 `output_dir` 目录下生成以下文件：

- **`final_results.csv`**: 包含每个样本的详细信息，包括问题、参考答案、模型预测结果和 Judge 评分。
- **`final_results.json`**: 结果的 JSON 格式文件。
- **`failed_videos.txt`**: 无法找到或处理失败的视频 ID 列表。
- **`results_checkpoint_X.csv`**: 每处理 10 个样本保存一次的中间结果，防止数据丢失。

### 控制台摘要

在执行结束时，脚本会打印如下摘要：

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

## 📜 引用

如果 E-VAds 对您的研究有帮助，请引用我们的论文：

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

**⭐ 如果 E-VAds 对您的研究有帮助，请给我们一个 Star！⭐**

</div>