# Principles

## Status

These principles are the playbook's currently accepted guidance. Accepted
means adopted for current use, not universally proven or permanently fixed.
The playbook should change when evidence from real work shows that a principle
is incomplete, ambiguous, or unnecessarily costly.

## 1. Human ownership and decision authority

A human engineer owns the outcome even when an agent authors most or all of a
change. Ownership comes from controlling the objective, consequential
decisions, constraints, delegated authority, verification standard, review
disposition, and final acceptance. Typing every line is neither necessary nor
sufficient.

Agents may investigate, propose, implement, verify, or review within an
explicitly assigned phase. Authority for one phase does not automatically
grant authority for another: permission to plan is not permission to implement,
and permission to implement is not permission to merge, publish, change
accepted requirements, or perform otherwise restricted actions.

The human remains responsible for deciding whether the evidence is sufficient
and whether the result should be accepted.

## 2. Proportional process and situational play selection

Use the play that fits the work rather than forcing every change through one
universal procedure. Decision discovery, guided setup, delegated
implementation, investigation, review, walkthrough, and evaluation serve
different purposes.

Select and combine plays according to:

- the consequences of being wrong;
- uncertainty in the problem or solution;
- reversibility of the work;
- the authority required;
- the strength of available verification; and
- where agent assistance adds value given the human's existing knowledge.

A familiar, low-consequence fix may need only implementation and targeted
verification or review. A foundational or unfamiliar change may need explicit
discovery, planning, and additional review. Do not manufacture artifacts or
ceremony that add no control, evidence, or understanding.

## 3. Explicit contracts, readiness, scope, and non-goals

Before substantial delegation, make success understandable without requiring
the originating conversation. A work-item contract should address,
proportionally:

- the intended outcome and governing context;
- committed scope and explicit non-goals;
- observable acceptance criteria;
- constraints and invariants;
- delegated and reserved authority;
- expected verification;
- dependencies; and
- unresolved consequential decisions.

Readiness is a human decision relative to the next play and actor. An item may
be ready for investigation or planning before it is ready for delegated
implementation. The next actor must be able to begin without silently resolving
a consequential decision. A concise `None` is sufficient when a concern does
not apply.

Both scope expansion and scope narrowing must be explicit. Agents must not
quietly add capabilities or omit promised behavior. Remaining work is
completed, filed as a concrete follow-up, rejected with a reason, or recorded
as blocked.

## 4. Bounded autonomy, escalation, and meaningful checkpoints

Agents should continue through routine, reversible choices when the accepted
contract is clear. They should stop and surface the issue when work encounters:

- material ambiguity or conflicting requirements;
- a consequential decision not already made;
- evidence that invalidates the accepted approach;
- unsafe or difficult-to-reverse action;
- required authority that was not delegated; or
- meaningful expansion or narrowing of scope.

An accepted plan is a working contract, not an instruction to ignore new
evidence. When evidence makes it unsafe, incomplete, or materially unsuitable,
return to planning instead of silently replanning or complying blindly.

Place checkpoints after coherent, reviewable outcomes—such as refined scope,
an accepted approach, a working implementation slice, completed verification,
or a review. Do not require approval after every command, file edit, test, or
routine subtask.

A clarification does not by itself replace the active objective. Answer it in
the context of the current work, record any durable consequence, and return to
the active track unless the human explicitly requests a pivot.

## 5. Verification, evidence-based review, and human acceptance

Verification must describe the exact proposed revision. Report checks honestly
as passed, failed, unavailable, or not run. Do not present stale evidence as
current, and do not weaken, remove, or skip tests, types, schemas, lint rules,
or CI merely to obtain a passing result. An intentional change to expected
behavior or to the verification contract is itself a visible decision.

Verification should be proportional to consequence and uncertainty. Agent
review is not deterministic verification, and absence of evidence is not a
pass.

Recording evidence does not by itself make that evidence current, approve a
result, complete a play, or accept a task. Those remain explicit decisions
unless a project-local rule defines a trusted transition.

Review compares the accepted work-item contract, governing repository
documentation, final diff, and current evidence. It should find defects and
gaps, not substitute the reviewer's preferred product or architecture for
accepted decisions. Classify findings as:

- **blocking defect** — the proposed change cannot safely be accepted;
- **verification gap** — a material claim lacks adequate evidence;
- **contract concern** — requirements or governing decisions are unclear,
  inconsistent, or unmet; or
- **follow-up or optional improvement** — useful work that is not required for
  the current acceptance decision.

Perform one deliberate review of the complete final change. If that happens
before a pull request, the pull-request checkpoint confirms that the pushed
revision is the reviewed revision, examines later deltas, checks current CI,
and reconciles acceptance criteria and known gaps. Repeating the same review
with the same perspective and no new evidence is ceremony, not another quality
gate.

Independent review is optional and proportional. When used, the reviewer did
not implement the change, begins with fresh context, receives the accepted
requirements and constraints, reviews read-only, and returns findings for
human disposition. A different model or vendor may add perspective but is not
required. Independent review is advisory; it is neither verification nor human
acceptance.

## 6. Durable memory and cold-resumable handoff

Repository files and other explicit project authorities hold accepted
decisions, current state, constraints, and evidence. Transcripts may help with
private recovery but are not authoritative project memory and should not be a
prerequisite for understanding or continuing the work. An implementing agent's
private reasoning or self-assessment is not verification evidence.

Before pausing or handing off meaningful work, preserve enough durable state
for a capable person or agent with no chat history to resume safely. Record:

- what was decided and completed;
- the current revision and relevant evidence;
- remaining work and its disposition;
- constraints, blockers, and unresolved questions; and
- the next recommended action.

Apply this when losing the current context would make resumption unreliable or
wasteful, not after every minor interruption.

## 7. Central guidance with project-local adaptation

This repository provides reusable principles, terminology, and plays. A
consuming repository defines how they apply to its own architecture, sources
of truth, risks, commands, authority boundaries, review practices, and delivery
lifecycle through a project-local profile.

The local profile is the operational authority for that repository. It must be
self-contained enough for safe local work without requiring access to this
central playbook. Central guidance does not silently override local rules, and
conflicts must be surfaced rather than guessed away.

Avoid copying the complete playbook into every repository. Keep central
rationale here and concise, actionable adaptation near the work it governs.
