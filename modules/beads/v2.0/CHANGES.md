# beads v2.0 の変更点

v1 からの差分と、v1 から上げるときの注意。

## 変更点

- SessionStart フックのコマンドを `bd prime --hook-json` から `bd prime --hook-json --memories-only` に変えた。`bd prime` の既定の出力には、終了前に `git status` で変更を確認して報告するよう命じる英語の「SESSION CLOSE PROTOCOL」が含まれており、会話の最後に beads のファイル更新の詳細が並んでノイズになっていた。`--memories-only` にすると、`bd remember` で残した知見だけが読み込まれる。
- `.claude/rules/beads.md` に「beads は裏方の記録であり、Issue の操作や `.beads/` 配下の変更はユーザーへの報告に書かない」を加えた。利用者が beads の仕組みを知らなくても、Claude Code が裏で使う状態にするため。
- 1 コミットで終わる軽微な修正は Issue を作らなくてよいことを明記した。
- コマンドの使い方は `bd prime` の出力ではなく `bd <コマンド> --help` で確認するよう改めた。`.claude/rules/` の内容は compaction 後も残るため、「コンテキストが失われたら `bd prime` を実行し直す」の指示は不要になり削った。
- Dolt モードでは生成されない `.beads/issues.jsonl` への言及を削った。

## v1 から上げるときの注意

- `.claude/settings.json` のフックは、`APPLY.md` の手順 3 で `--memories-only` 付きに書き換わる。
- `.claude/rules/beads.md` を v1 のまま改変していなければ、そのまま置き換わる。改変している場合は差分が示されるので、取り込み方を決める。
- handoff v1 を併用している場合、handoff の「最後のメッセージに Issue の ID つきで状況を書く」が本版の「報告に書かない」と矛盾する。handoff も v2.0 以降に上げること。
