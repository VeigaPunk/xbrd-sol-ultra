# xbrd-sol-ultra

Sol Ultra-native Godspeed orchestration modeled on [`xbrd-grok`](https://github.com/VeigaPunk/xbrd-grok), with [`Sekhmet`](https://github.com/VeigaPunk/xbrd-spark) (`xbrd-spark`) as the layer-3 execution surface.

**Sol Ultra is the only root judge.** It plans, judges evidence, Pareto-filters, resolves conflicts, integrates, and publishes the result. L3 workers never coordinate, never write the canonical tree, and never launch nested swarms.

Each round runs **exactly one** global Sekhmet wave: `sekhmet swarm --direct -j 64` (do not lower `-j 64`; do not run overlapping waves). Tasks are an **8 axes × 8 lenses** matrix (64 unique cells); connector coverage is mandatory every round.

## Runtime contract (matches `SKILL.md`)

| Rule | Contract |
| --- | --- |
| Root model | GPT-5.6 Sol Ultra only — no silent downgrade |
| Planner | Native `the-planner` **before** the first L3 wave |
| L3 dispatch | One wave per round: `sekhmet swarm --direct -j 64` (fallback binary: `xbrd-spark`) |
| L3 model pin | `gpt-5.6-luna`, low reasoning, fast service tier |
| Matrix | 8 × 8 axis/lens; connector cells every round |
| Rounds | 2–4 per activation; Round 2 always; 3–4 only while Pareto improvement remains |
| Mutations | Isolated snapshots only; **one** canonical writer integrates survivors |
| Evidence | Gate + Pareto (improve ≥1 axis, regress none); no voting / raw flatten |
| Worktree | Baselined preflight; ambient dirt never counts as improvement |
| Publication | Commit/push/deploy only when the request authorizes that action class |

Default read-only wave shape (see `SKILL.md` for mutation variants):

```bash
XBRD_SPARK_MODEL=gpt-5.6-luna \
XBRD_SPARK_FALLBACK_MODEL=none \
XBRD_SPARK_SERVICE_TIER=fast \
sekhmet swarm --direct -j 64 --ro --timeout 180 --no-keep \
  --tasks-file "$TASKS_JSONL" --root "$ROUND_ROOT"
```

## Invoke

```text
$xbrd-sol-ultra <objective>
```

Aliases: `xbsu`, `sol-ultra-godspeed`. Never spawn another `xbsu`.

## Package

- `SKILL.md` — full orchestration procedure and safety contract (authoritative)
- `agents/openai.yaml` — display metadata and default invocation
- `assets/icon.svg` — skill icon

## Related stack

| Piece | Role |
| --- | --- |
| [xbrd-spark](https://github.com/VeigaPunk/xbrd-spark) | L3 binary (`sekhmet` / `xbrd-spark`); global **64** concurrent runners |
| [xbgst](https://github.com/VeigaPunk/xbgst) | Grok-native Godspeed host stack (judge concurrency 16; L3 remains 64) |
| [ds4cc-marketplace](https://github.com/VeigaPunk/ds4cc-marketplace) | Plugin catalog (`sekhmet`, godspeed-core, xbrd-*, myagents, …) |
| [xbrd-selector](https://github.com/VeigaPunk/xbrd-selector) | Pure-Rust rover / model selector CLI |
| [xbrd-grok](https://github.com/VeigaPunk/xbrd-grok) | Design lineage for planner-first multi-round Godspeed |

## Design lineage

Planner-first WWKD, mandatory connector, evidence gate, Pareto frontier, and autonomous multi-round loop from `xbrd-grok`, adapted to Sol Ultra native delegation. Sekhmet is a **bounded** L3 substrate — never a recursive 64 × 64 worker tree.
