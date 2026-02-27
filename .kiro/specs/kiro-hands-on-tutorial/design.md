# 設計書

## 概要

このドキュメントは、Kiroハンズオンチュートリアルプロジェクトの設計を定義します。このチュートリアルは、GitHubリポジトリとしてクローン可能な形式で提供され、ユーザーがKiroに指示を出しながら段階的に学習を進める対話型の学習体験を提供します。

### 設計目標

1. **段階的な学習体験**: 4つのレッスンで初心者から実践レベルまで段階的にスキルアップ
2. **対話型学習**: ユーザーがKiroに指示を出すことで能動的に学習
3. **実践重視**: 具体的なプロジェクトを通じてKiroの価値を体感
4. **クレジット効率**: トライアルクレジット内で基本機能を十分に体験
5. **拡張性の理解**: 有料プラン推奨機能の価値を明確に伝達

### 対象ユーザー

- プログラミング初心者を含むKiro初学者
- AI駆動開発ツールを初めて使用する開発者
- Kiroの導入を検討している個人・チーム

## アーキテクチャ

### システム構成

```
kiro-hands-on-tutorial/
├── README.md                    # クイックスタートガイド
├── docs/
│   ├── setup.md                # 環境セットアップガイド
│   ├── credits-guide.md        # クレジット制の説明
│   └── troubleshooting.md      # トラブルシューティング
├── lessons/
│   ├── lesson-01/
│   │   ├── README.md           # レッスン1: Spec駆動開発入門
│   │   └── instructions.md     # Kiroへの指示例
│   ├── lesson-02/
│   │   ├── README.md           # レッスン2: コード生成とリファクタリング
│   │   └── instructions.md
│   ├── lesson-03/
│   │   ├── README.md           # レッスン3: AgentHooksによる自動化
│   │   └── instructions.md
│   └── lesson-04/
│       ├── README.md           # レッスン4: MCP連携と実践
│       └── instructions.md
└── .kiro/
    └── (Kiro設定ファイル)
```

### レッスン構成

各レッスンは以下の構造を持ちます：

1. **学習目標**: そのレッスンで習得するスキル
2. **所要時間**: 約30分以内
3. **前提知識**: 前のレッスンで学んだ内容
4. **Kiroへの指示例**: 具体的なプロンプト例
5. **期待される結果**: Kiroが生成すべき成果物
6. **確認ポイント**: 学習内容の理解度チェック
7. **次のステップ**: 次のレッスンへの導線


## コンポーネントとインターフェース

### 1. README.md（エントリーポイント）

**目的**: ユーザーが最初に読むドキュメント。チュートリアルの全体像と始め方を提供。

**内容**:
- プロジェクトの概要
- 前提条件（Kiroのインストール、アカウント登録）
- クイックスタート（最初のKiroへの挨拶）
- レッスン一覧と学習パス
- クレジット消費の目安
- サポート情報

**Kiroへの最初の挨拶例**:
```
こんにちは！Kiroのハンズオンチュートリアルを始めます。
まずはlesson-01/README.mdを開いて、内容を確認してください。
```

### 2. セットアップガイド（docs/setup.md）

**目的**: Kiroの環境構築手順を提供。

**内容**:
- Kiroのインストール手順
- アカウント登録とトライアルクレジットの確認
- プロジェクトのクローン方法
- 初期設定の確認
- 動作確認方法

### 3. クレジットガイド（docs/credits-guide.md）

**目的**: Kiroのクレジット制を説明し、効率的な使い方を提案。

**内容**:
- クレジット制の仕組み（2025年3月時点）
- トライアルクレジットの内容（約100クレジット）
- 各機能のクレジット消費目安
  - Spec作成: 高コスト（10-20クレジット程度）
  - コード生成: 中コスト（5-10クレジット程度）
  - チャット（Vibe）: 低コスト（1-3クレジット程度）
- 有料プランの比較
  - Pro Tier: 約$20/月、月間1,000クレジット
  - Pro+ Tier: 約$40/月、月間2,000-3,000クレジット
