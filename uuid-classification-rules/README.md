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

- `06_Universal_Schema_Concept.md` — ユニバーサルスキーマの概念、理論と実装のギャップ、従属レイヤー
- `07_TANAAKK_Engineering_Methodology.md` — 従来型 vs TANAAKK 流のエンジニアリング対比
- `tanaakk-uuid-hybrid.mdc` — デュアルID設計（logic_id/phys_id）、検索戦略、計算資源節約のスキーマ構成
- `tanaakk-universal-schema.mdc` — 規格階層（L4A/L4B/L4C）

## 補足：3PL 倉庫・ハンディターミナル

製造小売業のケーススタディには、3PL 倉庫におけるハンディターミナル（HT）の規格を反映した採番ルールを記載している。バーコード種別（1D/2D/QR）、ロケーションコード体系（エリア-通路-棚-段）、伝票コード体系（入荷/出荷/内部移動）は属性として扱い、個別端末情報や固有名詞は使用しない。
