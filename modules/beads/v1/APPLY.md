# beads v1

> この文書は Claude Code が読んで実行する導入手順書です。
> 現在のリポジトリに対して、以下の手順を上から順に実行してください。
> 既存のファイルや設定と衝突する場合は、上書きせずユーザーに確認してください。

## 概要

beads（`bd`）を現在のリポジトリで初期化し、Claude Code がタスク管理に beads を使うようにします。セッション開始時に `bd prime` の内容が自動で読み込まれるようフックを設定し、運用ルールを `.claude/rules/beads.md` に置きます。

## 前提条件

- `bd` がインストールされており、バージョンが 1.3 以上であること。確認: `bd --version`
- 現在のリポジトリが git で管理されていること。確認: `git rev-parse --is-inside-work-tree` が `true` を返す
- 依存する他モジュール: なし

前提条件を満たさない場合は、手順に進まずユーザーに報告してください。

## 手順

### 1. 初期化済みかを確認する

現在のリポジトリに `.beads/` ディレクトリがあれば、beads は初期化済みです。その場合は手順 2 を飛ばし、その旨をユーザーに伝えてから手順 3 に進んでください。

### 2. beads を初期化する

次のコマンドを実行してください。

```
bd init --skip-agents
```

`--skip-agents` を付けるのは、`bd init` が既定で生成する英語の `AGENTS.md`、`CLAUDE.md` への追記、Codex と Cursor 向けのファイルを作らせないためです。Claude Code 向けの設定は手順 3 と 4 で日本語で用意します。

このコマンドは次のことを行います。実行後、結果をユーザーに報告してください。

- `.beads/` を作成し、埋め込みの Dolt データベースを初期化する
- `.gitignore` に beads 関連の除外設定を追記する。既存の `.gitignore` があれば末尾に追記される
- git フックを `.beads/hooks/` に置き、このリポジトリの `core.hooksPath` をそこに向ける
- **`.beads/` と `.gitignore` を自動で git にコミットする。** コミットメッセージは `bd init: initialize beads issue tracking`
- git の `origin` が設定されていれば、Dolt の同期先として同じリモートを設定する。`origin` がなければ警告が出るが、ローカルでの利用には支障ない

Issue の接頭辞は、既定どおりディレクトリ名になります。変更したい場合は、適用後にユーザーが `bd rename-prefix` で変えられます。

### 3. SessionStart フックを設定する

`.claude/settings.json` に、セッション開始時に `bd prime --hook-json` を実行するフックを加えてください。

`.claude/settings.json` がない場合は、次の内容で作成してください。`.claude/` ディレクトリがなければ作成してください。

```json
{
  "hooks": {
    "SessionStart": [
      {
        "matcher": "",
        "hooks": [
          {
            "type": "command",
            "command": "bd prime --hook-json"
          }
        ]
      }
    ]
  }
}
```

既にある場合は、既存の内容をすべて残したまま、`hooks.SessionStart` の配列に上の要素を 1 つ追加してください。`hooks` や `SessionStart` のキーがなければ作ってください。既に `bd prime` を実行するフックが含まれていれば、追加せずそのままにしてください。

このフックは Claude Code を再起動すると有効になります。その旨をユーザーに伝えてください。

### 4. ルールファイルを配置する

`files/beads.md` を、現在のリポジトリの `.claude/rules/beads.md` にコピーしてください。`.claude/rules/` ディレクトリがなければ作成してください。

`.claude/rules/beads.md` が既に存在する場合は上書きせず、既存の内容と `files/beads.md` の差分をユーザーに示して、どうするか確認してください。

## 完了条件

適用後、次をすべて確認し、結果をユーザーに報告してください。

- [ ] `bd info` が成功し、表示されるデータベースのパスが現在のリポジトリの `.beads/` 配下を指している
- [ ] `.claude/settings.json` の `hooks.SessionStart` に、`bd prime --hook-json` を実行するフックが 1 つだけ含まれており、もともとあった設定が失われていない
- [ ] `.claude/rules/beads.md` が存在し、内容が `files/beads.md` と一致している
- [ ] `AGENTS.md`、`.codex/`、`.cursor/`、`.agents/` が、このモジュールの適用によって新たに作られていない
- [ ] 手順 2 を実行した場合、`git log --oneline -1` に `bd init` のコミットがある

## 導入記録

`.claude/claudecode-initial-settings-history.txt` の末尾に次の 1 行を追記してください。ファイルがなければ、先頭行に `# claudecode-initial-settings の導入記録。Claude Code への指示ではない。` を書いて作成してください。

```
beads@v1 <今日の日付 YYYY-MM-DD>
```