- クレジット節約のコツ

### 4. レッスン1: Spec駆動開発入門

**学習目標**:
- ステアリングファイルでKiroの性格と語尾をカスタマイズする方法を理解
- Kiroの最大の差別化ポイント「Spec駆動開発」を理解
- Requirements-first Workflowを体験
- 自然言語から設計書とコードが生成される流れを体感

**開発テーマ**: （後で決定）

**Kiroへの指示例**:

初期設定パート:
```
.kiro/steering.mdを開いて、Kiroの性格設定の部分を見せてください。
```

```
ステアリングファイルを編集して、Kiroの性格を[フレンドリー/丁寧/カジュアル]に、
語尾を[〜だよ/〜です/〜ですわ]に変更してください。
```

```
こんにちは！今日の調子はどう？
```

Spec作成パート:
```
[開発テーマ]のプロジェクトを作りたいです。
Requirements-first Workflowで進めてください。
```

**学習内容**:
1. ステアリングファイルとは何か
2. Kiroの性格と語尾の設定方法
3. ステアリングファイルの効果を実感（Kiroに話しかけて確認）
4. Specとは何か（Requirements、Design、Tasks）
5. Requirements-first Workflowの流れ
6. 要件定義の書き方（EARS形式）
7. Kiroとの対話による要件の洗練
8. 設計書の自動生成
9. タスクリストの作成

**期待される成果物**:
- カスタマイズされた`.kiro/steering.md`
- `.kiro/specs/[project-name]/requirements.md`
- `.kiro/specs/[project-name]/design.md`
- `.kiro/specs/[project-name]/tasks.md`

**クレジット消費目安**: 25-35クレジット（ステアリングファイル設定を含む）

### 5. レッスン2: コード生成とリファクタリング

**学習目標**:
- Specに基づくコード生成を体験
- リファクタリング機能を理解
- ファイル操作と検索機能を活用

**Kiroへの指示例**:
```
tasks.mdの最初のタスクを実行してください。
```

**学習内容**:
1. タスクの実行方法
2. コード生成の流れ
3. 生成されたコードの確認
4. リファクタリングの指示方法
5. ファイル検索とコード検索
6. エラーの修正方法

**期待される成果物**:
- 実装されたソースコード
- テストコード
- ドキュメント

**クレジット消費目安**: 30-40クレジット


### 6. レッスン3: AgentHooksによる自動化

**学習目標**:
- AgentHooksの概念と価値を理解
- ファイル保存時の自動処理を体験
- 有料プラン推奨機能の魅力を実感

**Kiroへの指示例**:
```
AgentHooksを設定して、ファイル保存時に自動でREADMEを更新するようにしてください。
```

**学習内容**:
1. AgentHooksとは何か
2. イベントトリガーの種類（ファイル保存、コミットなど）
3. Hooksの設定方法
4. 自動化の実例（README更新、テスト実行など）
5. クレジット消費の注意点
6. 有料プランの必要性

**期待される成果物**:
- `.kiro/hooks/` 配下の設定ファイル
- 自動更新されるREADME.md
- 自動生成されるテストコード

**クレジット消費目安**: 40-50クレジット（自動実行のため消費が多い）

**注意事項**:
- AgentHooksは放置すると大量のクレジットを消費する可能性がある
- 実運用には有料プラン（Pro Tier以上）が推奨される
- トライアルクレジットで試す場合は、短時間で無効化することを推奨

### 7. レッスン4: MCP連携と実践

**学習目標**:
- MCP（Model Context Protocol）の概念を理解
- 外部ツールとの連携を体験
- 実務での活用イメージを持つ

**Kiroへの指示例**:
```
MCPサーバーを使って、[外部サービス]と連携してください。
```

**学習内容**:
1. MCPとは何か
2. MCPサーバーの種類
3. 外部ツールとの連携例
4. 自社データベースとの連携の可能性
5. エンタープライズ向け機能
6. 実務導入のステップ

**期待される成果物**:
- MCP連携の設定ファイル
- 外部サービスと連携したコード
- 実践的なプロジェクト

