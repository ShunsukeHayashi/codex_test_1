---
story_id: STORY-001
epic_id: EPIC-001
status: pending
assignee: unassigned
dependencies: []
---

# STORY-001: 現状ディレクトリ棚卸しの完全化

## 背景
- `docs/inventory.md` にはトップレベルの一覧のみが記録されており、更新日や容量などの重要指標が欠落している。
- 正確な棚卸しが無ければ、分類ポリシーや移行計画の信頼性が損なわれる。

## ゴール
- 対象ルート (`/Users/shunsuke/Dev`, `/Users/shunsuke/projects`, `/Users/shunsuke/tools`, `/Users/shunsuke/go`) の各ディレクトリについて、更新日・サイズ・主要用途を記録する。
- 棚卸し結果を `docs/inventory.md` に整理し、チェックリストを完了させる。

## スコープ
- shell コマンド (`ls`, `du`, `stat`) によるメタデータ取得。
- ドキュメント更新と差分レビュー。
- 必要に応じてスクリーンショットや補助ファイルを `docs/attachments/` に配置。

## 成果物
- 更新済み `docs/inventory.md`。
- 解析メモ (必要であれば `.ai/logs/` 内の補助ログ)。
- @memory-bank.mdc の進捗更新。

## 受け入れ条件
- [ ] 対象ディレクトリの更新日と容量が `docs/inventory.md` に記録されている。
- [ ] 棚卸し結果に基づき、優先移行候補がラベル付けされている。
- [ ] `git diff docs/inventory.md` で内容が確認・承認されている。

## テスト戦略
- shell コマンドの出力を `tool_invocations.log` に保存し、数値の再現性を確保。
- ドキュメント整形後に Markdown リンター (必要に応じて) を実行。

## ログ要件
- codex_prompt_chain.md: STORY-001 の intent から verification まで記録。
- tool_invocations.log: 実行したメタデータ取得コマンドをすべて登録。
