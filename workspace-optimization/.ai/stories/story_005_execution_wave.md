---
story_id: STORY-005
epic_id: EPIC-003
status: pending
assignee: unassigned
dependencies: ["STORY-004"]
---

# STORY-005: 移行ウェーブ実行と検証

## 背景
- 計画策定後、実際にディレクトリを移動し、CI・IDE・スクリプトが期待通り動作するか確認する必要がある。
- 失敗時のロールバックやログ記録を徹底し、再現性を確保する。

## ゴール
- `docs/migration_plan.md` で定義した各ウェーブを実行し、検証ログと結果を `docs/migration_report.md` (新規) に記録する。
- Git リモート、依存ツール、エイリアスなどの設定が新ディレクトリで正しく動作することを確認する。

## スコープ
- shell コマンド `mv`, `rsync`, `ln -s` を用いた移行操作。
- `git status`, `git remote -v`, `pipenv`, `npm` などの検証コマンド実行。
- ロールバック手順の検証 (サンドボックスでリハーサル)。

## 成果物
- `docs/migration_report.md` にウェーブごとの実施結果を記録。
- `.ai/logs/tool_invocations.log` に実行コマンドを追記。
- @memory-bank.mdc にストーリー完了ログを追加。

## 受け入れ条件
- [ ] 各ウェーブの移行ログ (開始/終了時刻、コマンド、結果) が `docs/migration_report.md` に記録されている。
- [ ] `git status` がクリーンであり、リモートも正しく設定されている。
- [ ] 代表的なツール/スクリプトが新パスで動作確認済み。
- [ ] ロールバック手順がテストされ、成功ログがある。

## テスト戦略
- ウェーブ実行後、対象リポジトリで単体テストやビルドを実行。
- `rg` で旧パス参照が残っていないか確認。

## ログ要件
- 実行コマンドをすべて tool_invocations.log に記録。
- 失敗時は原因分析と再試行結果を codex_prompt_chain.md / handoff_summary.md に残す。
