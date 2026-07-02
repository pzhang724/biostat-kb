From chat, 2026-06-25

Q: 能举例说明一下 missing data 里的 MNAR, MAR, MCAR 和应该知道的事儿吗

A (digest):

Missing-data mechanisms — Rubin/Little 的三分类，讲的是"为什么缺失"(缺失机制)，不是数据本身。决定哪种分析方法不带偏。

- MCAR (Missing Completely At Random，完全随机缺失): 缺失概率和任何数据都无关 —— 既不依赖观测到的，也不依赖没观测到的。例子: 离心机坏了随机丢一管样本; 患者因为搬家(与病情无关)失访; 随机抽子样本测某指标。后果: complete-case / 直接删除不带偏，只是损失效率(样本量变小)。现实中很少真成立。

- MAR (Missing At Random，随机缺失): 给定观测到的数据后，缺失概率与未观测到的值无关 —— 缺失可以依赖 observed 协变量或更早的观测值，但不直接依赖那个缺失的值本身。例子: 重症患者(基线评分高，已观测)更容易脱落; 前几次访视疼痛读数高(已观测)的人后面更容易缺访。后果: likelihood-based 方法(MMRM)和 multiple imputation 在 MAR 下有效，无需把缺失当随机删除。MMRM 在 MAR 下不用显式填补即可有效。

- MNAR (Missing Not At Random，非随机缺失): 即便在观测数据已知的条件下，缺失概率仍依赖那个没观测到的值本身。例子: 患者因为这次真的更糟(而这个更糟的值恰恰没测到)而退出; 疼痛太重去用 rescue 然后离开; 抑郁加重的人不来填量表。后果: 标准 MAR 方法带偏; 需要 pattern-mixture、delta-adjustment / tipping-point、control-based imputation(如 jump-to-reference, copy-reference)等敏感性分析。

应该知道的事儿:
1. MAR vs MNAR 在观测数据里无法被检验 —— 是不可验证的假设(因为差别就在你没观测到的值上)。所以做法是: 主分析在 MAR 下做 + 预先指定 MNAR 敏感性分析看结论稳不稳。
2. MCAR 可以部分检验(如 Little's MCAR test)，但通常不可信，也很少真成立。
3. 缺失数据 ≠ intercurrent event。E9(R1) 框架里先定 estimand 和 ICE 处理策略; 真正"没有数据"的那部分才是 missing data，用分析方法(MMRM/MI/敏感性)处理。两者会交叉(如 hypothetical 策略会主动制造缺失再填补)。
4. 默认/惯例: 主分析常假设 MAR(MMRM 或 MI)，再用 MNAR 敏感性分析(尤其是把脱落者往不利方向 delta-adjust 或 control-based)做稳健性检查。这是 FDA / 2010 NRC missing-data 报告 / ICH E9(R1) 的精神。
5. 单一填补(LOCF/WOCF/BOCF)对应的是很强(常不现实)的 MNAR/特定假设，现在多作为保守敏感性，不作主分析。

口诀: MCAR=纯随机(谁都不依赖); MAR=只依赖你看得见的; MNAR=依赖你没看见的那个值本身。
