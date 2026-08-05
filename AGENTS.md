# Repository orchestration

- Use `$xbrd-sol-ultra` as the default orchestration workflow for every task in this repository.
- The primary agent is the single Sol judge and canonical writer. Never recursively invoke `xbrd-sol-ultra` from a delegated task.
- Keep the root on `gpt-5.6-sol` with the repository reasoning default. Run the planner-first, evidence-gated Pareto loop in `SKILL.md` and use Sekhmet as the bounded L3 execution surface.
- Preserve existing worktree changes. Do not commit, push, publish, deploy, or perform other external mutations unless the user explicitly authorizes that action and target.

## Discovery

Codex skill discovery path (repo-relative symlink to this package root):

```text
.agents/skills/xbrd-sol-ultra/SKILL.md
```

That path resolves to the canonical root `SKILL.md` (same file as package entry). Do not maintain a second copy.

## Repository checks

- Validate the skill with:
  `python "${CODEX_HOME:-$HOME/.codex}/skills/.system/skill-creator/scripts/quick_validate.py" .`
- Confirm repository discovery with `test -f .agents/skills/xbrd-sol-ultra/SKILL.md`.
- Confirm the execution substrate with `sekhmet --version`.
