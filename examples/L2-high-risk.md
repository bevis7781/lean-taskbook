# L2 — High-risk example

[Task]
Design and execute a reversible field migration for an existing data table while keeping historical records readable.

[Risk]
L2; the work affects historical data and production state and can be difficult to undo.

[Boundaries]
- Confirm backup, rollback, locking, and compatibility-window requirements before execution.
- The migration must be repeatable or explicitly reject duplicate execution.
- Do not touch real production data or remove the old field before verification.
- Parent independently reviews the critical invariants and failure scenarios.

[Delegation]
Child performs narrow reconnaissance, the smallest migration implementation, and controlled-environment tests; parent owns risk scoping, critical review, and release authorization.

[Acceptance]
- A rehearsal passes volume, constraint, and historical read/write checks.
- Key counts and sampled contents match before and after migration.
- Rollback rehearsal succeeds and interruption does not leave a partial migration.
- Production execution still requires explicit authorization and independent backup evidence.

[Report]
Return only status, changed files, verification evidence, rollback result, and remaining risks.
