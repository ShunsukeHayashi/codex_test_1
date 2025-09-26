# ディレクトリ移行計画

更新日: 2025-09-26
作成フェーズ: Phase 1 (Scaffold) / Phase 2 (Planning)

## 基本方針
- 作業はフェーズ単位で実行し、各フェーズ完了後に `@memory-bank.mdc` へ結果を反映する。
- Git 管理下のプロジェクトは移動後に `git status` を確認し、IDE のワークスペース設定を更新する。
- 破壊的操作（削除・上書き）は実行前にバックアップを取得する。
- 分類は `docs/classification_policy.md` に従い、例外は本書に記録する。

## フェーズ別ステップ
### Phase 0: 事前準備
1. `~/workspace/` の存在確認と作成 (STORY-003)。
2. 現状ディレクトリ一覧を `docs/inventory.md` に追記 (STORY-001)。
3. カテゴリ分類ポリシーの策定 (STORY-002)。

### Phase 1: スキャフォールディング
1. `~/workspace/{active,incubate,archive,learning,tools,data}` を生成。
2. 各カテゴリ README テンプレートを作成し、運用ルールを記載。
3. バックアップ戦略を選定 (TimeMachine or 手動スナップショット)。

### Phase 2: 移行計画の確定
1. 各リポジトリについて移動先を確定し、下記マッピング表を更新。
2. Git リモート・CI・スクリプト上のパス依存を洗い出す (`rg`, `git remote -v`)。
3. 移行手順書 (本書) とチェックリストを完成させ、ユーザー承認を得る。

### Phase 3: 実行
1. 低リスクなリポジトリから順に移動 (`mv` または `rsync`)。
2. 移動後に `git status`・`git remote -v` を確認。
3. 必要に応じて `ln -s` を用いた後方互換リンクを作成。
4. 完了後 `docs/migration_report.md` と `docs/inventory.md` を更新。

### Phase 4: 検証と最適化
1. IDE/エディタのプロジェクトリストを刷新。
2. シェルエイリアス・スクリプトの参照先を更新。
3. 不要となった旧ディレクトリをアーカイブまたは削除。
4. フィードバックを収集し、次回改善事項を `docs/post_migration_review.md` に記録。

## マッピング表 (ドラフト)
| ソースパス | 想定カテゴリ | ターゲットパス | ウェーブ | 検証チェック | ロールバック |
| --- | --- | --- | --- | --- | --- |
| `/Users/shunsuke/Dev/dify_workflow_gen_mcp` | active | `~/workspace/active/dify_workflow_gen_mcp` | Wave 1 | `pytest`, `git status` | `mv` で元位置へ戻す |
| `/Users/shunsuke/Dev/AI_entrepreneur_Agent` | incubate | `~/workspace/incubate/AI_entrepreneur_Agent` | Wave 2 | `npm test` (該当時) | 手動バックアップから復元 |
| `/Users/shunsuke/tools/github-mcp-server` | tools | `~/workspace/tools/github-mcp-server` | Wave 1 | `go test ./...` | `rsync` バックアップから戻す |
| `/Users/shunsuke/Dev/test_codex_Tetris` | archive | `~/workspace/archive/test_codex_Tetris` | Wave 3 | `git status` | ZIP バックアップ |
| `/Users/shunsuke/go/pkg` | data | `~/workspace/data/go/pkg` | Wave 2 | `go env GOPATH` | `rsync --delete` |
| ... | ... | ... | ... | ... | ... |

## ウェーブ構成 (テンプレート)
| Wave | 対象 | 目的 | 予定日 | 担当 | 状態 |
| --- | --- | --- | --- | --- | --- |
| Wave 1 | active/tools の高優先度プロジェクト | 日常開発影響の最小化 | *(未定)* | *(未定)* | pending |
| Wave 2 | incubate/data | PoC 継続とデータ整理 | *(未定)* | *(未定)* | pending |
| Wave 3 | archive/learning | 参照資産の統合 | *(未定)* | *(未定)* | pending |

## チェックリスト
- [ ] `~/workspace` の作成と README 配置
- [ ] マッピング表の全行がレビュー済み
- [ ] 各ウェーブの検証手順がドキュメント化
- [ ] ロールバック手順がテスト済み
- [ ] `docs/migration_report.md` のテンプレートを用意

## リスクと対策
| リスク | 対応策 |
| --- | --- |
| Git リポジトリ移動に伴うリモート URL 変更 | 移行後に `git remote -v` を確認し、必要なら `git remote set-url` |
| IDE が旧パスを参照 | VS Code 等でワークスペース設定を更新 |
| スクリプトのハードコードされたパス | `rg '/Users/shunsuke/Dev'` で検出し、環境変数ベースに修正 |
| 権限問題 | 移行前に所有者・権限を確認 (`stat`) |

## 承認欄
- 承認者: ____________________
- 日付: ____________________
- コメント:
  - 

## 変更履歴
- 2025-09-26: 初版テンプレート化、ウェーブ構成セクションを追加。
