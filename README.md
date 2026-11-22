# lib-tag

The `tag` package source, vendored by `plugin-lib-tag`.

The package surface is pure `.hnl`: consumers copy `pkg.hnl` +
`src/**/*.hnl` via `handl-pkg-vendor` into `OUT_DIR` and embed them with
`include_str!` at their own build time (`plugin-lib-tag` does this — the
`handl-lib-tag` crate's `TAG_HNL` const is no longer consumed).

`Cargo.toml` + `src/lib.rs` are retained **only** as a manifest shim:
cargo eagerly validates every `[patch]` path entry (even unused ones),
so the manifest must keep satisfying `handl-lib-tag` patches across
the workspace repos until the org-wide patch sweep removes them. They
will be deleted together with those patch entries.

## Layout

```text
src/index.hnl   the .hnl source (pure handl)
src/lib.rs      const shim — pending patch sweep (see above)
pkg.hnl         package manifest — modules, deps, description, license
scripts/hnl-gate.sh   the gate
ci.sh           bupha entry
```

## Gate

```bash
HNL=../host-cli/target/debug/hnl scripts/hnl-gate.sh
```

## License

MIT.
