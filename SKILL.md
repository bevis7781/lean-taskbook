---
name: lean-taskbook
description: >-
  Create minimal, executable taskbooks for Codex parent/subagent workflows.
  Use when the user asks for a taskbook, a Codex implementation brief, a parent
  Sol plus child Luna handoff, cost-aware delegation, or an ultra-lean
  construction prompt, including Chinese triggers such as 下任务书、施工提示词、
  父 Sol + 子 Luna、省额度施工、极简任务书. Do not use for ordinary questions
  or direct implementation without a taskbook handoff.
license: MIT
compatibility: Agent Skills compatible; Codex-first; Sol + Luna tested. No other harness is claimed as verified.
metadata:
  version: "0.2.3"
---

# Lean Taskbook

Generate the smallest taskbook that remains executable and reliable for a bounded AI coding workflow.

## Core principle

The strong model defines what must not be wrong; the lower-cost model handles the concrete implementation.

A taskbook is not a detailed construction tutorial. By default, pass only:

1. The result to achieve.
2. The boundaries that must not be broken.
3. The facts that must be verified.
4. The parent and child Agent responsibilities.

Do not pre-reason through implementation details that the execution Agent can discover from the repository.

## Language

Write the taskbook in the user's current language by default. Preserve technical names, identifiers, commands, and code as needed.

## 1. Classify risk before deciding parent depth

Use exactly one of these three levels.

### L0 — Mechanical

Typical work includes a single-point fix, documentation, configuration, small cleanup, or another explicit repeatable operation.

- The parent does not perform a repository-wide scan.
- The parent does not design a step-by-step implementation plan.
- Delegate the goal, boundaries, and verification to the lower-cost child.
- The child locates the change, implements it, and self-tests.
- The parent reviews only the diff, changed paths, and relevant test results.

### L1 — Normal engineering

Typical work includes a multi-file feature, ordinary integration, or debugging within a known module.

- The parent performs only enough reconnaissance to confirm scope and risk.
- The child handles concrete file discovery, implementation, and focused testing.
- The parent does not repeat the child's complete reconnaissance.
- Acceptance covers the changed surface and key integration points.

### L2 — High risk

Upgrade to L2 if any of the following applies:

- Database migration, historical data, or an irreversible state change.
- Bulk deletion or cleanup of many files.
- Authentication, security, privacy, or secrets.
- License or open-source compliance.
- Production deployment, payment, or a real external side effect.
- Shared or protected branches, or changes affecting real external users.
- Core architecture or shared infrastructure.
- An error could contaminate later state and be difficult to recover.

Only L2 allows the parent to go deep enough to:

- State critical invariants.
- Inspect relevant core code when necessary.
- Design the failure scenarios that must be covered.
- Independently review the most important evidence.

Even for L2, do not automatically redo the child's entire repository investigation.

### Git and GitHub publication exception

A personal repository's ordinary commit, push, or first open-source publication is not automatically L2 merely because it is called a publication. Usually treat it as L1 and perform narrow checks directly related to publication:

- No secrets, credentials, personal paths, or oversized unintended files are included.
- README and installation instructions match the actual repository.
- The license is compatible with known third-party material.
- A minimal startup or smoke check passes when appropriate.

Upgrade publication work to L2 only when it affects real external users, a shared or protected branch, production, a paid service, or a significant license or security risk.

## 2. Taskbook length budget

Aim for the smallest sufficient taskbook:

- L0: no more than 350 tokens.
- L1: no more than 700 tokens.
- L2: no more than 1200 tokens.
- Unless the user explicitly requests a complete audit or architecture design, do not exceed 2000 tokens.

Compress the taskbook as follows:

- When repository access exists, give file paths instead of copying file contents.
- Do not copy long chat history; retain only the current goal, frozen decisions, and key constraints.
- Do not add background education.
- Do not write steps that the execution Agent can discover itself.
- Do not repeat the same constraint.
- Do not request a long explanation, long summary, or polished report.
- If missing information can be discovered by local repository reconnaissance, tell the execution Agent to confirm it rather than asking the user to guess.
- Do not ask the user for facts that can be confirmed from the repository, tests, configuration, or existing documentation.
- Ask only when the missing choice could change the goal, create an irreversible consequence, or require the user's value judgment.

