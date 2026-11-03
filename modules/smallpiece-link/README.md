# smallpiece-link

Small Piece（https://smallpiece.jp/）へのリンクを置くとき、GA4 で流入元が分かるように UTM パラメータを付けるためのルール。

## 版

| 版 | 要約 |
|---|---|
| v1 | リンクの形（`utm_source=<サービス名>&utm_medium=referral`。設置場所を分けたいときだけ `utm_content` を足す）を `.claude/rules/smallpiece-link.md` に置く。サービス名は適用時にユーザーに確認して埋める |
