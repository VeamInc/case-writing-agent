# AGENTS.md

Harvard ケース作成システムのサブエージェント定義。

## エージェント一覧

| エージェント | ファイル | 役割 |
|-------------|---------|------|
| case-theme-finder | `.claude/agents/case-theme-finder.md` | テーマ探索（Web検索自動実行） |
| case-question-designer | `.claude/agents/case-question-designer.md` | ケースクエスチョン策定 |
| case-writer | `.claude/agents/case-writer.md` | ケース本文執筆 |
| case-evaluator | `.claude/agents/case-evaluator.md` | Harvard基準での品質評価 |
| class-simulator | `.claude/agents/class-simulator.md` | 授業ディスカッションシミュレーション |

## エージェント間の連携ルール

1. 各エージェントは前ステップの出力ファイルを入力として受け取る
2. ステップ1 (`case-theme-finder`) のみ自動実行。ステップ2〜5はユーザー承認待ち
3. 修正依頼を受けた場合は同じステップを再実行し、再度承認を求める
4. ユーザーが「進めて」「OK」「yes」等を返した場合のみ次ステップへ

## Harvard ケース品質基準（全エージェント共通）

- **意思決定局面**: 明確なデシジョンポイントが存在する
- **ジレンマ**: 単純な正解がなく、複数の合理的選択肢がある
- **情報の非対称性**: 読者が主人公と同じ不確実性を感じられる
- **具体性**: 実在しうる固有名詞・数値・日時が含まれる
- **議論喚起性**: クラスの45〜90分を支えられる議論の深さがある
- **教育目標の明確性**: 何を学ぶためのケースか明示されている
