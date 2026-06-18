From chat, 2026-06-18

Q: 解释这句: "The MTD is defined as the highest dose of trial drug where the posterior probability of the true DLT rate in the target interval [0.16-0.33] of the MTD is above 0.50 with less than 25% risk of the true DLT rate being above 33%."

A: 这是用贝叶斯模型 (典型是 BLRM 贝叶斯逻辑回归模型) 定义 MTD 的写法，配 EWOC 的超量控制。拆开:

- true DLT rate (真实 DLT 发生率): 某剂量下病人发生 DLT 的真实概率 (未知)，模型对它有后验分布。
- target interval [0.16-0.33] (目标区间): 把 DLT 率分三段——偏低 [0, 0.16)、目标 [0.16, 0.33]、偏高 (0.33, 1]。目标段 = "既有效又可接受毒性"的理想范围。
- "posterior probability ... in the target interval ... above 0.50": 对一个候选剂量，算 P(真实 DLT 率 ∈ [0.16,0.33] | 现有数据)，要 > 0.50——即"该剂量的真实毒性率更可能就在目标窗里"。
- "less than 25% risk of ... above 33%": EWOC 超量控制约束——P(真实 DLT 率 > 0.33 | 数据) < 0.25，即落入"过毒"区的后验概率不能太大 (这就是 α=0.25 的 feasibility bound)。
- "highest dose where ...": 在同时满足上面两条的所有剂量里，取最高的那个作为 MTD。

合起来: MTD = 满足 [P(DLT率∈[0.16,0.33])>0.5 且 P(DLT率>0.33)<0.25] 的最高剂量。第一条保证"落在目标毒性窗"，第二条保证"过量风险够低"。
