# smallpiece-link v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

Small Piece（https://smallpiece.jp/）へのリンクを置くとき、GA4 で流入元が分かるように `utm_source=<サービス名>&utm_medium=referral` の形にするルールを `.claude/rules/smallpiece-link.md` に置きます。サービス名はリポジトリごとに違うので、適用時にユーザーに確認してファイルに埋めます。

## 前提条件

- 依存する他モジュール: なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. `utm_source` に使うサービス名を決める

ユーザーの指示にサービス名が含まれていれば、それを使ってください。含まれていなければ、現在のリポジトリのディレクトリ名を英小文字とハイフンに直したものを候補として示し、ユーザーに確認してください。確認が取れるまで手順 2 に進まないでください。

サービス名は英小文字、数字、ハイフンだけで書きます（例: `my-service`）。

### 2. ルールファイルを配置する

`files/smallpiece-link.md` を、現在のリポジトリの `.claude/rules/smallpiece-link.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

コピーしたファイルの中にある `<サービス名>` を、すべて手順 1 で決めた値に置き換えてください。

`.claude/rules/smallpiece-link.md` が既に存在する場合は上書きせず、既存の内容と `files/smallpiece-link.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `.claude/rules/smallpiece-link.md` が存在し、`<サービス名>` を手順 1 の値に置き換えた以外は `files/smallpiece-link.md` と一致している
- [ ] `.claude/rules/smallpiece-link.md` に `<サービス名>` という文字列が残っていない
- [ ] ユーザーへの報告に、`utm_source` に使う値を含めている

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
smallpiece-link@v1 <今日の日付 YYYY-MM-DD>
```