**クレジット消費目安**: 30-40クレジット

**注意事項**:
- 基本的なMCP連携はトライアルクレジットで可能
- 高度な連携や大量のデータ処理には有料プランが推奨される

### 8. トラブルシューティング（docs/troubleshooting.md）

**目的**: よくある問題と解決方法を提供。

**内容**:
- Kiroが応答しない場合
- クレジットが不足した場合
- エラーメッセージの解釈
- コード生成が期待通りでない場合
- ファイルが見つからない場合
- AgentHooksが動作しない場合
- ステアリングファイルが反映されない場合
- サポートへの問い合わせ方法

### 9. ステアリングファイル（.kiro/steering.md）

**目的**: このプロジェクトをクローンしたユーザーのKiroに対する永続的な指示を提供し、チュートリアル体験を最適化する。

**配置**: リポジトリのルートに`.kiro/steering.md`として配置され、ユーザーがクローンした時点で有効になる。

**役割**:
- Kiroがこのプロジェクトの目的（ハンズオンチュートリアル）を理解する
- ユーザーが学習者であることを認識し、適切なサポートを提供する
- 日本語での説明、初心者向けの表現を徹底する
- クレジット効率を意識した応答を行う

**内容**:
- プロジェクトの目的と概要
- Kiroが従うべき基本方針
- Kiroの性格設定（デフォルト：フレンドリー）
- Kiroの語尾設定（デフォルト：〜です）
- レッスン進行時の注意事項
- コード生成時のスタイルガイド
- ドキュメント更新時のルール
- クレジット効率化のヒント

**例**:
```markdown
# Kiroハンズオンチュートリアル - ステアリングファイル

このプロジェクトは、Kiroの初心者向けハンズオンチュートリアルです。

## 基本方針

- ユーザーは学習者であり、段階的に学習を進めています
- 説明は日本語で、プログラミング初心者にもわかりやすく
- クレジット消費を意識し、効率的な指示を心がける
- 各レッスンの学習目標を達成できるようサポートする

## Kiroの性格設定

性格: フレンドリー
語尾: 〜です

（レッスン1でユーザーがこの部分を編集して、Kiroの応答が変わることを体験します）

## レッスン進行時の注意

- ユーザーが現在どのレッスンにいるか確認する
- 前のレッスンの内容を前提として説明する
- 次のレッスンへの導線を明確にする

## コード生成時のルール

- シンプルで読みやすいコードを生成する
- コメントは日本語で記述する
- 初心者でも理解できる実装を優先する

## クレジット効率化

- 不要な再生成を避ける
- 一度に複数の変更をまとめて処理する
- ユーザーの意図を確認してから実行する
```

**注意**: このファイルは、プロジェクト作成者（このspecを実行する人）が作成し、リポジトリに含めます。レッスンを受けるユーザーは、このファイルを編集する必要はありません。

## データモデル

### レッスンメタデータ

各レッスンは以下のメタデータを持ちます：

```typescript
interface Lesson {
  id: string;                    // "lesson-01"
  title: string;                 // "Spec駆動開発入門"
  duration: number;              // 30（分）
  creditEstimate: number;        // 20-30（クレジット）
  prerequisites: string[];       // ["Kiroのインストール"]
  learningObjectives: string[];  // ["Spec駆動開発を理解する", ...]
  features: string[];            // ["Spec作成", "Requirements-first"]
  tier: "trial" | "pro";        // トライアルクレジット内 or 有料プラン推奨
}
```

### プロジェクトテーマ

開発テーマは以下の条件を満たす必要があります：

```typescript
interface ProjectTheme {
  name: string;                  // プロジェクト名
  description: string;           // 説明
  difficulty: "beginner";        // 初心者向け
  estimatedTime: number;         // 全レッスン合計時間（分）
  technologies: string[];        // 使用技術
  learningValue: string[];       // 学習できる内容
}
```

**候補テーマの条件**:
- プログラミング初心者でも理解できる
- 4レッスン（合計2時間）で完成できる
- Kiroの機能を満遍なく体験できる
- 実務での活用イメージが湧く
- クレジット消費が適切（合計100クレジット以内）


