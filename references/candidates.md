# Candidates inbox

Proposed rules waiting for the writer's gate. The learning loops (harvest,
self-play, scout, aging; see `references/harvest.md` and
`references/weekly-loop.md`) write here. Nothing moves from this file into
`living-corpus.md`, `patterns.md`, or the protect list without approval, the
ingestion six-step, and the eval gate.

## Entry format

```
### <short-name> [status: proposed | approved | rejected | filed]

- Found: YYYY-MM-DD  |  Loop: harvest | self-play | scout | aging
- Evidence: "<the quoted span, or the diff hunk>"
- Source: <ledger file / detector round / URL>
- Proposed rule: <one-line directive + suggested tier>
- Mechanism guess: <ingestion taxonomy tag>
```

Aging proposals use the same block with `Proposed rule:` replaced by
`Proposed change: retire | re-tier <entry> because <evidence>`.

## How to process the inbox

Reply with the entry name plus `ok` (file it), `edit: <change>`, or `no`
(mark rejected, keep the entry as a record so the same candidate is not
re-proposed next round). Rejected entries are dedup targets too.

---

## Inbox

(empty)
