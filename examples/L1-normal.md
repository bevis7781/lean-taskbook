# L1 — Normal engineering example

[Task]
Add a read-only status endpoint with input validation to an existing small HTTP service and add focused tests.

[Risk]
L1; the change touches one module and route integration but does not migrate data or publish to users.

[Boundaries]
- Follow the existing routing, error format, and configuration conventions.
- The endpoint must not mutate business data.
- Do not refactor unrelated modules or add a runtime dependency.

[Delegation]
Parent performs minimal scope confirmation and final acceptance; child locates the implementation points, makes the smallest complete change, and runs focused tests.

[Acceptance]
- A valid request returns the agreed status shape.
- Invalid input uses the existing error format.
- Focused tests pass and show no regression in the nearby test surface.

[Report]
Return only status, changed files, test results, and unresolved risks.
