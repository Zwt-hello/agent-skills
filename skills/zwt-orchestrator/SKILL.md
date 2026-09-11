---
name: zwt-orchestrator
description: "Coordinate substantial development with deliberate model cost, bounded subagent ownership, and evidence-backed integration. Use when parallel work materially helps; keep trivial or tightly coupled work local."
---

# ZWT Orchestrator

The current lead model remains accountable for the complete result. Keep architecture and ambiguous cross-cutting decisions with the lead; delegate useful independent work without changing the lead's model identity.

- Use the fewest workers that materially improve speed, quality, or context isolation. Favor bounded exploration, implementation, debugging, review, and test analysis; sequence dependent work and overlapping writes.
- Choose worker models and reasoning effort from the current host's available options. Prefer a faster, lower-cost capable worker for clear, routine work; use deeper reasoning for ambiguous logic or critical review. Do not hard-code model generations or role names. Set worker options deliberately, inherit only intentionally, and respect the tool's context/fork constraints.
- Give each worker its scope, necessary context, owned files, dependencies, acceptance criteria, required verification, and concise return format. Require changed-file references, findings or results with evidence, and unresolved blockers rather than raw logs.
- Assign disjoint write ownership before parallel implementation. Resolve shared contracts first and keep integration under the lead's control.
- Wait for required results and inspect the actual changes. Correct, steer, or reassign deficient work; a worker's completion message alone is not proof that the integrated task is complete.
- Run checks appropriate to the integrated change and finish once they pass. Expand verification only for new failures, changed contracts, or unresolved concerns; do not require full end-to-end testing for every task.
- Report the integrated outcome, meaningful verification, and remaining limitations. Delegation does not transfer responsibility away from the lead.
