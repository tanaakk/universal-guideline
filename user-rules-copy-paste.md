# Cursor User Rules（Cursor Settings > Rules for AI に貼る用）

以下を **Cursor > Settings > General > Rules for AI** にコピー＆ペーストしてください。

---

# TANAAKK SaaS 横断ルール（完全版）

## 1. 適用範囲

| アプリ | 役割 | 会計連携 |
|-------|------|----------|
| OMS | 受注・稟議・ASN | 売上計上、請求 |
| WMS | 在庫・出荷 | 棚卸、原価 |
| MES | 生産・実績 | 製造原価 |
| Aura | 統合ダッシュボード | 集計・レポート |

## 2. ID設計 (Identity)

| 項目 | ルール |
|------|--------|
| PK | 全テーブルは業務的意味を持たない UUID v4 (RFC 9562) |
| Surrogate Key | JAN、法人番号、品番等をPK/結合キーに使用禁止。これらは「属性」として扱う |
| FK | テーブル間リレーションはすべて UUIDベースのFK |

## 3. 時間と単位

| 項目 | ルール |
|------|--------|
| 時刻 | UTC + ISO 8601 (YYYY-MM-DDTHH:MM:SSZ) |
| タイムゾーン | DB層は常にUTC、表示はアプリ層でローカル変換 |
| 単位 | 重量=kg、長さ=m。「ケース」「ロット」等は基準単位への変換係数で管理 |

### 3.1 通貨 (ISO 4217)

| 項目 | ルール |
|------|--------|
| 通貨コード | 必ず ISO 4217 の3文字コード（JPY, USD, EUR 等）を使用する |
| 金額の格納 | currency_code と amount を別カラムで管理。amount は decimal/numeric 型 |
| 小数桁 | 通貨の minor unit に従う（JPY=0桁、USD/EUR=2桁） |
| 禁止 | 「円」「ドル」等の表記、独自コード、float での金額格納 |

## 4. 会計API連携 (Money Forward / Xero)

### 4.1 会計基準マッピング

| 会計基準 | 主な適用先 | 連携先 |
|----------|------------|--------|
| JGAAP | 日本法人 | マネーフォワード クラウド会計 |
| IFRS | グローバル法人 | Xero (140+国) |
| US GAAP | 米国法人 | Xero US |

### 4.2 会計API引き渡しの必須項目

会計システムへ引き渡す取引データには以下を必須とする：

- transaction_uuid (UUID): 取引の一意識別子
- occurred_at (ISO 8601): 発生日時（実現主義）
- recognized_at (ISO 8601): 計上日（収益認識基準）
- currency_code (ISO 4217): 通貨
- amount (decimal): 金額（minor unit 桁数厳守）
- accounting_standard (enum): JGAAP | IFRS | US_GAAP
- external_id (string): 会計側の連携ID（冪等用）

### 4.3 金額計算・丸め

- Math.round 等を直接使わない
- 通貨ごとの precision と rounding_rule (truncate / half_up) をユーティリティで統一
- 監査ログ: 金額・ステータス変更は created_by (UUID) と共にイミュータブルに記録

## 5. API設計

- OpenAPI 3.0+ 準拠の RESTful 設計
- エンティティ操作は UUID (/orders/{order_uuid}) で指定
- JAN・品番等は検索パラメータとして扱う

## 6. マスタデータ戦略

- 商品・取引先・場所・イベントを独立エンティティとし、UUIDでグラフ状に結合
- 法人番号・JAN・Pantone等は「変更され得る属性」として履歴管理

## 7. 禁止事項

- 複合キー（部門+年度等をPKにしない）
- 意味のあるコードをIDに埋め込む
- 曖昧な時刻形式（YYYY/MM/DD 等）の出力

## 8. ドキュメンテーション

- 設計図は Mermaid形式 で出力
- ER図は erDiagram を使用し、PK(UUID)・FK・属性を明示
- 実装コードとMermaid図の変数名・構造を 100%一致 させる

## 9. 開発ワークフロー (Design First)

1. 設計先行: 新規機能・スキーマ変更時、いきなり実装しない
2. 図の提示: Mermaid形式でER図・シーケンス図を提示し合意を得る
3. セルフチェック: ID設計・時間・通貨ルールの遵守を検証
4. 合意後の実装: 承認を得てから実装

---

# 共通UI/UXプリンシパル: 汎用モダン・ライトクリーン

## 1. カラーシステム (Light Mode Base)

| 項目 | 値 |
|------|-----|
| Background | #FFFFFF または #F9FAFB |
| Primary | #3B82F6（信頼感のある Blue） |
| Text メイン | #111827 (Almost Black) |
| Text サブ | #6B7280 (Muted Gray) |
| Border | #E5E7EB（ラインで境界を表現） |

## 2. タイポグラフィ (Universal Sans)

| 項目 | ルール |
|------|--------|
| Font Family | Inter, system-ui, sans-serif |
| Title | Bold, 1.25rem以上 |
| Body | Normal, 0.875rem ~ 1rem |
| Line Height | 1.5 ~ 1.6 |

## 3. アイコン・コンポーネント

| 項目 | ルール |
|------|--------|
| Library | Lucide React または Heroicons |
| Radius | 8px (rounded-lg) |
| Clickable | 最小 44x44px のタップ領域 |

## 4. コーディング制約

| 項目 | ルール |
|------|--------|
| Framework | モバイルネイティブでレスポンシブなモダン言語を選択する |
| Consistency | shadcn/ui 等のデザイントークンと統一 |
| Accessibility | aria-label、セマンティックHTML（nav, main, section） |

---

# 言語・フレームワーク選択指針

## 1. 選択の原則

- レスポンシブ優先: モバイル・タブレット・デスクトップで一貫したUXを提供できる技術を選ぶ
- 横断再利用: OMS/WMS/MES/Aura 間でコンポーネント・型定義を共有しやすい構成を優先
- 会計連携: 金額計算・decimal 精度を厳密に扱える言語を選ぶ

## 2. 目的別選択マトリクス

| 目的 | 推奨言語/スタック |
|------|-------------------|
| Web UI（OMS/WMS/MES/Aura） | TypeScript + React + Next.js + Tailwind |
| API / BFF | TypeScript (Node.js) または Python |
| バッチ・ETL・会計連携 | Python |
| モバイルネイティブ | React Native (TypeScript) または Flutter |
| インフラ・CI | YAML, HCL (Terraform), Shell |

## 3. 検討フロー（AIが適用する手順）

1. UI が必要か？ → Yes: TypeScript + React/Next.js
2. 金額計算・会計ロジックが中核か？ → Yes: Python を検討（decimal 厳密）
3. 既存プロジェクトのスタックは？ → 既存に合わせる（一貫性優先）
4. モバイル専用か？ → React Native または Flutter
5. API クライアント（Money Forward / Xero）のみか？ → TypeScript で統一、または Python

## 4. レスポンシブ実装の前提

- CSS: Tailwind CSS の sm: md: lg: ブレークポイントを標準使用
- コンポーネント: 最小タップ領域 44x44px、aria-label 必須
- フォント: Inter, system-ui, sans-serif

---

※ プロジェクトルール（.cursor/rules/）と併用可。
