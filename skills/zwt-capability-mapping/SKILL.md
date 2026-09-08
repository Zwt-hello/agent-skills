---
name: zwt-capability-mapping
description: "Choose capability owners and supported implementation seams for framework-facing changes, cross-subsystem work, migrations, or compatibility decisions. Use a fast path for one established capability; skip unrelated mechanical edits."
---

# Capability Mapping

Choose one authoritative owner and a sustainable implementation seam. Preserve valid capabilities and real compatibility obligations; do not preserve historical representations by default. Keep the decision proportional to the task and proceed within the user's authorized scope.

## Choose the Smallest Relevant Path

- **Routine edit:** If content, values, or isolated code follow an established pattern without changing ownership or compatibility, proceed normally. Do not create a research phase or mapping report.
- **Focused framework change:** For one framework/library/SDK-owned capability with a locally identifiable owner and supported seam, use the fast path below.
- **Broader decision:** Build a compact map when work spans subsystems, coordinates multiple capabilities, changes state/lifecycle/protocol ownership or contracts, deliberately replaces an architecture, or risks duplicated infrastructure. Use it also when ownership remains unclear or a new abstraction or dependency may be needed.
- **Compatibility decision:** When legacy representations, stored data, external contracts, or mixed-version deployment may be affected, read [Compatibility and Breaking Evolution](references/compatibility.md). Focused compatibility work needs only that decision and its relevant implementation checks. Replacing internal code alone does not require release-status research.

Reuse evidence from repository guidance or another relevant skill. Maintain one decision record; do not repeat discovery when paths overlap.

## Focused Framework Fast Path

1. Inspect the affected code, configuration, tests, and an analogous repository flow. Confirm the installed package/version and who owns the behavior, state, and lifecycle.
2. Verify the supported native or extension seam using installed types/source and version-compatible first-party documentation when the API choice or deprecation status matters. Use Context7 as a retrieval aid when useful; do not treat model memory or a different-version example as sufficient evidence.
3. Apply the shared implementation preferences below. Stop discovery once the owner, supported seam, and version fit are clear, then implement and verify the affected behavior.

If evidence reveals a contract change, unclear ownership, or a compatibility obligation, expand only that part of the decision using the broader map or compatibility reference. Do not restart the investigation.

## Compact Map for Broader Work

Record only facts that can change the implementation:

- Required behavior and change intent: extend/repair, or replace/migrate.
- Affected entry points, subsystem boundaries, and existing supported implementations.
- Relevant framework/library/SDK and installed version; mark these not applicable when project or domain code owns the capability.
- Native capability or official extension point, backed by installed code and first-party documentation where needed.
- The authoritative owner of each relevant state and lifecycle, the chosen seam, and compatibility obligations only when applicable.

Search task-adjacent code, manifests, lockfiles, configuration, tests, and shared utilities. Consult history or broader documentation only when it resolves a material uncertainty. Reconcile current docs with the installed version and migration notes. Stop when the evidence supports a decision; keep the map internal unless a short explanation would help the user or an artifact was requested.

## Shared Implementation Preferences

Choose the first sustainable option that satisfies the required behavior, explicit architecture intent, supported lifecycle, and maintenance constraints:

1. Existing supported repository solution.
2. Framework-native capability.
3. Official extension or composition API, including its required official adapter/plugin package.
4. Thin project wrapper.
5. Custom implementation.
6. An unrelated or third-party new dependency.

Existing code does not outrank correctness or an explicitly requested replacement. For a deliberate migration or architecture change, treat the current implementation as baseline evidence and compare it with the strongest supported target seam; do not settle for a local workaround merely because it still works. Native-first does not require forcing an API that cannot meet the requirement.

Keep framework-owned state and lifecycle with the framework. A wrapper may translate project names, defaults, types, or policy; it must not mirror the dependency's API, state, or control flow. Re-check ownership if a new store, registry, router, cache, event bus, parser, or synchronization layer shadows an existing capability. Use custom code or an unrelated dependency only for a concrete gap that higher-ranked options cannot reasonably fill.

Uncertainty alone does not justify a fallback, shadow implementation, dual path, or local state copy. Recovery needs an explicit requirement, an existing contract, or a reproducible failure. An explicit error state is ordinary failure handling; a second success path or hidden substitute is a fallback. Prefer the existing owner's error, retry, or recovery seam and make failures observable.

When compatibility applies, use the reference's preserve/remove decision and verification once. With no obligation, replace the affected old path and remove its supporting obsolete code, types, tests, fixtures, and documentation. With an obligation, prefer the official migration mechanism and keep transitional behavior observable, tested, bounded, and removable.

## Implement and Verify Proportionally

Implement after resolving the relevant decision; do not introduce a technical approval checkpoint. Ask only when an unresolved user decision would materially change behavior, scope, or a real compatibility obligation. Do not expand a focused fix into an unrequested migration, or reduce an explicit replacement request to a compatibility patch.

Use existing test seams and the smallest checks that can falsify the implementation decision. Test project-owned behavior at the framework boundary, not framework internals. Add affected integration paths, transitions, failure cases, and compatibility checks when changed contracts require them. If suitable coverage is missing, add a focused seam rather than a general harness or exhaustive state matrix.

Confirm that valid capabilities remain supported or are intentionally changed, state and lifecycle retain one owner, the chosen API fits the installed version without newly adopting deprecated behavior, and no unnecessary parallel system was added. Stop after relevant checks pass unless new evidence warrants more investigation. Limit cleanup to the affected capability and briefly explain any material custom implementation or new dependency.
