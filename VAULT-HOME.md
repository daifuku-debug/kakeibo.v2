---
title: Vault Home
type: hub
status: active
created: 2026-04-05
updated: 2026-04-05
---

# Vault Home

このフォルダは Obsidian の Vault として使えるように構成されています。日常的にはこのページから移動してください。

## 入口ページ

- [wiki/overview.md](./wiki/overview.md) - いまの全体像
- [wiki/index.md](./wiki/index.md) - 全ページの索引
- [wiki/log.md](./wiki/log.md) - 更新履歴

## 資料投入

- `raw/inbox/` に新しい資料を入れる
- 画像や添付は `raw/assets/` に置く
- そのあと LLM に「ingest して」と依頼する

## よく使うページ

- [wiki/sources/README.md](./wiki/sources/README.md) - 情報源の要約
- [wiki/concepts/llm-wiki-pattern.md](./wiki/concepts/llm-wiki-pattern.md) - 概念ページ
- [wiki/entities/README.md](./wiki/entities/README.md) - 人物・組織・製品など
- [wiki/queries/README.md](./wiki/queries/README.md) - 質問から生まれた保存価値のある回答
- [wiki/maintenance/README.md](./wiki/maintenance/README.md) - 点検メモ
- [wiki/templates/obsidian-ingest-checklist.md](./wiki/templates/obsidian-ingest-checklist.md) - ingest の手順

## 運用ルール

- 元資料は `raw/` に置き、基本的に書き換えない
- 整理された知識は `wiki/` に蓄積する
- 大きめの質問の回答は、必要なら `wiki/queries/` に保存する
- 定期的に lint を回して、孤立ページや矛盾を検出する
