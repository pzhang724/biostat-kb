From chat, 2026-06-19

Q: 一般是不是没什么人看 SDTM Model,都看 IG?

A: Largely yes. The **IG is the working document** practitioners (SDTM programmers, data managers, statisticians) read and build to day-to-day — it has the concrete domains, variables, examples, and assembly conventions, so it answers almost every implementation question.

You reach back to the **Model** mainly in two situations:
- **Building a custom / non-standard domain** the IG doesn't cover — then you fall back to the Model's **three general observation classes + variable-role rules** to construct it correctly.
- **Understanding the why** — the conceptual underpinning (classes, roles, naming) behind what the IG prescribes.

And the people who actually live in the Model are **CDISC standards developers / governance** (and tool/validator builders), not the typical study team.

One line: read the IG to do the work; consult the Model when the IG runs out (custom domains) or when you want the concept behind the rule.
