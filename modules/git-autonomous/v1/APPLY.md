# git-autonomous v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

Claude Code が git の add、commit、push を、ユーザーの指示を待たずに自分の判断で行うようにします。コミットのタイミングと単位、メッセージの書き方、やってはいけない操作を定めます。

## 前提条件

- 現在のリポジトリが git で管理されており、push 先のリモートが設定されていること。確認: `git remote -v` で 1 つ以上のリモートが表示される
- 依存する他モジュール: なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. 既存の指示との衝突を確認する

現在のリポジトリの `CLAUDE.md` と `.claude/rules/` 配下に、「コミットは指示があるときだけ行う」「push しない」など、このモジュールと矛盾する記述がないか確認してください。

矛盾する記述があれば、その箇所をユーザーに示し、どちらを優先するか確認してください。ユーザーが既存の記述を直すと決めた場合はその指示に従って修正し、このモジュールを適用しないと決めた場合はここで中止してください。

### 2. ルールファイルを配置する

`files/git-autonomous.md` を、現在のリポジトリの `.claude/rules/git-autonomous.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/git-autonomous.md` が既に存在する場合は上書きせず、既存の内容と `files/git-autonomous.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/git-autonomous.md` が存在し、内容が `files/git-autonomous.md` と一致している
- [ ] `git remote -v` でリモートが表示される
- [ ] `CLAUDE.md` と `.claude/rules/` 配下に、このルールと矛盾する記述が残っていない

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
git-autonomous@v1 <今日の日付 YYYY-MM-DD>
```