## 正確性プロパティ

プロパティとは、システムのすべての有効な実行において真であるべき特性や振る舞いのことです。プロパティは、人間が読める仕様と機械で検証可能な正確性保証の橋渡しとなります。

このセクションでは、チュートリアルシステムが満たすべき普遍的なプロパティを定義します。これらのプロパティは、自動テストやレビューチェックリストとして使用できます。

### プロパティ1: レッスン構成の完全性

*すべての*レッスンディレクトリ（lesson-01からlesson-04）について、各レッスンはREADME.mdとinstructions.mdを含む必要がある

**検証方法**: Requirements 1.1, 9.4

### プロパティ2: Kiroへの指示例の提供

*すべての*レッスンについて、そのレッスンはKiroへの具体的な指示例を含む必要がある

**検証方法**: Requirements 2.5, 3.6, 4.3, 4.4, 6.6, 8.4, 9.6

### プロパティ3: クレジット消費情報の提供

*すべての*レッスンについて、そのレッスンはクレジット消費の目安を明示する必要がある

**検証方法**: Requirements 3.7, 6.7

### プロパティ4: 学習目標の明確化

*すべての*レッスンについて、そのレッスンは学習目標、所要時間、期待される成果物を明示する必要がある

**検証方法**: Requirements 4.5, 7.1

### プロパティ5: 段階的な進行

*すべての*レッスンについて、そのレッスンは前提知識と次のステップを明示する必要がある

**検証方法**: Requirements 4.3

### プロパティ6: 日本語ドキュメント

*すべての*ドキュメントファイル（.mdファイル）について、その内容は日本語で記述される必要がある

**検証方法**: Requirements 2.4, 8.1

### プロパティ7: 必須ファイルの存在

*すべての*必須ファイル（README.md、docs/setup.md、docs/credits-guide.md、docs/troubleshooting.md）について、それらのファイルはリポジトリのルートまたは適切なディレクトリに存在する必要がある

**検証方法**: Requirements 9.3, 9.5

### プロパティ8: 視覚的補助の提供

*すべての*レッスンについて、そのレッスンは図表やスクリーンショットなどの視覚的補助を含むことが推奨される

**検証方法**: Requirements 8.5

### 例ベースの検証項目

以下の項目は、特定の例や条件で検証します：

**例1: レッスン数の確認**
- レッスンディレクトリの数が正確に4つであること
- **検証方法**: Requirements 1.1

**例2: Spec駆動開発の優先配置**
- レッスン1がSpec作成機能（Requirements-first Workflow）を扱っていること
- **検証方法**: Requirements 1.6, 3.1

**例3: 機能カバレッジ**
- いずれかのレッスンがコード生成機能を扱っていること
- いずれかのレッスンがリファクタリング機能を扱っていること
- いずれかのレッスンがファイル操作機能を扱っていること
- いずれかのレッスンが検索機能を扱っていること
- **検証方法**: Requirements 3.2, 3.3, 3.4, 3.5

**例4: トライアルクレジット内での体験**
- レッスン1-2の合計クレジット消費目安が100クレジット以内であること
- **検証方法**: Requirements 1.4, 5.1

**例5: 有料プラン推奨機能の紹介**
- レッスン3がAgentHooksを扱っていること
- レッスン4がMCP連携を扱っていること
- **検証方法**: Requirements 1.5, 6.1, 6.3, 6.4

**例6: README.mdの内容**
- README.mdにKiroへの最初の挨拶指示が含まれていること
- README.mdにクイックスタートガイドが含まれていること
- **検証方法**: Requirements 2.1, 9.1, 9.2

**例7: セットアップガイドの内容**
- docs/setup.mdにKiroのインストール手順が含まれていること
- docs/setup.mdに環境設定の手順が含まれていること
- **検証方法**: Requirements 2.2, 2.3

