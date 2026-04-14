# LLM Wiki 運用スキーマ

このワークスペースには、エージェントが継続的に保守する永続的な Markdown Wiki があります。

## 目的

この Wiki は、生の資料とユーザー向けの回答のあいだにある知識レイヤーです。`raw/` の資料は不変のソースとして扱い、`wiki/` のページは更新可能な蓄積物として育てます。

## ディレクトリ構成

- `raw/inbox/`: ingest 待ちの新しい source を置く場所
- `raw/assets/`: raw source から参照される画像や添付ファイル
- `VAULT-HOME.md`: Obsidian で日常的に開く入口ページ
- `wiki/index.md`: wiki 全体の索引
- `wiki/log.md`: append-only の時系列ログ
- `wiki/overview.md`: ドメイン全体の上位レベル整理
- `wiki/sources/`: ingest 済み source ごとのページ
- `wiki/entities/`: 人物、組織、製品、場所、プロジェクト、ツールなどのページ
- `wiki/concepts/`: 概念、テーマ、手法、主張などのページ
- `wiki/queries/`: 質問から生まれた保存価値のある回答
- `wiki/maintenance/`: lint レポート、ギャップ分析、保守メモ
- `wiki/templates/`: ページテンプレートや ingest 手順

## 運用ルール

1. `raw/` 配下は、ユーザーが新しい source を追加する場合を除いて書き換えない。
2. wiki を読むときはまず `wiki/index.md` から入り、必要なページだけ深掘りする。
3. source を ingest するとき:
   - source を読む。
   - `wiki/sources/` に source ページを作るか更新する。
   - 関連する entity と concept ページを更新する。
   - 必要なら `wiki/overview.md` を更新する。
   - `wiki/index.md` を更新する。
   - `wiki/log.md` に 1 件追記する。
4. 大きめの質問に答えるとき:
   - 先に関係する wiki ページを読む。
   - 使ったページを明示して答える。
   - 保存価値がある回答なら `wiki/queries/` に保存し、索引とログも更新する。
5. 保守作業をするとき:
   - 矛盾、古い主張、孤立ページ、弱い相互リンク、抜けているページ候補を探す。
   - 発見事項を `wiki/maintenance/` に記録する。
   - `wiki/log.md` に記録する。

## ページ記述ルール

- Markdown のみを使う。
- セクションは短く保ち、関連ページへのリンクを明示する。
- ツール互換性のため標準 Markdown リンクを優先するが、必要なら本文や frontmatter で Obsidian の wikilink を使ってよい。
- 主張は `wiki/sources/` の該当ページに結びつける。
- 新しい情報が古い情報を上書きする場合は、黙って置き換えず「更新・修正・反証」であることを明示する。
- ファイル名は安定した kebab-case を優先する。

## 推奨 frontmatter

必要に応じて YAML frontmatter を使います。

```md
---
title: Example Page
type: concept
status: active
created: 2026-04-05
updated: 2026-04-05
sources:
  - [[sources/example-source]]
---
```

frontmatter は必須ではありませんが、長く残すページでは `title`, `type`, `updated`, `sources` を入れるのを推奨します。

## 基本ワークフロー

### Ingest

1. `wiki/index.md` を見て関連ページを確認する。
2. raw source を読む。
3. `wiki/sources/` に source 要約を書く。
4. 影響を受ける concept/entity ページを更新する。
5. overview、index、log を更新する。

### Query

1. `wiki/index.md` を読む。
2. 関係するページだけ開く。
3. まず wiki の内容から答える。
4. 保存価値がある整理なら `wiki/queries/` に保存する。

### Lint

1. `wiki/index.md`、`wiki/overview.md`、最近のページを見直す。
2. 矛盾、古い主張、孤立ページを探す。
3. `wiki/maintenance/` に保守メモを書く。
4. ログを 1 件追加する。
