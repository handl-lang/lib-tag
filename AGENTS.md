# lib-tag

The `tag` package source — tagged-value surface, host runtime
internal. Pure `.hnl`.

## Layout

| path | role |
| --- | --- |
| `src/index.hnl` | the .hnl source (pure handl) |
| `pkg.hnl` | package manifest — `modules: ["tag"]` |
| `scripts/hnl-gate.sh`, `ci.sh` | the gate / bupha entry |

## Contract

- Consumers copy `pkg.hnl` + `src/**/*.hnl` via `handl-pkg-vendor`
  into `OUT_DIR` and embed them with `include_str!`
  (`plugin-lib-tag` does this — the `handl-lib-tag` crate's
  `TAG_HNL` const is no longer consumed).
- Note: README mentions a retained `Cargo.toml`/`src/lib.rs` manifest
  shim pending an org-wide `[patch]` sweep, but the repo currently
  ships only `src/index.hnl` — no `Cargo.toml` is present.

## Verification

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.

<!-- myco:agent-awareness -->

## Agent awareness

- Session start / any work discussion: run `myco status --prompt`
  before proposing next steps — know the board first.
- User describes new work → offer to capture it (`myco todo add`,
  `issue new`, `proposal new`). Don't wait to be asked.
- Picking up a task: `myco resume <ID>` is the briefing.
- Wrapping up: `myco handoff <ID>` anything resumable; keep statuses
  honest (claimed → in-progress → blocked/done).

<!-- /myco:agent-awareness -->
