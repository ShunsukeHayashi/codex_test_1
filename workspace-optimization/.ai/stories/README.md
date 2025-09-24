# Stories ディレクトリ運用ガイド

各ストーリーはフロントマター (story_id, epic_id, status, assignee, dependencies) を持つ Markdown で管理する。
- **status**: `pending`, `in_progress`, `completed`, `blocked` のいずれかを使用。
- **dependencies**: 依存するストーリー ID を配列形式で列挙。
- ストーリー完了時は `@memory-bank.mdc` と `codex_prompt_chain.md` を更新する。

命名規則: `story_<3桁番号>_<短い英語説明>.md`
- 例: `story_003_workspace_scaffold.md`

ストーリーを更新した場合は、対応する Epic のステータスを `.ai/prd.md` で同期すること。
