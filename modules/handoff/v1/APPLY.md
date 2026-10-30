# handoff v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

Claude Code がターンを終えて停止するとき（タスクの完了、ユーザーへの質問、続行不能）に、beads の Issue と git の状態を揃えて記録するようにします。セッションを閉じて翌日に再開しても、Issue と git の記録だけから作業を続けられるようにするためです。

## 前提条件

- `git-autonomous@v1` が適用済みであること。確認: `.claude/rules/git-autonomous.md` が存在する
- `beads@v1` が適用済みであること。確認: `.claude/rules/beads.md` が存在し、`bd info` が成功する

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. ルールファイルを配置する

`files/handoff.md` を、現在のリポジトリの `.claude/rules/handoff.md` にコピーしてください。

`.claude/rules/handoff.md` が既に存在する場合は上書きせず、既存の内容と `files/handoff.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/handoff.md` が存在し、内容が `files/handoff.md` と一致している
- [ ] `.claude/rules/git-autonomous.md` と `.claude/rules/beads.md` が存在する

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
handoff@v1 <今日の日付 YYYY-MM-DD>
```
