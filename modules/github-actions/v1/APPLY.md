# github-actions v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

GitHub Actions の無料枠（実行時間と保存容量）は、アカウント全体で共有しています。Claude Code がワークフローを作るときと変えるときに、消費を小さく抑え、効果のあるところに絞って使うようにします。既存のワークフローは書き換えません。

## 前提条件

- なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. ルールファイルを配置する

`files/github-actions.md` を、現在のリポジトリの `.claude/rules/github-actions.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/github-actions.md` が既に存在する場合は上書きせず、既存の内容と `files/github-actions.md` の差分をユーザーに示して、どうするか確認してください。

### 2. 既存のワークフローを点検して報告する

`.github/workflows/` にワークフローがある場合は、配置したルールに照らして読み、消費を減らせる箇所をユーザーに報告してください。ファイルは書き換えないでください。直すかどうかはユーザーが決めます。

`.github/workflows/` がない場合、またはワークフローが 1 つもない場合は、この手順を飛ばしてください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/github-actions.md` が存在し、内容が `files/github-actions.md` と一致している
- [ ] `.github/workflows/` 配下のファイルが、適用の前後で変わっていない（`git status` で確認する）

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
github-actions@v1 <今日の日付 YYYY-MM-DD>
```
