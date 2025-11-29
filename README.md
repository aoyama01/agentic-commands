# SDD Commands

SDD（Spec-Driven Development）のための Claude Code コマンド集

## このリポジトリについて

AI エージェントとの協働開発を構造化するコマンド群です。

**PRD → Spec → Design → Implementation** の流れで開発を進め、各段階で人間がレビューすることで品質を担保します。

## アプローチ

### sdd-sequential（推奨）

PRD → Spec → Design → Implementation を順番に進めるアプローチ

- 各段階で人間がレビュー可能
- トレーサビリティが明確
- 変更時の影響範囲がわかりやすい

詳細: [sdd-sequential/README.md](sdd-sequential/README.md)

### parallel-and-reconcile

PRD から並列に Design + Implementation を生成し、Reconciliation で整合性を取るアプローチ

- 実験的
- Spec の欠如による課題あり

詳細: [parallel-and-reconcile/README.md](parallel-and-reconcile/README.md)

## クイックスタート

1. 使いたいコマンドファイルを `.claude/commands/` にコピー

```bash
# sdd-sequential のコマンドを使う場合
cp sdd-sequential/*.md ~/.claude/commands/
```

2. PRD を作成

3. `/review-prd` から開始

## ディレクトリ構成

```
sdd-commands/
├── sdd-sequential/       # 順次実行型コマンド群（推奨）
│   ├── review-prd.md
│   ├── generate-spec.md
│   ├── generate-design.md
│   ├── implement.md
│   └── verify.md
├── parallel-and-reconcile/  # 並列生成型（実験的）
└── docs/
    └── concepts.md       # PRD/Spec/Design/ADR の役割整理
```

## 関連ドキュメント

- [PRD / Spec / Design Docs / ADR の役割整理](docs/concepts.md)
