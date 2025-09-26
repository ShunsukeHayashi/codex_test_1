---
story_id: STORY-003
epic_id: EPIC-002
status: pending
assignee: unassigned
dependencies: ["STORY-001", "STORY-002"]
---

# STORY-003: `~/workspace` スキャフォールディング

## 背景
- 分類ポリシーに基づき、移行先となる `~/workspace` の物理ディレクトリを事前に作成する必要がある。
- バックアップとロールバックを容易にするため、標準化された README とディレクトリ保護ルールが求められる。

## ゴール
- `~/workspace/{active,incubate,archive,learning,tools,data}` を作成し、各ディレクトリに目的と運用ルールを記載した README を配置する。
- 作成手順と検証結果を `docs/migration_plan.md` に追記する。

## スコープ
- shell コマンドでのディレクトリ作成と README テンプレート生成。
- 既存 `~/workspace` が存在する場合のバックアップまたはマージ判断。
- `docs/migration_plan.md` の更新。

## 成果物
- 作成済み `~/workspace` ディレクトリ。
- 各カテゴリ用 README テンプレート。
- 更新済み `docs/migration_plan.md`。

## 受け入れ条件
- [ ] `ls ~/workspace` で 6 ディレクトリが確認できる。
- [ ] 各ディレクトリに目的・運用ルール・サンプル格納例を記した README が存在する。
- [ ] 作業手順と検証結果が `docs/migration_plan.md` に記録されている。
- [ ] TimeMachine などバックアップ取得方法が明示されている。

## テスト戦略
- ディレクトリ作成後に `stat` で権限と所有者を確認。
- README を Markdown プレビューし、リンクが正しいことを確認。

## ログ要件
- 作成コマンドと結果を tool_invocations.log へ記録。
- 必要に応じてスクリーンショットやファイルリストをハッシュ化し、再現性を確保。
