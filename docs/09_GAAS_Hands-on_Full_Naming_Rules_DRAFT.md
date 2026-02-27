# 09_GAAS_Hands-on_Full_Naming_Rules_DRAFT

7 リポジトリ統一の**フル命名規則**（ファイル・フォルダ・読む順序）。既存フォルダを含め、番号で一貫して整理する。

**ステータス**: DRAFT（2026-02-27）

---

## 0. 参照フレームワーク（Reference Frameworks）

本命名規則は以下の国際規格・業界慣行を参照する。

| フレームワーク | 用途 | 参照 |
|----------------|------|------|
| **ISO 2145:1978** | 文書の章・節の番号付け（1, 2.1, 2.1.1） | [ISO 2145](https://www.iso.org/standard/6937.html) |
| **ISO 8601** | 日付プレフィックス（YYYY-MM-DD）による時系列ソート | [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) |
| **golang-standards/project-layout** | cmd, internal, pkg, api, build, scripts の配置 | [GitHub](https://github.com/golang-standards/project-layout) |
| **Go internal 規約** | 外部 import 不可のパッケージ境界 | [Go 公式](https://go.dev/doc/modules/layout) |
| **GitHub Best Practices** | README, 浅い階層、説明的な名前 | [GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/best-practices-for-repositories) |
| **DPC File Naming** | ファイル命名のベストプラクティス（日付+内容、特殊文字回避） | [Digital Preservation Coalition](https://www.dpconline.org/docs/dpc-technology-watch-publications) |

### 0.1 分類軸（golang-standards 準拠）

| 分類 | フォルダ | 役割 |
|------|----------|------|
| **内部ロジック** | internal/, src/ | フレームワーク・アプリ固有の実装 |
| **ビルド** | build/, scripts/, configs/ | ビルド・CI・パッケージング |
| **外部 API** | api/, pkg/, schemas/ | 外部向け API 定義・公開ライブラリ |
| **外部通信** | clients/, adapters/, integrations/ | 外部サービスとの接続 |

---

## 1. 番号体系の全体像

```
00-09: ルート直下 中核ドキュメント（NN_*.md）
10-19: ルート直下 補足フォルダ / docs 内 番号付きファイル（NN-*.md）
20-29: ルート直下 コード・アーティファクトフォルダ
30-39: リポジトリ固有フォルダ
40-99: 予約・拡張
```

---

## 2. ルート直下ファイル（NN_<Name>.md）

| NN | 用途 | 全リポジトリ | 備考 |
|----|------|-------------|------|
| **00** | 中核概要 | 必須 | 読む順序の起点。各リポジトリ1本 |
| **01** | 中核ドキュメント第1 | 任意 | リポジトリ依存 |
| **02** | 中核ドキュメント第2 | 任意 | リポジトリ依存 |
| **03** | 中核ドキュメント第3 | 任意 | リポジトリ依存 |
| **04** | Repository Relationships | **共通** | 04_Repository_Relationships.md（固定） |
| **05** | Folder Structure Convention | **共通** | 05_Folder_Structure_Convention.md（固定） |
| **06** | Universal Schema Concept | **共通** | 06_Universal_Schema_Concept.md（固定） |
| **07** | リポジトリ固有補足 | 任意 | 例: 07_TANAAKK_Engineering_Methodology |
| **08** | リポジトリ固有補足 | 任意 | 例: 08_GAAS_Hands-on_7Repo_Naming_Rules |
| **09** | リポジトリ固有補足 | 任意 | 例: 09_GAAS_Hands-on_Full_Naming_Rules |

---

## 3. ルート直下フォルダ（NN_<name>/ または 標準名）

### 3.1 番号付きフォルダ（推奨）※ golang-standards 分類対応

| NN | フォルダ名 | 分類軸 | 用途 | 存在リポジトリ |
|----|-----------|--------|------|----------------|
| **10** | 10_docs | ドキュメント | 補足ドキュメント | 全リポジトリ（必要時） |
| **20** | 20_api | 外部 API | API 定義・OpenAPI・スキーマ | HCE 等 |
| **25** | 25_schemas | 外部 API | JSON Schema 等 | HCE |
| **30** | 30_internal | 内部ロジック | フレームワーク固有実装 | HCE, OLI |
| **35** | 35_src | 内部ロジック | ソースコード（src 互換） | HCE, OLI |
| **40** | 40_build | ビルド | ビルド・CI・パッケージング | complex-physics-scale |
| **45** | 45_scripts | ビルド | 自動化スクリプト | complex-physics-scale |
| **50** | 50_clients | 外部通信 | 外部 API クライアント・アダプター | 必要時 |
| **55** | 55_examples | 外部 API | サンプル・実行例 | OLI |
| **60** | 60_tests | ビルド | テスト | OLI |
| **70** | 70_uuid-classification-rules | リポジトリ固有 | 業種別 UUID 採番ルール | universal-guideline |

### 3.2 標準フォルダ（番号なし・ツール互換）

ビルドツール・パッケージマネージャが参照するため、**番号なし**を許容する。golang-standards の cmd, internal, pkg, api, build に対応。

| 標準名 | 分類軸 | 番号付き代替 |
|--------|--------|-------------|
| docs/ | ドキュメント | 10_docs/ |
| api/ | 外部 API | 20_api/ |
| schemas/ | 外部 API | 25_schemas/ |
| internal/ | 内部ロジック | 30_internal/ |
| src/ | 内部ロジック | 35_src/ |
| build/ | ビルド | 40_build/ |
| scripts/ | ビルド | 45_scripts/ |
| clients/ | 外部通信 | 50_clients/ |
| examples/ | 外部 API | 55_examples/ |
| tests/ | ビルド | 60_tests/ |
| .cursor/rules/ | — | 番号なし（隠しフォルダ） |

**ルール**: 新規リポジトリは番号付き（10_docs, 30_internal, 40_build 等）を推奨。既存リポジトリは移行時に番号付きへ統一可能。

---

## 4. docs/ 内ファイル（NN-<kebab-case>.md または UPPER_SNAKE.md）

### 4.1 番号付き（読む順序あり）

| NN | 用途 | 例 |
|----|------|-----|
| **10** | 仕様・マトリクス・チェックリスト | 10-categories-matrix.md, 10-operating-leverage-identifier-spec.md |
| **11** | 検証・整合性 | 11-verification-checklist.md, 11-cash-flow-definition-alignment.md |
| **12** | 場合分け・分類 | 12-intangibles-valuation-case-classification.md |
| **13-19** | その他補足 | 必要に応じて |

### 4.2 UPPER_SNAKE（順序なし・参照用）

| パターン | 用途 | 例 |
|----------|------|-----|
| UPPER_SNAKE.md | アーキテクチャ・ホワイトペーパー | ARCHITECTURE.md, WHITEPAPER.md, META_FRAMEWORK.md |

---

## 5. 7 リポジトリ別 フルマッピング（現状 → 推奨）

### 5.1 universal-guideline

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | 04, 05, 06, 07, HIERARCHY, README, tanaakk-*.mdc | 00_Overview.md 追加、04-08 維持 | ISO 2145 |
| ルート | docs/ | 10_docs/ または docs/ 維持 | GitHub Best Practices |
| ルート | uuid-classification-rules/ | **70_uuid-classification-rules/** | リポジトリ固有 |
| docs | 08, 09 ドラフト | docs に配置 | ISO 2145 |
| 70_uuid-classification-rules | README, manufacturing-retail, real-estate-construction | 10_README.md, 20_*.md, 30_*.md（任意） | ISO 2145 |

### 5.2 GAAS-dissipative-constraints

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | 04, 05, 06, README | 00_Dissipative_Constraints.md 追加、04-06 維持 | ISO 2145 |
| ルート | .cursor/rules/ | 維持（番号なし） | — |

### 5.3 complex-physics-scale（Canonical）

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | 00_Meta_Framework, 00_Screening, 01-06 | 00_Screening → **01_Screening** にリネーム | ISO 2145 |
| ルート | scripts/ | **45_scripts/** または scripts/ 維持 | golang-standards build |
| 45_scripts | sync-repository-relationships.sh | 維持 | — |

### 5.4 law-of-scale-verificator

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | 04, 05, 06, tanaakk-*.mdc | 00_Law_of_Scale.md 追加、04-06 維持 | ISO 2145 |
| ルート | docs/ | 10_docs/ または docs/ 維持 | GitHub Best Practices |
| docs | 10-categories-matrix.md | ✓ 維持 | ISO 2145 NN- |
| docs | verification-checklist.md | **11-verification-checklist.md** | ISO 2145 NN- |

### 5.5 homotopical-coherence-engine

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | 04, 05, 06 | 00_HCE_Overview.md 追加、04-06 維持 | ISO 2145 |
| ルート | docs/ | 10_docs/ または docs/ 維持 | GitHub Best Practices |
| ルート | schemas/, src/ | **25_schemas/** (api), **35_src/** (internal) または維持 | golang-standards |
| docs | ARCHITECTURE, META_FRAMEWORK, WHITEPAPER 等 | UPPER_SNAKE 維持（番号付きは任意） | DPC File Naming |

### 5.6 intangibles-valuation-logic

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | README のみ | 00_Intangibles_Valuation_Overview.md, 04, 05, 06 追加 | ISO 2145 |
| ルート | docs/ | 10_docs/ または docs/ 維持 | GitHub Best Practices |
| docs | intangibles-valuation-logic-case-classification.md | **12-intangibles-valuation-case-classification.md** | ISO 2145 NN- |

### 5.7 operating-leverage-identifier

| 種別 | 現状 | 推奨 | 参照フレームワーク |
|------|------|------|-------------------|
| ルート | README, pyproject.toml 等 | 00_Operating_Leverage_Overview.md, 04, 05, 06 追加 | ISO 2145 |
| ルート | docs/ | 10_docs/ または docs/ 維持 | GitHub Best Practices |
| ルート | src/, examples/, tests/ | **35_src/** (internal), **55_examples/** (api), **60_tests/** (build) または維持 | golang-standards |
| docs | operating-leverage-identifier-spec.md | **10-operating-leverage-identifier-spec.md** | ISO 2145 NN- |
| docs | cash-flow-definition-alignment.md | **11-cash-flow-definition-alignment.md** | ISO 2145 NN- |

---

## 6. フォルダ番号の割り当てロジック（参照フレームワーク準拠）

```
10: ドキュメント（docs）              ← GitHub Best Practices
20: 外部 API（api, schemas）          ← golang-standards /api
25: スキーマ・型定義（schemas）
30: 内部ロジック（internal）          ← Go internal 規約
35: ソースコード（src）
40: ビルド（build）                  ← golang-standards /build
45: スクリプト・自動化（scripts）
50: 外部通信（clients）              ← golang-standards clients/adapters
55: サンプル・例（examples）
60: テスト（tests）
70-99: リポジトリ固有の拡張
```

**例外**: ツールが固定パスを参照する場合（pyproject.toml の `packages = [{find = {where = ["src"]}}]` 等）は、**番号なしの標準名を維持**する。

---

## 7. 70_uuid-classification-rules 内の番号（任意）

| NN | 用途 | 例 |
|----|------|-----|
| 10 | フォルダ概要 | 10_README.md |
| 20 | 業種別ルール第1 | 20_manufacturing-retail.md |
| 30 | 業種別ルール第2 | 30_real-estate-construction.md |
| 40-99 | 追加業種 | 40_<industry>.md |

---

## 8. 移行チェックリスト（7 リポジトリ）

| 優先度 | 対象 | 作業 |
|--------|------|------|
| **P0** | intangibles, OLI | 04, 05, 06 追加、docs 内 NN- 統一 |
| **P1** | 全リポジトリ | 00_*.md 新規作成 |
| **P2** | universal-guideline | uuid-classification-rules → 70_uuid-classification-rules |
| **P3** | law-of-scale | verification-checklist → 11-verification-checklist |
| **P4** | complex-physics-scale | 00_Screening → 01_Screening |
| **P5** | 新規リポジトリ | 10_docs, 40_src 等の番号付きフォルダを採用 |

---

## 9. 参照フレームワーク一覧（7 リポジトリ適用）

| リポジトリ | ISO 2145 | ISO 8601 | golang-standards | GitHub BP |
|-----------|----------|----------|------------------|-----------|
| universal-guideline | 00-08, 70_内 NN_ | 任意（日付付き doc） | — | docs, README |
| GAAS-dissipative-constraints | 00, 04-06 | 任意 | — | README |
| complex-physics-scale | 00-06 | 任意 | scripts→45, build | docs |
| law-of-scale-verificator | 00, 04-06, docs NN- | 任意 | — | docs |
| homotopical-coherence-engine | 00, 04-06 | 任意 | schemas→25, src→35 | docs |
| intangibles-valuation-logic | 00, 04-06, docs NN- | 任意 | — | docs |
| operating-leverage-identifier | 00, 04-06, docs NN- | 任意 | src→35, examples→55, tests→60 | docs |

---

## 10. 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2026-02-27 | 初版作成（フル命名規則ドラフト） |
| 2026-02-27 | 参照フレームワーク追加（ISO 2145, ISO 8601, golang-standards, GitHub BP, DPC）、7 リポジトリ適用 |
