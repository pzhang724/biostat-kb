From chat, 2026-06-25

Q (理解确认 + 追问): 等于 MCAR 就感觉是随便丢的、无征兆; MAR 是某种人可能容易发生什么事儿; MNAR 是不管某种人、其实跟它最后真实的值有关系 —— 理解对吗? 再提醒各自 assumption 的处理方式,以及 trial 里 SAP 通常怎么开始 justify。

A: 理解基本正确。一处细化: MAR 的"某种人"必须是用**已测/observed 变量**定义的(协变量、更早的访视值)。如果区分这类人的特征你根本没测,那它会表现成 MNAR。MCAR 是 MAR 的特例(依赖的 observed 集合为空)。所以:
- MCAR = 随便丢、无征兆(谁都不依赖)。
- MAR = 看得见的特征能解释谁更容易缺(条件在这些特征上后,缺与不缺同分布)。
- MNAR = 看得见的特征解释不了,真正驱动缺失的是那个没观测到的值本身。

各自处理 / assumption:
- MCAR: complete-case 都无偏,但浪费效率;现实少见,不作为主张依据。
- MAR: 主分析的默认假设。用 MMRM(基于似然,用上所有 observed 访视,不用显式填补)或 multiple imputation under MAR。核心是"条件在 observed 协变量+早期值上,缺失与未观测值无关"。
- MNAR: 主分析方法会带偏;用 pattern-mixture、delta-adjustment / tipping-point、reference/control-based imputation(jump-to-reference, copy-reference)等做敏感性。

SAP 怎么开始 justify(关键: 不能从数据"证明"MAR/MNAR,所以 SAP 不是去证明,而是 选一个主假设并讲清→把它做得尽量可信→再压力测试偏离):
1. 先定 estimand(E9R1)和 ICE 处理策略;真正"没有数据"的那部分才进 missing-data 处理。
2. 主分析显式声明 MAR,用 MMRM 或 MI under MAR。把既预测结局又预测脱落的强变量放进模型/填补 —— 纳入的预测变量越多越强,MAR 越站得住("条件在这些之上,缺失与未观测值无关")。
3. 设计层面的支撑(SAP 会引用): 尽量减少缺失、对停药后仍随访(retrieved dropout)、记录脱落原因、遵循 E9R1 / 2010 NRC 缺失数据报告原则。
4. 预先指定 MNAR 敏感性分析(tipping-point / delta、reference-based / control-based、pattern-mixture):若主结论在合理的 MNAR 偏离下仍成立 → robust。
5. SAP 写出的叙事大致是:"主分析假设 MAR;鉴于纳入的协变量与估计目标的 ICE 策略,此假设被认为可信;对 MNAR 的稳健性通过 tipping-point / reference-based 填补评估。"
