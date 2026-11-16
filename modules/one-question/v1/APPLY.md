# one-question v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

要件定義や設計などで Claude Code がユーザーに質問するとき、1 回のメッセージで尋ねる質問を 1 つだけにします。まとめて尋ねられると答えづらく、質問の意味が分からないときに聞き返しにくいためです。ユーザーが聞き返してきたら、次の質問に進まずその質問を説明します。

## 前提条件

- なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. ルールファイルを配置する

`files/one-question.md` を、現在のリポジトリの `.claude/rules/one-question.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/one-question.md` が既に存在する場合は上書きせず、既存の内容と `files/one-question.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/one-question.md` が存在し、内容が `files/one-question.md` と一致している

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
one-question@v1 <今日の日付 YYYY-MM-DD>
```
