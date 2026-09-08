# Compatibility and Breaking Evolution

Read this reference only when a change may add, retain, or remove a legacy schema, persisted or wire representation, or compatibility path; reinterpret stored data; affect an external contract; or require multi-version interoperability. Replacing internal code or architecture alone does not activate this lane. Preserve valid capabilities and real obligations, not historical representations.

## Resolve the Mode

Use the highest-priority applicable task and repository instructions. A current user statement may refine a generic repository lifecycle default when they are otherwise compatible; it cannot override a stricter governing instruction. If signals conflict and the choice could destroy valuable data or break an external contract, ask before the destructive action. Do not infer pre-release status from missing tags, migrations, references, or production configuration.

- **Known pre-release:** Default to breaking code and schema evolution within the affected capability. Remove compatibility that only serves unshipped representations. Do not assume discovered persisted data is disposable: if its value or disposability is unclear and cleanup is irreversible, ask one concise question before deletion. A backup limits loss but does not establish permission to discard the data. Treat identified valuable data, external contracts, deployment interoperability, and rollback as obligations.
- **Known released:** Identify real obligations such as published contracts, live clients or downstream consumers, valuable persisted data, queued events, mixed-version deployment, and rollback. Preserve them unless an applicable instruction explicitly authorizes the breaking change and its consequences. Compatibility is not automatically permanent.
- **Unknown:** Ask one concise release-status question only when the answer would change compatibility, stored-data interpretation, or an external contract. Otherwise continue without compatibility work.

## Record the Decision

Keep the result internal and compact:

- **Preserve:** current capabilities, contracts, and valuable data with evidence;
- **Remove:** superseded representations with no obligation in the selected mode;
- **Compatibility:** none, or the identified consumer plus owner, verification, and removal condition;
- **Owner:** the single authority for resulting state, lifecycle, schema, or protocol.

Evidence includes current requirements, published contracts, real consumers, valuable data, deployment constraints, and tests that still express intended behavior. Existing code, schemas, tests, types, fixtures, aliases, or fallbacks alone do not prove an obligation.

## Implement and Verify

- With no obligation, replace the old path directly and remove its affected fields, aliases, dual reads/writes, fallbacks, obsolete transitional migration machinery, code, types, tests, fixtures, and documentation. Preserve a reproducible schema or bootstrap path; rewrite or squash migration history only through the repository's or framework's supported workflow. Do not leave a parallel legacy system.
- With an obligation, prefer an official migration or compatibility mechanism. Keep one owner; make transitional behavior observable, tested, bounded, and tied to a removal condition. Do not silently mask incompatible or invalid data.
- Before deleting a legacy test, port every assertion that still describes current required behavior. Delete only assertions tied solely to the superseded representation.
- For valuable or irreplaceable data, rehearse migration on a representative copy, validate completeness and semantic equivalence, and establish a recoverable backup or rollback path before destructive cleanup.
- For rolling or multi-version deployment, verify applicable old-to-new, new-to-old, mixed-version, and rollback paths.
- Limit cleanup to the affected capability and seam. Do not convert the task into unrelated repository debt removal.
