# japanese v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

Claude Code とユーザーのやり取り（返答、質問、作業報告）と、コミットメッセージや Issue などユーザーが読む文面を、日本語で書くようにします。

## 前提条件

- なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. ルールファイルを配置する

`files/japanese.md` を、現在のリポジトリの `.claude/rules/japanese.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/japanese.md` が既に存在する場合は上書きせず、既存の内容と `files/japanese.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/japanese.md` が存在し、内容が `files/japanese.md` と一致している

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
japanese@v1 <今日の日付 YYYY-MM-DD>
```
