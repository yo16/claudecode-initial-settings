# handoff v3.0

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

Claude Code がターンを終えて停止するとき（タスクの完了、ユーザーへの質問、続行不能）に、beads の Issue と git の状態を揃えて記録するようにします。セッションを閉じて翌日に再開しても、Issue と git の記録だけから作業を続けられるようにするためです。あわせて、停止点ではないところで止まらないようにします。依頼の目的に至る残りの手順が明らかで、ユーザーの判断を要しないなら、「次に〜ができます」と書いて止まらず続けて進めます。最後のメッセージには作業の成果とユーザーに求めることだけを書き、求めることがなければ「確認や操作は不要」と明記します。Issue の詳細は note に残します。

## 前提条件

- `git-autonomous@v1` 以降が適用済みであること。確認: `.claude/rules/git-autonomous.md` が存在する
- `beads@v2.0` 以降が適用済みであること。確認: `.claude/rules/beads.md` が存在し、その中に「裏方」という語が含まれる（beads v1 のルールには含まれない）。`bd info` が成功する

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. ルールファイルを配置する

`files/handoff.md` を、現在のリポジトリの `.claude/rules/handoff.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/handoff.md` が既に存在する場合は、次のように扱ってください。

- 既存の内容が handoff v1 の `../v1/files/handoff.md`、handoff v2.0 の `../v2.0/files/handoff.md`、または handoff v2.1 の `../v2.1/files/handoff.md` と一致している（ローカルで改変されていない）場合は、`files/handoff.md` で置き換えてください。置き換えたことをユーザーに報告してください。
- どれとも一致しない場合は上書きせず、既存の内容と `files/handoff.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/handoff.md` が存在し、内容が `files/handoff.md` と一致している
- [ ] `.claude/rules/git-autonomous.md` と `.claude/rules/beads.md` が存在し、`.claude/rules/beads.md` に「裏方」という語が含まれる

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
handoff@v3.0 <今日の日付 YYYY-MM-DD>
```
