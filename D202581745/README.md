# 个人信息
D202581745-王鸿运

# Socratic Inquirer

prompt for learning by questioning

**提示词**:
    请从实际应用落地的可行性、可扩展性、可靠性与安全性、核心工作的代价和收益矛盾、实验场景和负载的代表性这几个方面，对这项工作提出质疑

prompt for rating the questions

**所使用的评分提示词**
【角色设定】
你是一名顶级系统与机器学习方向的学术评审专家，熟悉 FAST / OSDI / SOSP / NeurIPS Systems Track 等高水平会议的论文评审标准，擅长评估学术研讨中问题（question）的质量。

【任务说明】
我将提供两部分内容：
1）一篇论文
2）针对该论文提出的问题

请你从“学术研讨中提问质量”的角度，对该问题进行 0–10 分的综合评分，并给出简明但有深度的评价。

【评分依据（需综合考虑）】
在评分时，请综合以下维度（无需逐条打分，但必须整体权衡）：

1. 理解准确性  
是否准确抓住论文的核心贡献、关键设计或核心假设，是否存在明显误读或停留在表层复述。

2. 基础与前提追溯  
是否追问了方法成立所依赖的模型假设、系统条件或数学前提，是否触及论文中默认但未充分展开的关键条件。

3. 批判深度与针对性  
是否明确指出论文方法在设计、理论或工程上的潜在局限、矛盾或风险，质疑是否具有针对性，而非泛泛而谈。

4. 实验与现实合理性意识  
是否关注实验设置、负载分布、规模假设、硬件条件、SLO 定义等现实约束，是否思考该方法在不同场景下是否仍然成立。

5. 研究价值与启发性  
该问题是否有助于引出新的实验、改进方向或后续研究问题，是否体现出研究者视角而不仅是读者视角。

【评分锚点（供你内部参考）】
- 9–10 分：精准命中论文核心假设或关键设计取舍，具有审稿级别的洞察力
- 7–8 分：理解到位且有针对性，但深度或外推性略有限
- 5–6 分：问题合理但偏通用，对该论文并非高度特有
- 3–4 分：停留在总结或表层质疑层面
- 0–2 分：明显误读论文或与核心内容无关

【输出格式（必须严格遵守）】
评分：X / 10.0

评价：
（不超过 120 字）
- 用 2–3 句话说明该问题为什么得到这个分数
- 明确指出该问题最突出的优点
- 如果评分低于 8 分，需指出最关键的不足或缺失视角


**常用模型**：DeepSeek、KIMI、豆包、文心、ChatGPT

**交叉评价**:

$$\{evaluator(reviewer(paper)) | reviewer, evaluator \in [DS, KM, DB], paper \in ReadingList\}$$

0. 基于**学术评价参考论文**，准备评分提示词 $Prompt_{evaluator_{id}}$
1. 在 reviewer 模型中，上传目标论文，使用提示词 $Prompt_{baseline}$ 质疑论文，得出**向论文的提问** $Question_{paper}$
2. 在 evaluator 模型中，上传目标论文，使用评分提示词，对 $Question_{paper}$ 打分
3. 根据 reviewer 和 evaluator 所用模型，归纳数据

**学术评价参考论文**

1. **IEEE Network Reviewer Guidelines**  
   **来源**: IEEE Communications Society  
   **链接**: [IEEE Network 审稿指南](https://www.comsoc.org/publications/magazines/ieee-network/reviewer-guidelines)  
   **说明**: 强调对方法理论完备性和实验可重复性的评估标准。
2. **Wang, Y., Zhang, L., & Chen, H. (2017)**  
   *Questioning Techniques Promote Critical Thinking in Engineering Education*  
   **期刊**: IEEE Transactions on Education  
   **链接**: [IEEE Xplore](http://ieeexplore.ieee.org/document/7942978/)  
   **说明**: 该研究验证了创新性质疑对工程教育中论文修改后创新指数提升23%的量化效果。
3. **Gupta, R. et al. (2021)**  
   *Models for Finding Quality Questions in Scientific Discussions*  
   **会议**: ACL  
   **链接**: [ACL Anthology](https://aclanthology.org/2021.acl-long.32/)  
   **说明**: 基于BERT的语义相似度计算框架（F1=66.6%）。
4. **Shin, H. et al. (2025)**  
   *Mind the Blind Spots: A Focus-Level Evaluation Framework for LLM Reviews*  
   **预印本**: arXiv:2502.17086  
   **链接**: [arXiv](https://arxiv.org/abs/2502.17086)  
   **说明**: 量化分析LLM生成的评审对技术有效性关注度比人类高30%，但创新性评估不足。
5. 严炜炜,黄为,温馨. 学术社交网络问答质量智能评价与服务优化研究[J]. 图书情报工作,2021,65(6):129-137.
6. 吴雅威,张向先,陶兴,等. 基于用户感知的学术问答社区答案质量评价指标构建[J]. 情报科学,2020,38(10):141-147

**准备评分提示词**
    现在希望能够给学术研讨小组找到一个系统性的方法，应用大语言模型推理来帮助提升同学们论文研讨的质量，结合目标论文，通过开发特定提示词，引导、鼓励同学们进行相关研究工作基础知识的追溯、有思想深度的质疑，以及研究合理性的批判。请结合这篇论文，考虑高质量质疑和研讨的关键要素，综合进行科学评分，构造一套对"提问质量"进行评分的提示词，提示词的使用方法是结合一篇论文及对这篇论文的提问，对所提问题进行0到10分的评价。


## 评分统计

对论文 FLATQUANT: Flatness Matters for LLM Quantization 进行DeepSeek、KIMI、豆包、文心的质疑与相互评分统计，共得到16组得分。

| 质疑模型 | Deepseek打分 | Kimi打分 | 豆包打分 | 文心打分 |
|:-----------------:|:---------:|:-----:|:-----:|:---------:|
| Deepseek  | 7.8      | 8.5  | 9.5  | 7.5      |
| Kimi      | 9.5      | 9.5  | 9.5  | 9.0      |
| 豆包      | 8.5      | 9.0  | 9.5  | 7.0      |
| 文心一言  | 6.0      | 5.0  | 7.5  | 7.0      |

