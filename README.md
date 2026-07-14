# TANAAKK Cursor Rules

TANAAKKグループが提供する全アプリで共通利用する Cursor AI ルールです。このレポジトリはPublicです。

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL%20v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)

## コンセプト

この Universal Rule は**逐次アップデート**される。

- **地球のベストプラクティス**: 最新時点での業界標準（Google AIP、Microsoft、IANA、会計API連携等）を採用し、随時更新する。
- **多惑星文明のベストプラクティス**: NASA/ホワイトハウス Celestial Time Standardization Policy、Coordinated Lunar Time (LTC)、火星時間等、重力圏に応じた抽象時間・参照系の標準が策定・普及するに従い、それらを取り込んで更新する。

## Universal Guideline の前提条件

この宇宙に存在する任意のシステムは、以下の 3 つの物理原理を大局制約（global constraints）として満たすことを前提とする。

- **Locality（局所性）**: 相互作用・情報伝播は局所的結合を通じて生起し、超光速の因果的伝達を許さない。
- **Causality（因果性）**: 原因は結果に先行し、システムの時間発展は因果順序を保存する。
- **Unitarity（ユニタリ性）**: 系の確率・情報が保存される。

形式的には、任意のシステム `S` について `S |= (L ∧ C ∧ U)` を満たすものとして扱う。

