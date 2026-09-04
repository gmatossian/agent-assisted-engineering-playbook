# Agent-Assisted Engineering Playbook

A human-led, evidence-driven approach to designing, delegating, verifying,
reviewing, and learning from software engineering with coding agents.

## Purpose

This repository is an operational playbook for engineers who want useful agent
autonomy without giving up human understanding, judgment, or accountability.
It provides reusable guidance for turning intended outcomes into bounded work,
delegating appropriate parts of that work, evaluating the resulting evidence,
and preserving enough durable context to continue safely.

The guidance is vendor-neutral. It does not depend on a particular agent,
model, editor, hosting platform, company, or project.

## Audience

The playbook is for engineers and teams incorporating coding agents into real
delivery work. It is especially concerned with the practical questions that
appear between a prompt and a merge:

- Which decisions should remain human decisions?
- When is work ready to delegate?
- How far should an agent proceed without interruption?
- When should it stop and escalate?
- What evidence supports review and acceptance?
- How can another session resume without relying on a hidden transcript?

## Terminology

- The **playbook** is this overall collection of reusable guidance.
- A **play** is a bounded way of performing a phase of work, such as refinement,
  planning, implementation, verification, or review.
- A **workflow** is a situational composition of plays chosen for a particular
  task.

There is no single required workflow. A familiar, reversible fix and an
uncertain architectural change should not receive identical ceremony. The
appropriate workflow depends on consequence, uncertainty, reversibility,
authority, available verification, and where agent help adds value.

## Start here

1. Read the [principles](docs/principles.md) for the human and agent operating
   model.
2. Use the [bounded task lifecycle](docs/task-lifecycle.md) to understand how a
   candidate task moves through refinement, implementation, evidence, review,
   acceptance, and handoff.
3. Read [project-local profiles](docs/project-profiles.md) when applying the
   playbook to a specific repository.

The central playbook supplies reusable rationale and plays. Each consuming
repository remains independently operable through a concise local profile that
defines its own authorities, risks, commands, checks, and adaptations.

## Maturity and change

This repository is early and evolving. Its guidance is intended for real use
and revision based on delivery evidence; it is not presented as a finished or
universally proven methodology.

Canonical documents contain the currently **accepted** guidance. Accepted
means adopted for current use, not permanently settled. Proposed or
experimental ideas remain in clearly identified issues until accepted. If an
experimental rule is temporarily included in canonical guidance, it must be
marked as experimental and linked to its tracking issue.

Durable conclusions and rationale belong in repository files. Raw transcripts
may help private recovery, but readers and contributors should not need them to
understand the playbook or continue its work.
