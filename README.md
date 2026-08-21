# lean-taskbook

[简体中文](README.zh-CN.md)

**Agent Skills compatible. Codex-first. Sol + Luna tested.**

`lean-taskbook` writes compact, risk-proportional taskbooks for Codex parent/subagent workflows. It preserves the handoff contract—goal, risk, boundaries, delegation, acceptance, and concise reporting—without pre-solving implementation details.

Current version: `v0.2.3`.

## Use when

- You need a taskbook for a bounded coding or repository task.
- You are handing work from a strong Codex parent to a lower-cost implementation Agent.
- You want L0 mechanical, L1 normal, or L2 high-risk scoping with proportionate verification.
- The user asks for a Codex implementation brief, parent Sol plus child Luna handoff, or cost-aware delegation.

## Don't use when

- The user wants an ordinary answer, explanation, or direct code change.
- There is no parent/subagent handoff or taskbook to write.
- The request needs a full project plan rather than a minimal executable brief.

## Install

### Recommended

```bash
npx skills add bevis7781/lean-taskbook
```

The installer should create a discovered `lean-taskbook` skill directory and preserve `SKILL.md` plus `agents/openai.yaml`.

### Codex manual installation

Clone or download this repository, then copy its contents into one of these locations:

- Repository-scoped: `<repo-root>/.agents/skills/lean-taskbook/`
- User-scoped: `~/.agents/skills/lean-taskbook/`

The target directory must contain `SKILL.md` and may also contain `agents/openai.yaml`. Its final directory name must be `lean-taskbook`, matching the frontmatter `name`. Restart Codex if a newly installed skill does not appear.

## Call it

Invoke it explicitly with `$lean-taskbook`, or ask for a taskbook/parent-subagent handoff and let implicit selection match the description.

```text
Use $lean-taskbook to write a minimal taskbook for adding a read-only health endpoint.
```

The skill writes the taskbook in the user's current language by default. It does not execute the work or authorize external side effects; the parent remains responsible for final acceptance.

## Compatibility boundary

This repository follows the Agent Skills format and is Codex-first. It has been tested with Sol + Luna. No support or verification is claimed for other harnesses.

## Examples

- [L0 mechanical](examples/L0-mechanical.md)
- [L1 normal](examples/L1-normal.md)
- [L2 high risk](examples/L2-high-risk.md)

## Acknowledgements and license

See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for upstream attribution. This project is MIT licensed; see [LICENSE](LICENSE).
