# Project-Local Profiles

## Purpose

The central playbook is reusable guidance. A project-local profile translates
that guidance into the concrete operating rules of one repository.

The profile is the operational authority for work in that repository. A human
or agent must be able to operate safely from the repository's own instructions
without access to this repository, a private conversation, or unstated personal
knowledge.

The central playbook explains reusable rationale and plays. It does not
silently override local rules. When central and local guidance conflict, surface
the conflict for human resolution instead of guessing which instruction to
follow.

## What a profile should establish

A profile should be concise, actionable, and proportional to the project. It
should cover the following concerns where they apply.

### Sources of truth and context routing

Identify the files or systems that authoritatively define product decisions,
architecture, current work, operational constraints, and durable history.
Explain which source answers which kind of question. Mark stale, derived, or
historical material so it cannot silently compete with current authority.

### Local lifecycle adaptations

State how the [bounded task lifecycle](task-lifecycle.md) maps to the project's
actual issue states and delivery process. Explain what `Ready`, `In progress`,
`Review`, `Done`, or equivalent states mean if the project uses them.

The project may combine or omit explicit plays when the omitted ceremony adds
no value. It must still handle material readiness, authority, verification,
review, acceptance, and handoff concerns.

### Delegated and reserved authority

Define which actions agents may perform without another checkpoint and which
remain human decisions. Account for both consequence and the assigned phase.

Examples that may require explicit local treatment include changes to accepted
requirements, destructive operations, external communication, secrets,
production systems, dependency policy, publishing, merging, and releases.
These examples are not universal central rules; the repository must define the
boundaries appropriate to its work.

### Escalation and risk boundaries

Record project-specific signals that require an agent to stop, such as changes
to a public contract, data integrity, security boundaries, irreversible state,
generated artifacts, migration behavior, or areas with weak verification.

Use path-based examples only when the architecture makes them reliable. Risk is
primarily shaped by consequence, uncertainty, reversibility, required
authority, and available evidence—not by a filename alone.

### Verification

List the exact commands, environments, and manual checks used to verify work.
Clarify:

- which checks apply to which kinds of changes;
- whether commands modify files or generate artifacts;
- which generated outputs are committed;
- any required thresholds or CI jobs;
- known limitations of the checks; and
- how exceptions are approved and recorded.

Results must cover the exact proposed revision and follow the verification
integrity rules in [the principles](principles.md#5-verification-evidence-based-review-and-human-acceptance).

### Review, acceptance, and merge

Explain where the deliberate final-diff review occurs, how later deltas are
handled, which evidence must be current, who dispositions findings, and who may
accept or merge a change.

If independent review is sometimes useful, describe how a human requests it
and what context the reviewer receives. Do not require it mechanically unless
the repository has evidence that a stable trigger improves outcomes.

### Durable state and handoff

Identify where accepted decisions, current progress, verification evidence,
review findings, known gaps, and next actions are recorded. Make meaningful
interrupted work cold-resumable without requiring transcript recovery.

## Entry points and supporting mechanisms

Use a concise `AGENTS.md` or equivalent canonical agent entry point to route
agents to the repository's local profile and authoritative documents. If a tool
requires an additional vendor-specific instruction file, it should redirect to
the canonical guidance rather than introduce unique policy.

Issue and pull-request templates, CI, and other automation may operationalize
the profile after real usage demonstrates which fields and checks are useful.
They are supporting mechanisms, not substitutes for clear authority or human
judgment.

## Keeping profiles independent and current

Do not copy this entire playbook into a consuming repository. Copying creates
multiple policy sources that can drift silently. Instead:

- keep reusable rationale and plays central;
- keep project-specific rules beside the project;
- make the local profile self-contained for safe operation;
- update local rules deliberately when the project learns something; and
- surface central/local conflicts rather than resolving them implicitly.

The playbook does not yet prescribe a versioning, baseline, or synchronization
mechanism for profiles. Revisit that design after multiple repositories use
profiles or actual drift demonstrates the need. Until then, clarity and local
operability are more valuable than speculative coordination machinery.
