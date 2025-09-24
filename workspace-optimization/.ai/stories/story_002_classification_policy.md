---
story_id: STORY-002
epic_id: EPIC-001
status: pending
assignee: unassigned
dependencies: ["STORY-001"]
---

# STORY-002: カテゴリ分類ポリシーの策定

## 背景
- 棚卸し結果をもとに、各リポジトリをどのカテゴリ (active/incubate/archive/learning/tools/data) に配置するかの基準が必要。
- 一貫性のある分類がなければ移行後の運用が混乱する。

## ゴール
- 判定基準・チェックリストを含む `docs/classification_policy.md` を作成し、ユーザー承認を得る。
- 各カテゴリに代表例を紐付け、例外処理方針を明記する。

## スコープ
- 棚卸しデータの分析。
- カテゴリ定義、判定フロー (yes/no チャート) の文書化。
- 例外 (複数カテゴリに跨るケース) の処理指針策定。

## 成果物
- 新規 `docs/classification_policy.md`。
- @memory-bank.mdc への決定事項追記。

## 受け入れ条件
- [ ] 各カテゴリの定義、判定基準、優先度が明文化されている。
- [ ] 判定チェックリストが作成されている。
- [ ] 例外処理ポリシーが記述されている。
- [ ] ユーザーがレビューし、承認コメントを残している。

## テスト戦略
- STORY-001 の棚卸しデータを用いてサンプル分類を実施し、想定通りにカテゴリへ割り当てられることを確認。
- Markdown プレビューで図表やリストが正しく表示されるか確認。

## ログ要件
- codex_prompt_chain.md に判定プロセスを記録。
- tool_invocations.log に追加の調査コマンド (例: `rg`, `git remote -v`) を追記。
