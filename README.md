# TANAAKK Cursor Rules

TANAAKKグループが提供する全アプリで共通利用する Cursor AI ルールです。このレポジトリはPublicです。

## コンセプト

この Universal Rule は**逐次アップデート**される。

- **地球のベストプラクティス**: 最新時点での業界標準（Google AIP、Microsoft、IANA、会計API連携等）を採用し、随時更新する。
- **多惑星文明のベストプラクティス**: NASA/ホワイトハウス Celestial Time Standardization Policy、Coordinated Lunar Time (LTC)、火星時間等、重力圏に応じた抽象時間・参照系の標準が策定・普及するに従い、それらを取り込んで更新する。

## 階層・抽象度

共通ルールの抽象度レベルと重複チェックは `HIERARCHY.md` を参照。L0（基盤）→ L1（横断）→ L2/L3（ドメイン）の順で適用する。

## ルール一覧

| ファイル | 説明 |
|----------|------|
| `tanaakk-universal-schema.mdc` | Universal Data Architecture（Industry-Agnostic）、UUID v4、会計API連携、クロスドメイン結合 |
| `tanaakk-api-first.mdc` | API First / Schema First の開発ワークフロー指針 |
| `tanaakk-url-sitemap-seo.mdc` | URL・サイトマップの階層化・命名規則（SEO、日本語パス禁止） |
| `tanaakk-multi-cloud-iam.mdc` | マルチクラウド IAM 標準（Alibaba/AWS/GCP/Azure 非依存） |
| `tanaakk-security.mdc` | セキュリティ（OWASP ASVS・MITRE ATT&CK、Form & Password） |
| `tanaakk-vehicle-geospatial.mdc` | 車両DB・位置情報・建設・FMの汎用スキーマ |
| `tanaakk-physical-branding-sku.mdc` | 物理ブランディング・SKU（UUID 中核、デジタルツインモデル） |
| `tanaakk-mes-manufacturing.mdc` | MES・縫製・製造（インナーウェア、刺繍糸かせとりき等）の汎用スキーマ |
| `tanaakk-language-selection.mdc` | 言語・フレームワーク選択指針 |
| `tanaakk-ui-ux.mdc` | 共通UI/UX（カラー・タイポ・アクセシビリティ） |

## 使い方

### プロジェクトに追加

各アプリの `.cursor/rules/` にこのフォルダの `*.mdc` をコピーするか、Git サブモジュールとして追加：

```bash
git submodule add https://github.com/tanaakk/universal-guideline.git .cursor/rules
```

### User Rules に貼る

`user-rules-copy-paste.md` の完全版を Cursor Settings > Rules for AI にコピー＆ペースト。
