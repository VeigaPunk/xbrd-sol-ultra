# xbrd-sol-ultra

Sol Ultra-native Godspeed orchestration modeled on [`xbrd-grok`](https://github.com/VeigaPunk/xbrd-grok), with [`Sekhmet`](https://github.com/VeigaPunk/xbrd-spark) as the layer-3 execution surface.

The root judge stays on GPT-5.6 Sol Ultra. Each round runs exactly one global Sekhmet wave with 64 concurrent workers, organized as eight task axes by eight evidence lenses. Sol owns planning, evidence gates, Pareto selection, conflict resolution, integration, and the final result.

## Runtime contract

- GPT-5.6 Sol Ultra is the only root judge.
- A native planner runs before the first L3 wave.
- Each round dispatches one `sekhmet swarm --direct -j 64` wave.
- L3 is pinned to GPT-5.6 Luna, low reasoning, fast service tier.
- The 64 tasks form an 8 × 8 axis/lens matrix; connector coverage is mandatory.
- Round 2 always runs. Rounds 3–4 run only while evidence-backed improvement remains.
- Candidates mutate isolated snapshots. One canonical writer harvests and integrates accepted artifacts.
- Evidence gates and Pareto filtering replace voting and raw-output flattening.
- Existing worktree changes are baselined and preserved; ambient dirt never counts as improvement.
- Commit, push, deploy, or other external publication happens only when the request authorizes it.

## Invoke

```text
$xbrd-sol-ultra <objective>
```

Aliases recognized by the skill include `xbsu` and `sol-ultra-godspeed`.

## Package

- `SKILL.md` — full orchestration procedure and safety contract
- `agents/openai.yaml` — display metadata and default invocation
- `assets/icon.svg` — skill icon

## Design lineage

This procedure preserves the planner-first WWKD posture, mandatory connector, evidence gate, Pareto frontier, and autonomous multi-round loop that make `xbrd-grok` effective. It adapts those ideas to Sol Ultra's native delegation while treating Sekhmet as a bounded L3 substrate—not a recursively multiplying 64 × 64 worker tree.
