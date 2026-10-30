# beads でタスクを管理する

- タスク管理には `bd`（beads）を使う。TodoWrite や Markdown の TODO リストは使わない。
- コマンドの詳細は、セッション開始時にフックで読み込まれる `bd prime` の出力を参照する。コンテキストが失われたら `bd prime` を実行し直す。
- 着手前に Issue を作り（`bd create`）、作業中は claim し（`bd update <id> --claim`）、終わったら閉じる（`bd close <id>`）。
- 作業中に見つかった残作業や後回しにしたことは、その場で Issue にする。
- 次のセッションに引き継ぎたい知見は `bd remember` で残す。
- Issue のデータは `.beads/` 配下の Dolt データベースにある。リモートとの同期は `bd dolt push` と `bd dolt pull` で行う。`.beads/issues.jsonl` は書き出しであり、正本ではない。
- `bd edit` はエディタを開いて止まるので使わない。