Default behavior is to output a directly copyable taskbook. Do not explain the methodology or repeat long background unless the user asks.

## 3. Parent Agent responsibility limit

The parent normally does only these five things:

1. Confirm the result goal.
2. Confirm the risk level.
3. State the boundaries and invariants that must not be broken.
4. Identify the child Agent or model.
5. Perform narrow final acceptance based on the child's evidence.

If the current context already identifies a validated lower-cost child, use it. Otherwise write "the currently validated, lowest-total-cost child Agent that can do the work"; do not block only to ask for a model name.

By default, the parent should not:

- Fully design the implementation before delegation.
- Perform a full repository scan for an ordinary task.
- Specify every command, SQL statement, code path, or implementation step for the child.
- Repeat the child's complete reconnaissance after the child finishes.
- Expand review indefinitely merely because it seems safer.
- Turn a low-risk task into a release- or incident-grade process.

If proceeding appears to require broad reading, delegate the bounded read-only reconnaissance to the child first instead of expanding the parent's context unnecessarily.

## 4. Child Agent responsibility

The child is responsible for:

- Locating the relevant code and files within the task boundary.
- Choosing the smallest complete implementation.
- Making the requested changes.
- Running tests proportionate to the change.
- Checking obvious regressions.
- Returning concise evidence.

Explicitly specify the child model. Do not let it inherit the expensive parent model. Choose the currently validated model with the lowest total cost that can perform the work; do not choose solely by the cheapest single call if weakness would cause materially more rework.

Batch related, same-shaped independent work into one child task. Parallelize only when write scopes are independent and the parallel work genuinely saves time.

## 5. Verification strategy

Use this default order:

**Child self-test → parent narrow acceptance → broader verification only when triggered.**

The parent should first check:

- Which files were actually changed.
- Whether the diff stayed within scope.
- Whether the claimed tests really passed.
- Whether the task's one to three most important behaviors work.

Do not run the entire test suite by default after every small change. Expand verification only when:

- Shared core code was changed.
- A focused test behaves abnormally.
- The area has a known regression history.
- A release gate explicitly requires broader checks.
- L2 invariants require broader evidence.

### Retry limit

If the first acceptance fails, send the same child one targeted correction task focused only on the discovered issue.

If the second attempt still fails:

- Stop the automatic loop.
- Report the evidence and unresolved issue.
- State whether a stronger model or broader reconnaissance is needed.

Never run an unlimited modify → review → modify → review cycle.

## 6. Required taskbook structure

Unless L2 genuinely requires additional sections, output only:

```text
[Task]
One-sentence result goal.

[Risk]
L0 / L1 / L2; one sentence explaining why.

[Boundaries]
- Content that must remain intact.
- Explicitly prohibited extra changes.
- Leave other implementation details to the child Agent's reconnaissance.

[Delegation]
Parent: minimal scoping and final narrow acceptance.
Child: the explicitly selected, currently validated, lowest-total-cost model; responsible for reconnaissance, implementation, and self-test.
Do not let the child inherit the parent's expensive model.

[Acceptance]
List 2–5 observable completion conditions.
Prefer focused tests; expand only when a risk trigger requires it.

[Report]
Return only:
- Status.
- Changed files.
- Tests and verification results.
- Risks or unresolved items.
Do not provide a long construction retrospective.
```

Use the user's current language for the headings and prose unless a specific output language is requested.

## 7. Generation self-check

Before outputting a taskbook, check:

- Did I pre-solve implementation details that the child could discover?
- Did I make the parent perform unnecessary full-repository reconnaissance?
- Is the verification level proportional to the risk instead of automatically maximal?
- Did I explicitly select a lower-cost child model?
- Did I avoid duplicate audits and unlimited retry loops?
- Is the current-language rule respected?
- If I delete any sentence, would execution correctness, safety, or acceptance change? If not, delete it.

The objective is sufficient reliability with the least expensive reasoning, not a taskbook that merely looks comprehensive.
