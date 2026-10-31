# claudecode-initial-settings

Claude Code 用の共通ルールを、版付きで管理して各プロジェクトに配布するためのリポジトリ（配布元）。

複数のプロジェクトで共通して使いたいルールや設定を、`~/.claude/` 配下のグローバル設定ではなく、各リポジトリの `CLAUDE.md` や `.claude/` 配下に置くための仕組み。グローバルに置くと更新がすべてのプロジェクトに即座に波及するため、版を固定して取り込めるようにしている。詳しくは [docs/requirements.md](docs/requirements.md) を参照。

## 使い方

1. このリポジトリを手元に clone しておく。置き場所は自由。
2. ルールを取り込みたいプロジェクトのリポジトリで Claude Code を起動する。
3. 次のように指示する。`<配布元のクローン>` は手順 1 の clone 先に、`<version>` は下のモジュール一覧にある版（例: `v1`）に置き換える。

```
<配布元のクローン>/modules/<module-name>/<version>/APPLY.md を読んで、このリポジトリに適用して
```

4. Claude Code が手順を実行し、完了条件を確認して報告する。内容を確認してコミットする。

複数のモジュールを一度に指示してもよい。導入後のファイルは、各プロジェクトで自由に改変してよい。

## モジュール一覧

| モジュール | 内容 | 最新版 |
|---|---|---|
| [japanese](modules/japanese/) | ユーザーとのやり取りを日本語で行う | v1 |
| [git-autonomous](modules/git-autonomous/) | git の add、commit、push を適切なタイミングで自律的に行う | v1 |
| [beads](modules/beads/) | beads（`bd`）でタスクを管理する | v1 |
| [handoff](modules/handoff/) | 停止するたびに git と beads の状態を揃え、まっさらなコンテキストから再開できるようにする | v1 |

版ごとの要約は、各モジュールの `README.md` にある。

## 導入記録

適用先の `.claude/claudecode-initial-settings-history.txt` に、導入したモジュールと版が 1 行ずつ記録される。参考情報であり、Claude Code への指示ではない。

## 保守する人へ

- 仕様: [docs/requirements.md](docs/requirements.md)
- このリポジトリでの Claude Code の使い方: [CLAUDE.md](CLAUDE.md)
- 新しい版を作るときは [templates/APPLY.template.md](templates/APPLY.template.md) をコピーして埋める。公開済みの版のディレクトリは書き換えず、新しい版を作る。
- 版は `vN.M` の形（例: `v2.0`、`v2.1`）。要素の追加など少し大きな変更は N を上げ、指示の言い回しなど小さな変更は M を上げる。初版だけ `v1` の表記で、その次は `v2.0`。
