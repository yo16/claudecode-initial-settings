# handoff

Claude Code が停止するたびに git と beads の状態を揃え、翌日など、まっさらなコンテキストから作業を再開できるようにするためのルール。

## 版

| 版 | 要約 |
|---|---|
| v1 | 停止前に行う同期の手順（Issue の更新、コミット、最後の報告）と、再開時の手順を `.claude/rules/handoff.md` に置く。`git-autonomous@v1` と `beads@v1` に依存する |
