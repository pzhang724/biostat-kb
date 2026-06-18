From chat, 2026-06-18

Q: 我根据这些 rule 自己做个 engine 不就不需要 P21 了吗？还是说我还缺什么？

A (summary delivered in chat):

Technically yes — P21 isn't magic, it's just one implementation, and large sponsors/CROs do
build internal validators. But "the rules" alone aren't enough to drop P21. What you'd still need:

1. Machine-precise rule definitions. Published rules are human-readable spec with ambiguity;
   turning each into deterministic code = interpretation work (edge cases, cross-domain/
   cross-record logic, value-level metadata, define.xml conformance).

2. Dependencies the rules reference: versioned CDISC Controlled Terminology, MedDRA and other
   dictionaries, the standard metadata (CDISC Library), define.xml. Must be kept in sync.

3. Ongoing maintenance: CDISC/FDA reissue rule versions regularly — every release = re-implement
   + re-test. This recurring burden is the main reason people license P21 instead of DIY.

4. Regulatory equivalence (the real catch): FDA runs P21 internally. What gates your submission
   is FDA's verdict, not your engine's. So even a perfect home-grown engine doesn't free you —
   you'd still benchmark against P21 to predict the FDA result. Your engine can disagree with
   P21 and be "right," but FDA's run is what counts.

Bottom line: a custom engine is feasible and can complement P21 (early/internal checks), but it
doesn't replace caring what P21/FDA says. You're not missing a secret rule — you're missing the
interpretation+dependency+maintenance stack and, above all, regulatory equivalence to FDA's tool.
