# UUID 採番分類ルール — ケーススタディ

`tanaakk-uuid-hybrid.mdc` の採番原則に基づく、業種別の UUID v4 / UUID v7 / 採番なし の分類ルール。

## 位置づけ

本フォルダは **従属レイヤーの構造化**（`06_Universal_Schema_Concept.md` 6.2、`tanaakk-uuid-hybrid.mdc` 7.0 参照）の一環である。理論（UUIDv4 の完全性・非局所性）を維持しつつ、**業種別のドメイン定義**に基づいて最小作用で実装するための採番ルールを提供する。

TANAAKK 流のエンジニアリングでは、古いアプリを参照せず **事業ドメイン・重要アセット・データセット** を参照する（`07_TANAAKK_Engineering_Methodology.md` 参照）。本ケーススタディは、そのドメイン定義に応じた採番の具体化である。

## 用語の対応（tanaakk-uuid-hybrid.mdc との整合）

| 本ドキュメント | tanaakk-uuid-hybrid.mdc | 役割 |
|----------------|-------------------------|------|
| **対象 (v4)** | logic_id | 空間・時間に依存しない事象の「点」。論理的不変性 |
| **記録 (v7)** | phys_id | 時間軸でソートされる事象の「座標」。時系列検索・物理的書き込み最適化 |
| **Object（対象）** | L3 Identity | 実体。製品、原材料、建物、契約等 |
| **Morphism（射）** | L4 Attribute への射 | 関係・行動・イベント。対象間の結合 |

## 採番原則（要約）

| 採番 | 条件 |
|------|------|
| **UUID v4** | ビジネスが世界を分類する重要なインジケーター。ARPP・KPI・収益認識の対象 |
| **UUID v7** | 検索・時系列が必要な場合。v4 と同時付与も自然 |
| **採番なし** | ビジネス分類の軸にならず、記録の主体にもならない変数 |

## ケーススタディ一覧

| 業種 | ファイル | 中心となる価値 |
|------|----------|------------------|
| 製造小売業 | [manufacturing-retail.md](./manufacturing-retail.md) | モノ。消費者が最終所有者 |
| 不動産・建設業 | [real-estate-construction.md](./real-estate-construction.md) | 空間・資産。購入者・賃借人が利用者 |

## 参照

### 上位の採番ルール（本ケーススタディの前提）

- `tanaakk-uuid-hybrid.mdc` — デュアルID設計（logic_id/phys_id）、検索戦略、計算資源節約のスキーマ構成。**公式仕様（RFC 9562, RFC 4122）への参照を含む**
- `tanaakk-universal-schema.mdc` — 規格階層（L4A/L4B/L4C）

### 概念・方法論

- `06_Universal_Schema_Concept.md` — ユニバーサルスキーマの概念、理論と実装のギャップ、従属レイヤー
- `07_TANAAKK_Engineering_Methodology.md` — 従来型 vs TANAAKK 流のエンジニアリング対比

## 参考文献：採番要否の条件検討のヒント

採番原則（v4/v7/採番なし）の条件を検討する際のヒントとなる文献。GTIN 等を natural key として属性扱いし、UUIDv4 を surrogate key とする設計、収益認識につながるインジケーターの数値管理、採番コストとビジネスリターンのトレードオフに関する議論を含む。

### サロゲートキー vs ナチュラルキー（GTIN を属性とする考え方）

| 文献 | ヒント |
|------|--------|
| [Kimball (1998) Surrogate Keys](https://www.kimballgroup.com/1998/05/surrogate-keys/) | ナチュラルキー（UPC/GTIN 含む）を PK に使わずサロゲートキーに置き換える。ナチュラルキーは次元テーブルの属性として保持。UPC の再利用・再採番問題を指摘 |
| [Kimball Dimension Surrogate Key](https://www.kimballgroup.com/data-warehouse-business-intelligence-resources/kimball-techniques/dimensional-modeling-techniques/dimension-surrogate-key/) | 次元の PK は匿名整数のサロゲートキー。複数ソースのナチュラルキーは不整合になりやすい |
| [Natural vs. Surrogate Keys (Baeldung)](https://www.baeldung.com/sql/keys-natural-vs-surrogate) | サロゲートキーは安定性・パフォーマンスに有利。ナチュラルキーは意味を持つが変更・再利用のリスク |

### 識別子採番のコストとビジネスリターンのトレードオフ

| 文献 | ヒント |
|------|--------|
| [ARDC: Incentives to Invest in Identifiers](https://ardc.edu.au/resource/incentives-to-invest-in-identifiers-report/) | 永続識別子（PID）の投資インセンティブ。コスト便益分析。オーストラリア研究セクターで年 2,400 万ドル・38,000 人日相当の節約を試算 |
| [ARDC: Strategic Investment in Identifiers](https://ardc.edu.au/article/strategic-investment-in-identifiers-could-save-24-million-and-38000-person-days-per-year/) | 識別子への戦略的投資の ROI。機会コストを含めると年 8,400 万ドル相当 |
| [ODI: Using identifiers](https://theodi.org/insights/guides/using-identifiers/) | 識別子スキームの設計・ガバナンス・採番がコストと持続可能性に与える影響。「identifiers which capture revenue (eg ISRCs or GS1 codes)」。UUID は生成コストは低いがスペース・可読性のトレードオフ |

### 収益データモデル・収益認識と識別子

| 文献 | ヒント |
|------|--------|
| [IFRS 15 Revenue from Contracts with Customers](https://www.ifrs.org/content/dam/ifrs/publications/html-standards/english/2024/issued/ifrs15.html) | 契約・履行義務の識別が収益認識の前提。識別可能性の要件 |
| [A Practical Guide to Building a Unified Revenue Data Model](https://devrix.com/tutorial/revenue-data-guide/) | 収益データモデルでは次元・ファクトの結合にサロゲートキーを使用。ナチュラルキーは使わない。粒度（grain）を先に定義 |
| [Kimball: Declaring the Grain](https://www.kimballgroup.com/2003/03/declaring-the-grain/) | ファクトの粒度を先に定義。収益・KPI の単位を決める前提 |

### マスタデータ管理・サプライチェーン

| 文献 | ヒント |
|------|--------|
| [Design considerations for Enterprise Entity Identifier](https://kodali-satish.medium.com/design-conciderations-for-enterprise-entity-identifier-d5c7092b385) | 顧客・ベンダー・製品等の**ビジネス上重要なエンティティ**にエンタープライズ識別子を付与 |
| [GS1 Global Traceability Standard](https://www.gs1.org/standards/gs1-global-traceability-standard/current-standard) | 製品（GTIN）、ロケーション（GLN）、イベントの識別。トレーサビリティの前提 |
