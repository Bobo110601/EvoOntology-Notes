# EvoOntology 中文综述笔记

对论文 **EvoOntology: A Self-Evolving Ontology Layer for Data Agents**（[arXiv:2609.15779](https://arxiv.org/abs/2609.15779)，中国人民大学 ruc-datalab）的深度中文综述笔记。

## 内容

- **方法论**：三层本体架构 `L_t = (S_t, Γ_t, R_t)`、Builder 智能体的证据锚定初始化、进化闭环的四步（诊断 / 归因 / 补丁 / 门控）
- **实验数据**：三个 benchmark × 六个 LLM 骨干的全部结果，并对论文所有"平均增益"做了逐骨干独立重算
- **批判性评价**：扎实之处、弱点与风险、改进方向
- **论文 vs 开源代码交叉核对**：论文表述与 `ruc-datalab/EvoOntology` 实现逐条比对，附文件名与行号

## 文件

- `EvoOntology-中文综述笔记.md` — 主笔记（384 行 / 27.5K 字符）

## 笔记要点摘录

> **门控机制对验证集的依赖被完全忽略。** 论文公式 (2) 的配对门控假设存在一个能代表部署分布的验证集；生产环境的 workload 漂移会让门控退化为对验证集的过拟合 —— 这是该范式最脆弱的环节，而论文对此零讨论。

> **公式 (2) 的 margin τ 在开源实现中不存在。** `evoontology/evaluation/evaluation.py:34` 实际是 `candidate_avg > parent_avg`（严格大于），全仓库检索 `margin` / `tau` 零命中。

> **成本分析比性能提升更有说服力。** 轮数从 14.6 降到 8.4、总 token 降约 20%，同时 Trajectory-Wise 从 69.5 升到 89.5。

## 免责声明

本笔记为个人学习整理，包含独立核算结果与主观判断，不代表原论文作者观点。论文版权归原作者所有。
