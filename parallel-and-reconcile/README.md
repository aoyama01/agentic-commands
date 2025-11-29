## Reconciliation Loop の考え方による SDD

PRD → 並列生成(Design + Implementation) → Reconciliation → 反復

### 問題：Spec の欠如

問題:

- 「Spec」に相当するステップがない
- PRD から直接 Design と Implementation を生成している

懸念:

- PRD = ビジネス価値・Why/What
- Spec = 具体的な振る舞い・API 仕様
- この中間層がないと、Design が曖昧になりやすい

### 改善提案: Spec を中間層に挿入

提案フロー:

1. /review-prd → PRD を完成させる
2. /generate-spec → PRD から Spec を生成（API 仕様、DB Schema 等）
3. /dev → Spec と PRD を元に Design + Implementation

### メリット:

Spec が「実装の契約書」として機能
