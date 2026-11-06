# claudecode-initial-settings

Claude Code 用の共通ルールを、版付きで管理して各プロジェクトに配布するためのリポジトリ（配布元）。

複数のプロジェクトで共通して使いたいルールや設定を、`~/.claude/` 配下のグローバル設定ではなく、各リポジトリの `CLAUDE.md` や `.claude/` 配下に置くための仕組み。グローバルに置くと更新がすべてのプロジェクトに即座に波及するため、版を固定して取り込めるようにしている。詳しくは [docs/requirements.md](docs/requirements.md) を参照。

## 使い方

1. ルールを取り込みたいプロジェクトのリポジトリで Claude Code を起動する。
2. 次のように指示する。`<module-name>` と `<version>` は、下のモジュール一覧にあるモジュール名と版（例: `beads` と `v2.0`）に置き換える。

```
https://github.com/yo16/claudecode-initial-settings.git を、このリポジトリの外の一時ディレクトリに clone して。clone した中にある modules/<module-name>/<version>/APPLY.md を読んで、このリポジトリに適用して。
適用が終わったら、clone した一時ディレクトリを削除して。
```

3. Claude Code が配布元を GitHub から一時ディレクトリに clone して手順を実行し、完了条件を確認して報告する。clone は適用後に削除される。内容を確認してコミットする。

配布元を手元に clone しておく必要はない。複数のモジュールを一度に指示してもよい。導入後のファイルは、各プロジェクトで自由に改変してよい。

## 新しいリポジトリの初期設定

新しいリポジトリを作ったら、そのリポジトリで Claude Code を起動して、次のプロンプトをそのまま貼り付ける。全モジュールの最新版をまとめて適用する。書き換える箇所はない。

```
https://github.com/yo16/claudecode-initial-settings.git を、このリポジトリの外の一時ディレクトリに clone して。clone した中にある次の APPLY.md を、上から順に 1 つずつ読んで、このリポジトリに適用して。
前提条件を満たさないモジュールは飛ばして次に進み、飛ばしたモジュールと理由を最後にまとめて報告して。
適用が終わったら、clone した一時ディレクトリを削除して。

- modules/japanese/v1/APPLY.md
- modules/git-autonomous/v1/APPLY.md
- modules/beads/v2.0/APPLY.md
- modules/handoff/v2.1/APPLY.md
- modules/infra-readme/v1/APPLY.md
- modules/smallpiece-link/v1/APPLY.md
```

- 貼り付ける前に、リポジトリを git で管理して push 先のリモートを設定し、`bd` 1.3.2 以上をインストールしておく。`git-autonomous` と `beads` の前提条件である。
- 要らないモジュールは、その行を消してから貼り付ける。`smallpiece-link` は、Small Piece へのリンクを置くプロジェクトだけで使う。
- 行の順番は変えない。`handoff` は、`git-autonomous` と `beads` が先に適用されていることを前提にしている。
- このプロンプトは版やモジュールを追加するたびに書き換えており、常に最新版を指している。

## モジュール一覧

| モジュール | 内容 | 最新版 |
|---|---|---|
| [japanese](modules/japanese/) | ユーザーとのやり取りを日本語で行う | v1 |
| [git-autonomous](modules/git-autonomous/) | git の add、commit、push を適切なタイミングで自律的に行う | v1 |
| [beads](modules/beads/) | beads（`bd`）でタスクを管理する | v2.0 |
| [handoff](modules/handoff/) | 停止するたびに git と beads の状態を揃え、まっさらなコンテキストから再開できるようにする | v2.1 |
| [smallpiece-link](modules/smallpiece-link/) | Small Piece（smallpiece.jp）へのリンクに GA4 用の UTM パラメータを付ける | v1 |
| [infra-readme](modules/infra-readme/) | 使用する外部サービスなど、インフラの情報を `README.md` に書いて最新に保つ | v1 |

版ごとの要約は、各モジュールの `README.md` にある。

## 導入記録

適用先の `.claude/claudecode-initial-settings-history.txt` に、導入したモジュールと版が 1 行ずつ記録される。参考情報であり、Claude Code への指示ではない。

## 保守する人へ

- 仕様: [docs/requirements.md](docs/requirements.md)
- このリポジトリでの Claude Code の使い方: [CLAUDE.md](CLAUDE.md)
- 新しい版を作るときは [templates/APPLY.template.md](templates/APPLY.template.md) をコピーして埋める。公開済みの版のディレクトリは書き換えず、新しい版を作る。
- 版は `vN.M` の形（例: `v2.0`、`v2.1`）。要素の追加など少し大きな変更は N を上げ、指示の言い回しなど小さな変更は M を上げる。初版だけ `v1` の表記で、その次は `v2.0`。
