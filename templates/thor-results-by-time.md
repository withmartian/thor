# Results By Time (thor-results-by-time.md)

Read role and rules: [Results Ledger](thor-document-rules.md#results-ledger).

Append each completed result bundle in chronological order. Preserve prior entries.
Record what each bundle covered and where its artifacts live — not the current
best story (that goes in `thor-results-summary.md`).

Mark exploratory or pending-review bundles explicitly; a ledger entry is not
claim approval. For concurrent writers, use dated bundle files only where the
agent contract defines their location and index; otherwise keep this ledger.

## Bundles

### `<date>` — `<bundle name>`

- **Covered**: `<models / datasets / conditions / scope>`
- **Tier / review**: `<exploratory / unreviewed, or gated with pending/reviewed status and study link>`
- **Artifacts**: `<files, plots, logs, and where they live>`
- **Caveats / coverage gaps**: `<what this bundle does not establish>`
- **Linked study / run record**: `<path relative to this ledger, e.g. study-thor/thor-study-name.md>`

### `<date>` — `<bundle name>`

- ...
