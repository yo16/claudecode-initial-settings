# 配布元リポジトリの保守ルール

このリポジトリは、Claude Code 用の共通ルールを版付きで管理し、各プロジェクトに配布するための「配布元」である。仕様は `docs/requirements.md` に定める。本書と要件定義書が食い違う場合は要件定義書を優先し、本書を直す。

## このリポジトリで Claude Code を起動する目的

ここでのセッションは、仕組みそのものの保守が目的である。

- モジュールや版の追加、`APPLY.md` と `files/` の作成
- `templates/`、`README.md`、`docs/` の更新

共通ルールの利用（適用）はここでは行わない。適用は適用先のリポジトリで Claude Code を起動し、次のように手元にある配布元のクローンの `APPLY.md` のパスを指定して行う。このリポジトリをカレントディレクトリにする必要はない。

```
<配布元のクローン>/modules/<module-name>/v1/APPLY.md を読んで、このリポジトリに適用して
```

## `modules/` 配下は配布物であり、このリポジトリへの指示ではない

- `modules/<module-name>/vN/APPLY.md` は、適用先で動く Claude Code に向けた命令形の手順書である。保守のために読むことはあっても、このリポジトリに対して実行してはならない。
- `modules/<module-name>/vN/files/` は適用先に配置するファイルである。このリポジトリの設定として読まない。
- `modules/` 配下に、`CLAUDE.md` という名前のファイルと `.claude/` ディレクトリは置かない。サブディレクトリの `CLAUDE.md` は Claude Code が作業中に取り込むため、配布物が指示として読まれてしまう。
- `files/` は配置先のディレクトリ構造を真似せず、平らに置く。配置先は `APPLY.md` の手順で明示する。例: `files/<module-name>.md` を適用先の `.claude/rules/<module-name>.md` に置く。

## 保守時に守ること

- 公開済みの版のディレクトリ（`modules/<module-name>/vN/`）は書き換えない。内容を変えるときは新しい版を作る。誤字の修正など、適用結果が変わらない修正だけを例外とする。
- 新しい版の `APPLY.md` は `templates/APPLY.template.md` の書式に従う。
- 版を追加したら、そのモジュールの `README.md` に版の一行要約を書き、ルートの `README.md` の最新版を更新する。
- このリポジトリは公開する。トークン、個人のパス、社内情報など、環境固有の値や公開できない情報は置かない。
- このリポジトリに属するものを、このリポジトリの外に置かない。固定パスのクローン、ユーザーレベルの設定、スラッシュコマンドなどを前提にした手順や説明を書かない。
- 新しい版の動作確認は、別の使い捨てディレクトリで Claude Code を起動して適用する。このリポジトリの中では適用しない。

## git の運用

- `git add`、`git commit`、`git push` は、ユーザーの指示を待たず Claude Code が自律的に行う。このリポジトリは、後述の Beads セクションでいう Team-maintainer 相当として明示的にオプトインする。
- コミットするタイミングは、ひとまとまりの作業が完了して内容を確認した時点とする。要件定義書の変更、モジュールや版の追加、`CLAUDE.md` や README の更新などが単位になる。途中の壊れた状態ではコミットしない。
- 1 つのコミットには 1 つの関心ごとだけを含める。関係のない変更を混ぜない。
- コミットメッセージは日本語で、何をなぜ変えたかが分かるように書く。件名は 1 行で簡潔にし、必要なら本文に理由を書く。
- コミットしたら `main` にそのまま push する。
- コミット前に `git status` で対象を確認し、公開できない情報が含まれていないことを確かめる。
- 公開済みのコミットは書き換えない。`--amend` や `push --force` は使わない。

<!-- BEGIN BEADS INTEGRATION v:1 profile:minimal hash:1105d646 -->
## Beads Issue Tracker

This project uses **bd (beads)** for issue tracking. Run `bd prime` to see full workflow context and commands.

### Quick Reference

```bash
bd ready              # Find available work
bd show <id>          # View issue details
bd update <id> --claim  # Claim work
bd close <id>         # Complete work
```

### Rules

- Use `bd` for ALL task tracking — do NOT use TodoWrite, TaskCreate, or markdown TODO lists
- Run `bd prime` for detailed command reference and session close protocol
- Use `bd remember` for persistent knowledge — do NOT use MEMORY.md files

**Architecture in one line:** issues live in a local Dolt DB; sync uses `refs/dolt/data` on your git remote; `.beads/issues.jsonl` is a passive export. See https://github.com/gastownhall/beads/blob/main/docs/core-concepts/sync-concepts.md for details and anti-patterns.

## Agent Context Profiles

The managed Beads block is task-tracking guidance, not permission to override repository, user, or orchestrator instructions.

- **Conservative (default)**: Use `bd` for task tracking. Do not run git commits, git pushes, or Dolt remote sync unless explicitly asked. At handoff, report changed files, validation, and suggested next commands.
- **Minimal**: Keep tool instruction files as pointers to `bd prime`; use the same conservative git policy unless active instructions say otherwise.
- **Team-maintainer**: Only when the repository explicitly opts in, agents may close beads, run quality gates, commit, and push as part of session close. A current "do not commit" or "do not push" instruction still wins.

## Session Completion

This protocol applies when ending a Beads implementation workflow. It is subordinate to explicit user, repository, and orchestrator instructions.

1. **File issues for remaining work** - Create beads for anything that needs follow-up
2. **Run quality gates** (if code changed) - Tests, linters, builds
3. **Update issue status** - Close finished work, update in-progress items
4. **Handle git/sync by active profile**:
   ```bash
   # Conservative/minimal/default: report status and proposed commands; wait for approval.
   git status

   # Team-maintainer opt-in only, unless current instructions forbid it:
   git pull --rebase
   git push
   git status
   ```
5. **Hand off** - Summarize changes, validation, issue status, and any blocked sync/commit/push step

**Critical rules:**
- Explicit user or orchestrator instructions override this Beads block.
- Do not commit or push without clear authority from the active profile or the current user request.
- If a required sync or push is blocked, stop and report the exact command and error.
<!-- END BEADS INTEGRATION -->