**例8: クレジットガイドの内容**
- docs/credits-guide.mdにクレジット制の仕組みの説明が含まれていること
- docs/credits-guide.mdにトライアルクレジットの情報が含まれていること
- docs/credits-guide.mdに有料プランの料金情報が含まれていること
- **検証方法**: Requirements 5.3, 5.4, 6.5

**例9: トラブルシューティングの内容**
- docs/troubleshooting.mdによくある問題と解決方法が含まれていること
- docs/troubleshooting.mdにエラーメッセージの解釈方法が含まれていること
- docs/troubleshooting.mdにサポートリソースへのリンクが含まれていること
- **検証方法**: Requirements 10.1, 10.2, 10.3

**例10: 最終レッスンの内容**
- レッスン4に総合的な振り返りが含まれていること
- レッスン4に実務導入のための次のステップが含まれていること
- **検証方法**: Requirements 7.2, 7.4


## エラーハンドリング

### ユーザーエラー

**クレジット不足**:
- 症状: ユーザーがトライアルクレジットを使い切った
- 対処: docs/credits-guide.mdに有料プランへのアップグレード方法を記載
- 予防: 各レッスンでクレジット消費目安を明示

**Kiroが応答しない**:
- 症状: Kiroが指示に応答しない、または期待通りの結果が得られない
- 対処: docs/troubleshooting.mdに再試行方法、指示の改善方法を記載
- 予防: 各レッスンで具体的な指示例を提供

**ファイルが見つからない**:
- 症状: レッスンで参照しているファイルが存在しない
- 対処: docs/troubleshooting.mdにファイル構造の確認方法を記載
- 予防: リポジトリに必要なファイル構成を事前に用意

**AgentHooksが動作しない**:
- 症状: AgentHooksを設定したが自動処理が実行されない
- 対処: docs/troubleshooting.mdに設定確認方法、クレジット残高確認を記載
- 予防: レッスン3でAgentHooksの注意事項を明記

### システムエラー

**ドキュメントの不整合**:
- 症状: レッスン間で情報が矛盾している
- 対処: レビュープロセスで正確性プロパティを確認
- 予防: 正確性プロパティに基づく自動チェック

**クレジット消費目安の誤り**:
- 症状: 実際のクレジット消費が目安と大きく異なる
- 対処: 定期的にクレジット消費を測定し、ドキュメントを更新
- 予防: 2025年3月時点の情報であることを明記

**リンク切れ**:
- 症状: ドキュメント内のリンクが無効
- 対処: 定期的なリンクチェック
- 予防: 相対パスの使用、外部リンクの最小化

## テスト戦略

### デュアルテストアプローチ

このプロジェクトでは、以下の2つのテストアプローチを組み合わせます：

1. **ユニットテスト**: 特定の例、エッジケース、エラー条件を検証
2. **プロパティベーステスト**: 普遍的なプロパティをすべての入力で検証

両方のアプローチは補完的であり、包括的なカバレッジを実現します。

### ユニットテスト

ユニットテストは、特定の例とエッジケースに焦点を当てます：

**ファイル存在チェック**:
```typescript
describe('Required Files', () => {
  test('README.md exists', () => {
    expect(fs.existsSync('README.md')).toBe(true);
  });
  
  test('All lesson directories exist', () => {
    for (let i = 1; i <= 4; i++) {
      const lessonDir = `lessons/lesson-0${i}`;
      expect(fs.existsSync(lessonDir)).toBe(true);
    }
  });
});
```

**レッスン数チェック**:
```typescript
describe('Lesson Count', () => {
  test('Exactly 4 lessons exist', () => {
    const lessons = fs.readdirSync('lessons');
    expect(lessons.length).toBe(4);
  });
});
```

**特定機能のカバレッジ**:
```typescript
describe('Feature Coverage', () => {
  test('Lesson 1 covers Spec creation', () => {
    const content = fs.readFileSync('lessons/lesson-01/README.md', 'utf-8');
    expect(content).toContain('Spec');
    expect(content).toContain('Requirements-first');
  });
  
  test('Lesson 3 covers AgentHooks', () => {
    const content = fs.readFileSync('lessons/lesson-03/README.md', 'utf-8');
    expect(content).toContain('AgentHooks');
  });
});
```

