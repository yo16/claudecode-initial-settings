# beads

beads（`bd` コマンド）でタスクを管理するための初期化と、Claude Code 向けの運用ルール。

## 版

| 版 | 要約 |
|---|---|
| v1 | `bd init --skip-agents` で初期化し、`.claude/settings.json` に SessionStart フック（`bd prime --hook-json`）を加え、日本語の運用ルールを `.claude/rules/beads.md` に置く。英語の AGENTS.md や Codex、Cursor 向けのファイルは作らせない |
