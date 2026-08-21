# L0 — Mechanical example

[Task]
Replace one obsolete command in an existing guide with the current command and leave the rest of the document unchanged.

[Risk]
L0; this is a single-point, reversible documentation edit.

[Boundaries]
- Edit only the guide section containing the command.
- Preserve the existing tone, structure, and surrounding example.
- Add no dependency and do not broaden the scope.

[Delegation]
Parent confirms scope and reviews the diff; child locates the text, edits it, and performs a documentation self-check.

[Acceptance]
- The obsolete command is absent from the target section.
- No unrelated paragraph changed.

[Report]
Return only status, changed file, and self-check result.
