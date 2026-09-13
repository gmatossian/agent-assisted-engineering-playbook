# Agent-Assisted Engineering Playbook

A human-led, evidence-driven approach to designing, delegating, verifying,
reviewing, and learning from software engineering with coding agents.

## Why this exists

Coding agents make **implementation fast**. They do not automatically make the
**intended outcome clear**, preserve decisions outside a conversation, know
which choices belong to a human, or prove that their work is correct.

This playbook addresses the engineering work between an initial request and an
accepted change:

- making the intended outcome and constraints explicit;
- deciding what an agent may do and when it must stop;
- selecting only the planning, implementation, review, or learning activities
  that add value for this task;
- checking the result against current evidence; and
- preserving enough durable context for someone else to continue safely.

The objective is **useful agent autonomy** without giving up **human
understanding, judgment, or accountability**. The guidance is vendor-neutral
and does not depend on a particular agent, model, editor, hosting platform,
company, or project. It documents an approach developed through real delivery
work with coding agents.

## The 60-second model

1. **Make the work understandable.** Record the outcome, relevant context,
   constraints, acceptance criteria, and unresolved consequential decisions.
2. **Choose the appropriate plays.** Use only the refinement, planning,
   implementation, verification, review, acceptance, or handoff activities that
   fit the work.
3. **Delegate with boundaries.** Let the agent continue through clear, routine,
   reversible work. It stops when material uncertainty, risk, or missing
   authority appears.
4. **Verify the exact proposal.** Tests, builds, CI, and targeted manual checks
   provide evidence. An agent's confidence or another agent's approval is not
   proof.
5. **Keep acceptance human.** A human resolves material findings and decides
   whether to accept, revise, reject, or defer the proposal.
6. **Leave durable state.** Important decisions, evidence, limitations, and next
   actions must not depend on recovering the original chat.

The playbook is deliberately **firm about authority, evidence, escalation, and
acceptance**. It is deliberately **flexible about how much process** a task
needs.

## How the pieces fit together

```text
central principles + reusable plays
                  |
                  | adapted by
                  v
       project-local profile
                  |
                  | applied to
                  v
 task-specific workflow -> evidence -> human acceptance
```

| Term | Plain-language meaning |
| --- | --- |
| **Playbook** | This overall collection of reusable guidance. |
| **Play** | One bounded kind of work, such as refinement, planning, implementation, verification, or review. |
| **Workflow** | The plays selected and combined for a particular task. There is no required universal sequence. |
| **Project-local profile** | A repository's own explanation of its authorities, risks, commands, checks, and adaptations. |

The central playbook explains reusable reasoning. A consuming repository keeps
its operational rules close to the work so that a human or agent can operate
safely without access to a private conversation or this repository.

## Choose a workflow that fits the task

Two tasks in the same project may need different treatment.

| Familiar, reversible fix | Uncertain or consequential change |
| --- | --- |
| The human may already know the appropriate change and implement it directly. | Begin by resolving product, architecture, security, or other consequential decisions. |
| An agent may join only for targeted testing or review. | Make the contract and approach reviewable before substantial delegation. |
| A concise issue and focused verification may be sufficient. | Use stronger planning, broader verification, and possibly independent review when those reduce a named risk. |
| Extra artifacts are unnecessary when they add no control, evidence, or understanding. | Stop and return to discovery or planning when implementation exposes a material gap. |

The point is **not to maximize** the number of agents, prompts, documents, or
checkpoints. The point is to apply **enough structure** to make the work safe,
understandable, and reviewable.

## Human and agent responsibilities

The **human engineer owns the outcome**. That does **not require typing every
line**. Ownership comes from controlling the objective, consequential decisions,
constraints, delegated authority, verification standard, review disposition,
and final acceptance.

Within an accepted boundary, an agent may investigate, propose, implement,
verify, or review. **Permission for one phase does not automatically grant
another**: permission to plan is not permission to implement, and permission to
implement is not permission to merge, publish, change accepted requirements, or
perform otherwise restricted actions.

## How the playbook is applied

The playbook is applied in this sequence:

1. Engineers read the [principles](docs/principles.md) for the accepted human
   and agent operating model.
2. They use the [bounded task lifecycle](docs/task-lifecycle.md) to select the
   plays that add value for the current task.
3. Each consuming repository defines a concise
   [project-local profile](docs/project-profiles.md).
4. Teams use the profile during real work. When experience exposes a useful
   pattern, missing rule, or unnecessary process, they preserve the conclusion
   and decide whether the profile or central guidance should change.

For the practical sequence from repository entry point to task delegation, see
[Starting work with an agent](docs/project-profiles.md#starting-work-with-an-agent),
including examples for proposing a workflow and proceeding after one has been
accepted.

The project-local profile is the **operational authority** for its repository.
Central guidance does not silently override local rules, and conflicts must be
surfaced rather than guessed away.

## Case studies

- [Engineering Reference adoption](case-studies/engineering-reference.md) — a
  short retrospective and lessons catalogue from the playbook's first
  consuming repository. It is a case study, not normative guidance.

## What this is not

This is not:

- one mandatory workflow for every change;
- an agent framework or orchestration product;
- a replacement for product judgment, engineering expertise, or verification;
- a requirement to involve an agent in every phase; or
- a claim that more process automatically produces a better result.

## Maturity and change

This repository is an **early and evolving public work in progress**, developed
through use in real delivery work. Its guidance is revised based on delivery
evidence; it is not presented as complete or universally proven.

Canonical documents contain the currently **accepted** guidance. Accepted
means adopted for current use, not permanently settled. Proposed or
experimental ideas remain in clearly identified issues until accepted. If an
experimental rule is temporarily included in canonical guidance, it must be
marked as experimental and linked to its tracking issue.

Durable conclusions and rationale belong in repository files. Raw transcripts
may help private recovery, but readers and maintainers should not need them to
understand the playbook or continue its work.

## License

This repository is proprietary and published publicly for visibility and
feedback only. No open-source or other license is granted, and all rights are
reserved. External contributions are not accepted. See [LICENSE](LICENSE).
