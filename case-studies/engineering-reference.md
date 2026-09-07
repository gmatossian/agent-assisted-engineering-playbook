# Engineering Reference: the playbook in practice

## Purpose

This is a short retrospective on using the playbook while building
[Engineering Reference](https://github.com/gmatossian/engineering-reference),
its first consuming repository.

Its purpose is to preserve useful experience for the human owner and the agents
helping to evolve the playbook.

This retrospective records experience from one project; it is not canonical
guidance.

## How it was used

The central playbook provided reusable principles and plays. Engineering
Reference then created a self-contained
[project-local profile](https://github.com/gmatossian/engineering-reference/blob/main/docs/ai-assisted-development.md)
for its own sources of truth, workflow states, authority boundaries, stop
conditions, verification, review, and durable state.

For substantial tasks:

- the issue described the outcome, scope, acceptance criteria, verification,
  and non-goals;
- a kickoff comment selected the plays for that task and assigned planning,
  implementation, verification, review, and acceptance responsibilities;
- meaningful human checkpoints were agreed before implementation;
- the agent continued through routine work inside the accepted boundary;
- automated checks, agent review, and human acceptance remained distinct; and
- repository documents and GitHub artifacts preserved decisions and state
  outside the conversation.

The kickoff was not a fixed template. Existing examples show different levels
and kinds of ceremony:

| Task shape | Example | What the kickoff emphasized |
| --- | --- | --- |
| Concise delegated implementation | [Application shell](https://github.com/gmatossian/engineering-reference/issues/25#issuecomment-5548651859) | Workflow, responsibilities, checkpoints, and the reason for independent review in five short entries. |
| Substantial cross-boundary implementation | [Runtime catalog pilot](https://github.com/gmatossian/engineering-reference/issues/21#issuecomment-5548295731) | A fuller division of authority, multiple checkpoints, review timing, stop conditions, and GitHub responsibilities. |
| Verification-led work | [Cross-browser and accessibility verification](https://github.com/gmatossian/engineering-reference/issues/31#issuecomment-5552344761) | The split between agent-run automation and human-run checks, with independent review initially omitted. |

These are examples, not required formats. Smaller or more familiar tasks may
need less—or no separate kickoff—when another artifact already makes the
workflow and boundaries clear.

No single GitHub issue or document was considered the complete project memory.
The profile, governing documents, issues, comments, branches, pull requests,
checks, and accepted code each answered different questions.

## What felt useful

### Context outside conversations

The project profile and governing documents reduced the need to reconstruct
context whenever an agent session changed. Decisions and constraints could be
revisited directly instead of recovered from a long-running transcript.

### Structure proportional to the task

Detailed contracts and plan checkpoints helped when work crossed several
technical boundaries. Once consequential choices were accepted, the agent
could implement, test, and make routine corrections without requesting approval
after every step.

The same process would have been wasteful for a familiar, reversible fix. The
useful idea was choosing from a set of plays, not imposing one workflow on every
task.

### Delegation without giving up understanding

After delegated implementation, reviewing the result with the agent and asking
questions about unfamiliar code supported both review and learning. This felt
more useful than manually copying agent-authored code into files.

Implementation could be delegated while the human retained consequential
decisions, understanding, finding disposition, acceptance, and merge.

### Clearer meanings for checks and reviews

Automated verification, the implementing agent's self-review, optional
independent review, and human acceptance served different purposes. Keeping
them distinct avoided treating passing tests or a favorable agent response as
automatic approval.

It also helped avoid duplicate ceremony. If the complete change had already
been reviewed, the pull-request checkpoint could concentrate on later changes,
current CI, and final acceptance instead of repeating the same review.

### Enough progress tracking without another system

For the tasks completed so far, the GitHub project board provided enough
visibility into whether work was waiting, active, under review, or done. A more
detailed task-visualization tool might help with longer-running work, but was
not necessary merely because one was available.

## What did not become a rule

- Long kickoff comments were not required for small tasks.
- Independent review was selected when another perspective seemed useful, not
  performed automatically for every change.
- Feedback was not recorded after every task. Useful process changes usually
  emerged when friction was noticed during the work.
- Engineering Reference's GitHub conventions and verification commands were
  project-specific, not central playbook policy.
- The experience did not justify new automation or templates simply to make
  every task look uniform.

## Working lessons

1. Keep reusable principles central and project-specific operating context near
   the work.
2. Preserve important context outside agent conversations.
3. Make substantial delegated work clear enough that the agent need not invent
   consequential decisions.
4. Fit the workflow to the task instead of maximizing artifacts, agents, or
   checkpoints.
5. Separate implementation authorship from human understanding, judgment, and
   acceptance.
6. Let friction from real work drive process changes instead of requiring a
   retrospective ritual after every task.

These are observations worth testing again, not newly adopted canonical
principles.

## Still unknown

More experience is needed to decide:

- when independent review consistently justifies its cost;
- how short a useful kickoff can be;
- when work becomes large enough to need more detailed progress visualization;
- which patterns remain useful across other projects and people; and
- which parts of the iterative UI-design experience should become a reusable
  play.

The UI-design question remains a separate
[experimental play candidate](https://github.com/gmatossian/agent-assisted-engineering-playbook/issues/3).

## References

- [Engineering Reference project-local profile](https://github.com/gmatossian/engineering-reference/blob/main/docs/ai-assisted-development.md)
- [Profile definition and pilot retrospective](https://github.com/gmatossian/engineering-reference/issues/22)
- [Example substantial-task contract and kickoff](https://github.com/gmatossian/engineering-reference/issues/21)
