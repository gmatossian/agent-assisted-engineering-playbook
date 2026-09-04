# Bounded Task Lifecycle

## Purpose and boundary

This lifecycle governs a bounded engineering task. It begins when higher-level
project work yields a candidate outcome and ends when the proposed change is
accepted or otherwise disposed of and remaining work is durably recorded.

It does not define how products are conceived, roadmaps are prioritized, or
projects are managed. Those activities produce candidate work for this
lifecycle but require their own future play family.

The phases below are **plays**. A **workflow** selects and composes the plays
that add value for a particular task. A simple, familiar change may combine or
skip explicit artifacts; a consequential or uncertain change may require each
play and additional checkpoints. The concerns still need to be handled
proportionally even when no separate document is produced.

## Lifecycle overview

| Play | Starts with | Produces | Human checkpoint |
| --- | --- | --- | --- |
| Refinement | Candidate work | A reviewable work-item contract | Decide whether the item is ready for its next actor |
| Planning | An accepted contract | A sufficient implementation approach | Resolve consequential choices and accept or revise the approach |
| Implementation | The contract and accepted approach | A proposed change | Confirm deviations, new decisions, and scope remain acceptable |
| Verification | The exact proposed revision | Current, accurately reported evidence | Decide whether evidence gaps require more work |
| Review | Contract, governing context, diff, and evidence | Classified findings | Disposition each material finding |
| Acceptance | The proposal, evidence, and findings | Accept, revise, reject, or defer decision | Human makes the decision |
| Closure and handoff | The disposition and remaining work | Cold-resumable durable state | Confirm the record is accurate and complete |

The lifecycle may loop. New evidence can return implementation to planning,
verification can return a change to implementation, and review can expose a
contract concern that requires refinement. These are controlled responses to
evidence, not failures to follow the lifecycle.

## 1. Refinement

Refinement turns a candidate outcome into a contract suitable for its intended
next play and actor. For substantial delegated implementation, address:

- **Outcome:** what observable result should exist?
- **Governing context:** which repository documents and existing decisions
  apply?
- **Scope and non-goals:** what is committed, and what is deliberately excluded?
- **Acceptance criteria:** how will a reviewer distinguish complete from
  incomplete?
- **Constraints and invariants:** what must remain true?
- **Authority:** what may the assigned agent decide or change, and what remains
  reserved?
- **Verification:** which checks and observations should provide evidence?
- **Dependencies:** what must already exist or happen?
- **Unresolved decisions:** which consequential questions are still open?

A concise `None` is valid. Omitting a concern through oversight is not.

Readiness is not a universal document-completeness score. It means the intended
next actor can begin the selected play without making an unacknowledged
consequential decision. The human marks or treats an item as ready only after
accepting that judgment.

## 2. Planning

Planning determines a sufficient approach before artifacts are generated. The
level of detail depends on uncertainty, consequence, familiarity, delegation,
and reversibility.

A useful plan identifies:

- the affected areas and intended design;
- the order and boundaries of the work;
- the verification strategy;
- important failure modes and risks;
- assumptions being relied upon;
- meaningful alternatives when they genuinely exist; and
- decisions that still require human judgment.

The issue itself may contain the complete plan. A knowledgeable human may also
supply an accepted approach or implement a known fix directly. Do not require
a separate agent-generated plan when it adds no useful control or evidence.

When planning exposes a consequential gap, return to refinement. For
foundational, unfamiliar, or high-consequence work, an independent plan review
may be useful before implementation; it is not mandatory by default.

## 3. Implementation

Implementation turns the accepted contract and approach into a proposed
change. Within that boundary, the implementing agent may make routine,
reversible choices, add or update tests, run relevant checks, and self-review
the diff.

The implementer must stop and escalate when it encounters a stop condition from
[the principles](principles.md#4-bounded-autonomy-escalation-and-meaningful-checkpoints).
In particular, it must not silently redefine the outcome, expand or narrow the
scope, change reserved decisions, or keep following an approach contradicted by
new evidence.

The result of implementation is a proposal, not an accepted change. Record any
material deviation from the accepted approach and the reason for it.

## 4. Verification

Verification produces evidence about the exact proposed revision. Use the
project-local profile and work-item contract to determine the required checks.

Protect verification integrity:

- identify the revision or working-tree state covered;
- report each relevant check as passed, failed, unavailable, or not run;
- do not present results from an earlier revision as current;
- do not weaken or bypass the verification contract merely to get green output;
- make intentional changes to expected behavior or verification explicit; and
- state known coverage limits and manual observations accurately.

Verification may include automated tests, type checking, schemas, linting,
builds, security checks, generated-artifact checks, targeted manual behavior,
or other project-defined evidence. More checks are not automatically better;
choose evidence that addresses the change's material claims and risks.

## 5. Review

Review evaluates the proposal relative to its accepted contract. Supply the
reviewer with:

- the current work-item contract and any accepted amendments;
- governing repository documentation;
- any durable accepted plan needed to understand the change;
- the complete final diff; and
- verification evidence for that revision.

Do not ask the reviewer to infer requirements from the implementation. Do not
use the implementing agent's private reasoning or approval as evidence.

Classify material findings as a blocking defect, verification gap, contract
concern, or follow-up/optional improvement. A finding should cite the relevant
requirement or invariant and concrete evidence. The human dispositions the
finding; the reviewer does not silently expand the contract.

### Independent review

Independence is a difference in perspective, not ignorance of accepted context.
An independent reviewer:

- did not implement the proposed change;
- begins from a fresh context;
- receives the accepted contract, governing decisions, diff, and evidence;
- performs a read-only, evidence-based review; and
- returns findings for human disposition.

Use independent review when its additional perspective is proportionate to a
risk, uncertainty, or weakly verified area. A different model or vendor is
optional, not a requirement. Independent review does not replace deterministic
verification or human acceptance.

### Review timing

Perform one genuine review of the complete final diff. If it occurs before the
change is pushed, the pull-request checkpoint confirms that the reviewed and
pushed revisions match, reviews subsequent deltas, checks current CI, and
reconciles acceptance criteria and known gaps. If no coherent pre-push review
occurred, review the complete pull-request diff.

Every material post-review delta requires review and reconsideration in the
context of the whole change. Do not describe an unchanged reread by the same
party as a new quality gate.

## 6. Acceptance

Acceptance is a human decision informed by the proposal, verification evidence,
review findings, known gaps, and project rules. The available dispositions are:

- **accept** — the contract is satisfied and the evidence is sufficient;
- **revise** — further work is required within the current contract;
- **reject** — the proposal should not proceed; or
- **defer** — acceptance cannot yet be decided, with the blocker recorded.

A green check or favorable agent review informs this decision but does not make
it automatically.

## 7. Closure and handoff

Close or pause the task with enough durable information for a capable person or
agent with no transcript to resume safely. Record, when material:

- the accepted or rejected outcome;
- the exact revision and verification evidence;
- review findings and their disposition;
- deviations from the contract or plan;
- known limitations, blockers, and unresolved questions;
- remaining work and whether it was completed, filed, rejected, or blocked;
- the current repository or work-item state; and
- the next recommended action.

The repository, issue, pull request, checks, and explicit decision records form
the durable evidence. The conversation that produced them is optional context,
not required project memory.