### プロパティベーステスト

プロパティベーステストは、普遍的なプロパティを検証します。各テストは最低100回の反復で実行します。

**プロパティ1: レッスン構成の完全性**:
```typescript
// Feature: kiro-hands-on-tutorial, Property 1: レッスン構成の完全性
describe('Property: Lesson Structure Completeness', () => {
  test('All lessons have required files', () => {
    const lessons = ['lesson-01', 'lesson-02', 'lesson-03', 'lesson-04'];
    
    lessons.forEach(lesson => {
      const lessonPath = `lessons/${lesson}`;
      expect(fs.existsSync(`${lessonPath}/README.md`)).toBe(true);
      expect(fs.existsSync(`${lessonPath}/instructions.md`)).toBe(true);
    });
  });
});
```

**プロパティ2: Kiroへの指示例の提供**:
```typescript
// Feature: kiro-hands-on-tutorial, Property 2: Kiroへの指示例の提供
describe('Property: Kiro Instructions Provided', () => {
  test('All lessons contain Kiro instruction examples', () => {
    const lessons = ['lesson-01', 'lesson-02', 'lesson-03', 'lesson-04'];
    
    lessons.forEach(lesson => {
      const content = fs.readFileSync(`lessons/${lesson}/instructions.md`, 'utf-8');
      // 指示例を示すマーカー（コードブロックや特定のフォーマット）が含まれているか確認
      expect(content.length).toBeGreaterThan(0);
      expect(content).toMatch(/```|指示例|Kiroへの指示/);
    });
  });
});
```

**プロパティ3: クレジット消費情報の提供**:
```typescript
// Feature: kiro-hands-on-tutorial, Property 3: クレジット消費情報の提供
describe('Property: Credit Consumption Info', () => {
  test('All lessons specify credit consumption estimates', () => {
    const lessons = ['lesson-01', 'lesson-02', 'lesson-03', 'lesson-04'];
    
    lessons.forEach(lesson => {
      const content = fs.readFileSync(`lessons/${lesson}/README.md`, 'utf-8');
      expect(content).toMatch(/クレジット|credit/i);
    });
  });
});
```

**プロパティ6: 日本語ドキュメント**:
```typescript
// Feature: kiro-hands-on-tutorial, Property 6: 日本語ドキュメント
describe('Property: Japanese Documentation', () => {
  test('All markdown files are in Japanese', () => {
    const mdFiles = glob.sync('**/*.md', { ignore: 'node_modules/**' });
    
    mdFiles.forEach(file => {
      const content = fs.readFileSync(file, 'utf-8');
      // 日本語文字（ひらがな、カタカナ、漢字）が含まれているか確認
      expect(content).toMatch(/[\u3040-\u309F\u30A0-\u30FF\u4E00-\u9FAF]/);
    });
  });
});
```

### テスト実行

**テストフレームワーク**: Jest（TypeScript/JavaScript）または pytest（Python）

**実行コマンド**:
```bash
# ユニットテスト
npm test

# プロパティベーステスト（100回反復）
npm test -- --testNamePattern="Property"
```

**CI/CD統合**:
- プルリクエストごとにすべてのテストを実行
- ドキュメント更新時に正確性プロパティを検証
- 定期的にクレジット消費目安の妥当性を確認

### レビューチェックリスト

自動テストでカバーできない項目は、人間のレビューで確認します：

- [ ] 各レッスンは30分以内で完了できる分量か（Requirements 1.2）
- [ ] レッスンは初級から上級へ段階的に進行しているか（Requirements 1.3）
- [ ] 開発テーマはプログラミング初心者でも理解できるか（Requirements 4.2）
- [ ] ドキュメントはプログラミング初心者にもわかりやすい表現か（Requirements 8.2）
- [ ] 技術用語に適切な説明が付いているか（Requirements 8.3）
- [ ] チュートリアル完了後、「Kiroってどんな感じ？」に答えられるか（Requirements 7.3）

