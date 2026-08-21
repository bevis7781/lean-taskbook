# lean-taskbook

Codex-first. Sol + Luna tested.

`lean-taskbook` is a compact taskbook skill for handing bounded AI coding work from a strong parent agent to a lower-cost implementation agent. It keeps the goal, risk, boundaries, delegation, acceptance checks, and concise report in one small brief.

## Version

Current release: `v0.2.2`.

## Install

Copy `SKILL.md` into the skills directory used by your Codex installation, preserving the filename and its parent skill folder. For a local checkout, the skill can be referenced directly from this repository. No build step or runtime dependency is required.

## Use

Invoke the skill when you need a minimal, executable taskbook for a Codex parent/child workflow—for example, when handing a bounded change to a local child agent. The skill classifies work as L0 (mechanical), L1 (ordinary engineering), or L2 (high risk), then keeps delegation and verification proportional to that risk. The included examples show the intended level of abstraction:

- `examples/L0-mechanical.md`
- `examples/L1-normal.md`
- `examples/L2-high-risk.md`

The skill is a writing aid and operating rule set; it does not execute changes, replace repository review, or authorize external side effects. For licensing, security, production, privacy, deletion, migration, and other high-impact work, follow the stricter checks described in the skill and your own project controls.

## Acknowledgements

This project preserves ideas and terminology informed by:

- [jellydn/my-ai-tools](https://github.com/jellydn/my-ai-tools)
- [obra/superpowers](https://github.com/obra/superpowers)
- [ashp15205/vibe-coding-essentials](https://github.com/ashp15205/vibe-coding-essentials)

See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md) for attribution and license notes.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
