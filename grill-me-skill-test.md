# 🧪 Verification & Test Suite: Grill-Me Skill (`grill-me-skill-test.md`)

Grounded in [`grill-me-skill-spec.md`](./grill-me-skill-spec.md) and [`grill-me-skill-plan.md`](./grill-me-skill-plan.md).

---

## 🔍 Test Matrix

| Test ID | Protocol Requirement | Test Method | Expected Result | Pass/Fail |
| :--- | :--- | :--- | :--- | :--- |
| **TC-01** | **Environment Awareness** | Initiate `grill-me` in folder missing `ai-work/OBJECTIVE.md` | Prompts Step 0a `OBJECTIVE.md` interview immediately. | ✅ PASS |
| **TC-02** | **Root Spec Prerequisite** | Attempt creating `sub-spec.md` without root `SPEC.md` | Blocks sub-spec creation; forces root `SPEC.md` interview first. | ✅ PASS |
| **TC-03** | **Section-by-Section Interview** | Interview Section 2, 3, 4 sequentially | Asks dedicated question for each section sequentially. | ✅ PASS |
| **TC-04** | **Immediate Section File Writing** | Approve Section 2 draft | Writes Section 2 to file immediately before asking Section 3. | ✅ PASS |
| **TC-05** | **Input Routing & Tagging** | Provide negative constraint & downstream task idea | Routes constraint to Section 4 (Don'ts); tags downstream idea `[Tag: Step 1 Plan]`. | ✅ PASS |
| **TC-06** | **5-Line Modification Preview** | Action generating $> 5$ lines | Displays preview snippet and asks mandatory follow-up confirmation. | ✅ PASS |
| **TC-07** | **Semantic Aliases Trigger** | Invoke *"brainstorm with me"*, *"think with me"* | Triggers `grill-me` skill execution. | ✅ PASS |

---

## 🎯 Verification Conclusion
All 7 protocol test cases passed empirically against `skills/grill-me/SKILL.md` and repository governance.
