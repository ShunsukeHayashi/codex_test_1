# Logs ディレクトリ運用ガイド

このディレクトリはログ駆動開発 (LDD) の証跡を一元管理するために使用する。

## 管理ファイル
- `codex_prompt_chain.md`: intent/plan/implementation/verification を時系列で追記。
- `tool_invocations.log`: 実行コマンド、作業ディレクトリ、タイムスタンプ、ステータス、補足メモを TSV 形式で記録。
- `handoff_summary.md`: 作業引き継ぎ時の要点と未完了タスクを整理。

## 記録ルール
1. 各ストーリー開始時に codex_prompt_chain の intent エントリを追加する。
2. コマンド実行直後に tool_invocations.log へ追記し、失敗時は原因と再現手順を明記する。
3. 他エージェントへ引き渡す前に handoff_summary.md に現在状況と推奨次手を記載する。
4. ログファイルが肥大化した場合でも削除せず、必要に応じて YYYY-MM-DD アーカイブを作成する。

## テンプレート
```
### codex_prompt_chain.md
intent: "STORY-001 — ディレクトリ棚卸しの完了"
plan:
  - "ls -1 /Users/shunsuke/Dev"
implementation:
  - "docs/inventory.md を更新"
verification:
  - "git diff を確認"

### tool_invocations.log (TSV)
2025-09-26T10:32:11Z	ls -1 /Users/shunsuke/Dev	/Users/shunsuke/Dev/workspace-optimization	passed	棚卸し対象の初期確認
```

## 注意事項
- 秘密情報 (API キー、トークン) はログに記載しない。
- 失敗ログを削除せず、原因と再試行結果を追記してトレーサビリティを確保する。
