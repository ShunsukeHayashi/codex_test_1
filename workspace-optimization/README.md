# Workspace Optimization Project

## 概要
`/Users/shunsuke` 配下に散在している開発用ディレクトリ・ツール・アーカイブを整理し、再利用性と保守性を高めるためのプロジェクト。安全な手順の文書化と段階的なディレクトリ移行を LDD ベースで実行する。

## プロジェクトガバナンス
- `.ai/prd.md`: プロダクト要求仕様と KPI 管理。
- `.ai/arch.md`: 情報アーキテクチャとワークフロー定義。
- `.ai/stories/`: Epic/Story 単位の実行ガイド。
- `.ai/logs/`: codex_prompt_chain, tool_invocations, handoff_summary を保管。
- `@memory-bank.mdc`: 引き継ぎメモと決定事項の記録。

## 目的
- 開発中プロジェクトとアーカイブ済みコンテンツを分離し、参照性を向上させる。
- ツール系リポジトリを一箇所に集約してメンテナンスを容易にする。
- `~/workspace` 配下に統一的な構造を構築し、今後の追加プロジェクトにも適用できるテンプレートを用意する。

## 想定ディレクトリ構造 (ドラフト)
```
~/workspace/
  active/
  incubate/
  archive/
  learning/
  tools/
  data/
```
- `active/`: 現在開発・運用中のリポジトリ。
- `incubate/`: 検証段階のPoCや短期タスク。
- `archive/`: 保守終了または参照用の成果物。
- `learning/`: 学習素材・教材リポジトリ。
- `tools/`: 補助ツール・共通モジュール。
- `data/`: 言語ごとのワークスペースや共有データ (`go/` など)。

## タスク一覧
1. 現状ディレクトリの棚卸し (`inventory`)
2. カテゴリ判定ポリシーの確定 (`classification-policy`)
3. `~/workspace/` 作成と基本構造の生成 (`scaffold-workspace`)
4. 移行対象毎のムーブ計画策定 (`migration-plan`)
5. 実移行と Git リモート・IDE 設定の更新 (`execution`)
6. 事後検証とドキュメント更新 (`post-migration-review`)

## ロードマップ
| フェーズ | 対象タスク | 成果物 |
| --- | --- | --- |
| Phase 0 | `inventory`, `classification-policy` | `docs/inventory.md`, `docs/classification_policy.md` |
| Phase 1 | `scaffold-workspace`, `migration-plan` | `~/workspace` スキャフォールディング, `docs/migration_plan.md` |
| Phase 2 | `execution` | `docs/migration_report.md`, 移行ログ |
| Phase 3 | `post-migration-review` | `docs/post_migration_review.md`, 改善提案 |

## ドキュメント構成
- `README.md`: プロジェクト概要とタスク一覧（本ファイル）
- `.ai/`: プロジェクト管理ドキュメント、ストーリーファイル、ログテンプレート
- `docs/inventory.md`: 現状のディレクトリと分類結果テンプレート
- `docs/classification_policy.md`: カテゴリ定義と判定フロー
- `docs/migration_plan.md`: 移行準備・計画手順書
- `docs/migration_report.md`: 実移行ログ・検証結果
- `docs/post_migration_review.md`: 移行後レビューと改善提案
- `docs/attachments/`: 補助資料 (スクリーンショット等)

## 次のアクション
1. `docs/inventory.md` に詳細な棚卸し結果を記録する (STORY-001)。
2. `docs/classification_policy.md` を検討し承認する (STORY-002)。
3. 承認後、段階的にディレクトリ移動を実施する (STORY-003 以降)。