参照: [物理の三大構造原理](https://www.tanaakk.com/2026/03/17/physics-2/)

## Universal Guideline のスコープと階層

**本リポジトリは L3 以降の階層を定義する。** L0〜L2 は [groundism-ontopologics](https://github.com/tanaakk/groundism-ontopologics) 等で定義される。

UUID v4 を識別子規格として採用した場合、車両・製造・建設・貴金属・医療等の規格は、**UUID v4 で記録された対象への射として表現される属性**にすぎない。従って階層が繰り下げられる。

| 層 | 内容 | 主な規格・ルール |
|----|------|------------------|
| **L3** | UUID v4。識別子規格。対象の層 | tanaakk-universal-schema.mdc, tanaakk-uuid-hybrid.mdc |
| **L4** | 対象への射としての属性 | L4A（産業分類）、L4B（クロスインダストリ）、L4C（インダストリ別） |
| **L5** | プロジェクト | プロジェクト固有のコーディング規約 |

## L4 の下位階層（L4A, L4B, L4C）

`tanaakk-universal-schema.mdc` 2.1 では、規格を以下の階層で位置付ける。これらは L4 の**射（属性）**として L3 の UUID v4 対象に付与される。

| 層 | 内容 | 主な規格 |
|----|------|----------|
| **L4A** | 産業分類（国家・国際管理） | ISIC, NACE, CPC, NAICS |
| **L4B** | クロスインダストリ | ISO 8601, ISO 4217, GTIN, EDI, ISO 20022, IAM, MES, Amazon Marketplace Ads |
| **L4C** | インダストリ別 | 建築, 貴金属, 宝石, 鉱物・宝石学, 繊維, 元素, 宇宙機, 時計, メティエダール, 発電, 保険, 金融, 石油・ガス, 医療, 農業・食品, Fauna・Flora・Marine life（ミュージオロジー） |

**識別子は UUID v4 のみ。** 上記規格コードはすべて属性として格納し、PK/FK には使用しない。

## パッケージング方針

スキーマが決まれば procedure が決まる（[groundism-ontopologics](https://github.com/tanaakk/groundism-ontopologics)）。**スキーマ・procedure・UUID 採番ルール・業種別ケーススタディは同一リポジトリでパッケージングする。** 分離すると決定の連鎖が断ち切られる。

## ルールの階層・抽象度

共通ルールの抽象度レベルと重複チェックは `HIERARCHY.md` を参照。L3（UUID v4）→ L4（属性・射）→ L5（プロジェクト）の順で適用する。

## ルール一覧

| ファイル | 説明 |
|----------|------|
| `tanaakk-universal-schema.mdc` | Universal Data Architecture。規格階層（L4A/L4B/L4C）、UUID v4、会計API連携、クロスドメイン結合 |
| `tanaakk-uuid-hybrid.mdc` | UUID v4/v7 ハイブリッド（デジタルツイン・イベント発行、計算資源節約のスキーマ構成） |
| `70_uuid-classification-rules/` | 業種別ケーススタディ（製造小売業、不動産・建設業の v4/v7/採番なし 分類） |
| `tanaakk-saas-procedure.mdc` | TANAAKK SaaS 標準プロシージャ（ドメイン先行・UI 先行 v1.0.0 リリース） |
| `tanaakk-api-first.mdc` | API First / Schema First の開発ワークフロー指針 |
| `tanaakk-url-sitemap-seo.mdc` | URL・サイトマップの階層化・命名規則（SEO、日本語パス禁止） |
| `tanaakk-multi-cloud-iam.mdc` | マルチクラウド IAM 標準（Alibaba/AWS/GCP/Azure 非依存） |
| `tanaakk-security.mdc` | セキュリティ（OWASP ASVS・MITRE ATT&CK、Form & Password） |
| `tanaakk-dependency-security.mdc` | 依存関係セキュリティ（GitHub Security Critical/High/Moderate 事前防止） |
| `tanaakk-secrets-management.mdc` | シークレット管理統一ルール（.env.example、GitHub Secret Scanning、pre-commit） |
| `tanaakk-vehicle-geospatial.mdc` | 車両DB・位置情報・建設・FMの汎用スキーマ |
| `tanaakk-physical-branding-sku.mdc` | 物理ブランディング・SKU（UUID 中核、デジタルツイン）。貴金属・宝石・鉱物・宝石学・繊維・元素・宇宙機・時計・メティエダール・発電・保険・金融・石油・ガス・医療・農業・食品・Fauna・Flora・Marine life（ミュージオロジー）の規格 |
| `tanaakk-mes-manufacturing.mdc` | MES・縫製・製造（インナーウェア、刺繍糸かせとりき等）の汎用スキーマ |
| `tanaakk-amazon-sponsored-ads.mdc` | Amazon VC/SC 前提の Sponsored Products キーワード探索→3日判定→勝ち残し運用（在庫≥5ゲート） |
| `tanaakk-language-selection.mdc` | 言語・フレームワーク選択指針 |
| `tanaakk-ui-ux.mdc` | 共通UI/UX（カラー・タイポ・アクセシビリティ） |
| `tanaakk-responsive-first.mdc` | マルチデバイス対応・レスポンシブファースト規則（W3C/WCAG/web.dev 準拠） |

## 概念・補足ドキュメント

| ファイル | 説明 |
|----------|------|
| `01_IO_Specification.md` | I/O Specification の定義と本リポジトリの想定 I/O |
| `04_Repository_Relationships.md` | 5 層フレームワーク対応リポジトリ一覧 |
| `05_Folder_Structure_Convention.md` | 5 リポジトリ統一フォルダ構成・命名規則 |
| `06_Universal_Schema_Concept.md` | ユニバーサルスキーマの概念体系、理論と実装のギャップ |
| `07_TANAAKK_Engineering_Methodology.md` | 従来型 vs TANAAKK 流のエンジニアリング対比（規格準拠の説明、同期モデル、理論と実装） |
| `docs/10_Responsive_First_Rules.md` | マルチデバイス対応・レスポンシブファースト規則（ブレークポイント、タッチターゲット、検証チェックリスト） |
| `docs/11_HST_Basic_Concepts.md` | HST 原則の参照（正本は [holographic-sphere-topology](https://github.com/tanaakk/holographic-sphere-topology)） |

## 8 リポジトリ構造

8 つのリポジトリが一つの広域系を形成している。本リポジトリ（universal-guideline）はその一部である。

| リポジトリ | リンク |
|-----------|--------|
| universal-guideline | [github.com/tanaakk/universal-guideline](https://github.com/tanaakk/universal-guideline) |
| holographic-sphere-topology | [github.com/tanaakk/holographic-sphere-topology](https://github.com/tanaakk/holographic-sphere-topology) |
| GAAS-dissipative-constraints | [github.com/tanaakk/GAAS-dissipative-constraints](https://github.com/tanaakk/GAAS-dissipative-constraints) |
| complex-physics-scale | [github.com/tanaakk/complex-physics-scale](https://github.com/tanaakk/complex-physics-scale) |
| law-of-scale-verificator | [github.com/tanaakk/law-of-scale-verificator](https://github.com/tanaakk/law-of-scale-verificator) |
| homotopical-coherence-engine | [github.com/tanaakk/homotopical-coherence-engine](https://github.com/tanaakk/homotopical-coherence-engine) |
| intangibles-valuation-logic | [github.com/tanaakk/intangibles-valuation-logic](https://github.com/tanaakk/intangibles-valuation-logic) |
| operating-leverage-identifier | [github.com/tanaakk/operating-leverage-identifier](https://github.com/tanaakk/operating-leverage-identifier) |

## GAAS Hands-on ワークスペース

8 リポジトリを一括で開くには `gaas-hands-on.code-workspace` を使用する。**フォルダとして開いた場合**、[Auto-Open Workspace](https://marketplace.visualstudio.com/items?itemName=zoma.vscode-auto-open-workspace) 拡張（推奨）が起動時に QuickPick でワークスペースへの切り替えを案内する。詳細は `.vscode/README_workspace.md` を参照。

## 使い方

### プロジェクトに追加

各アプリの `.cursor/rules/` にこのフォルダの `*.mdc` をコピーするか、Git サブモジュールとして追加：

```bash
git submodule add https://github.com/tanaakk/universal-guideline.git .cursor/rules
```

### User Rules に貼る

`user-rules-copy-paste.md` の完全版を Cursor Settings > Rules for AI にコピー＆ペースト。
