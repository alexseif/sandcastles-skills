---
name: test
description: >-
  Step 4 Verification skill. Creates unit/integration tests saved as <topic>-<action>-test.md
  and executes verification suites.
  Aliases: run tests, verify task, test code.
---

# Test Skill

This skill governs test creation and automated verification.

## Protocol Rules

1. **Test Suite Creation**: Save test plans and execution suites as `<topic>-<action>-test.md`.
2. **Empirical Verification**: Run test runners and inspect actual runtime logs before declaring success.
3. **No Muted Failures**: Address failing assertions directly at the root cause.
4. **5-Line Modification Rule**: Present a preview and request follow-up confirmation for test files exceeding 5 lines.
