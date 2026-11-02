# beads

beads（`bd` コマンド）でタスクを管理するための初期化と、Claude Code 向けの運用ルール。

## 版

| 版 | 要約 |
|---|---|
| v1 | `bd init --skip-agents` で初期化し、`.claude/settings.json` に SessionStart フック（`bd prime --hook-json`）を加え、日本語の運用ルールを `.claude/rules/beads.md` に置く。英語の AGENTS.md や Codex、Cursor 向けのファイルは作らせない |
| v2.0 | SessionStart フックを `bd prime --hook-json --memories-only` にして `bd remember` の知見だけを読み込み、運用ルールに「beads は裏方の記録であり、Issue の操作や `.beads/` の変更はユーザーへの報告に書かない」と「1 コミットで終わる軽微な修正は Issue を作らなくてよい」を加えた。会話の最後に beads のファイル更新の詳細が並ぶノイズをなくす |
