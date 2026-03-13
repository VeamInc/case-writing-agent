# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

Harvard Business School スタイルのケーススタディを作成・検証・授業シミュレーションするエージェントシステム。

## ワークフロー

5つのサブエージェントが順番に連携する。**ステップ1のみ自動実行**、ステップ2以降はユーザー確認後に次へ進む。

```
Step 1: case-theme-finder     → テーマ候補を自動検索・提案
         ↓ [ユーザー承認]
Step 2: case-question-designer → ケースクエスチョン策定
         ↓ [ユーザー承認]
Step 3: case-writer            → ケース本文の執筆
         ↓ [ユーザー承認]
Step 4: case-evaluator         → Harvard基準での品質検証
         ↓ [ユーザー承認]
Step 5: class-simulator        → 授業シミュレーション実行
```

## エージェント呼び出し方法

```
# 全フローを開始（ステップ1から自動スタート）
"ケース作成を始めたい。テーマ: [テーマヒント]"

# 特定ステップから開始
"case-theme-finder で [トピック] のテーマを探して"
"case-question-designer でクエスチョンを作って"
"case-writer でケースを書いて"
"case-evaluator で評価して"
"class-simulator で授業シミュレーションして"
```

## ファイル構成規則

```
cases/
└── {case-slug}/
    ├── theme.md          # テーマ・背景情報（Step 1出力）
    ├── questions.md      # ケースクエスチョン（Step 2出力）
    ├── case.md           # ケース本文（Step 3出力）
    ├── evaluation.md     # 評価レポート（Step 4出力）
    └── simulation.md     # 授業シミュレーション（Step 5出力）

case-writing/
└── CLAUDE.md
```

> **注意**: casesフォルダの保存先は `cases/` (ワークスペース直下)

## エージェント定義

詳細は `AGENTS.md` を参照。

## ユーザー確認プロトコル

ステップ2〜5では、各エージェント完了後に必ず以下を提示する:

```
✅ [ステップ名] 完了

[成果物のサマリー]

次のステップ: [次のエージェント名と処理内容]
進めてよいですか？ (yes / 修正事項を入力)
```
