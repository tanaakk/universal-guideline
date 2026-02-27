# 08_GAAS_Hands-on_7Repo_Naming_Rules_DRAFT

7 リポジトリ統一のフォルダ・ファイル命名ルール（ドラフト）。`05_Folder_Structure_Convention.md` を 7 リポジトリに拡張する。

**ステータス**: DRAFT（2026-02-27）

---

## 0. 参照フレームワーク

| フレームワーク | 用途 |
|----------------|------|
| ISO 2145:1978 | 文書の章・節番号（1, 2.1, 2.1.1） |
| ISO 8601 | 日付プレフィックス（YYYY-MM-DD） |
| [golang-standards/project-layout](https://github.com/golang-standards/project-layout) | cmd, internal, pkg, api, build, scripts |
| [GitHub Best Practices](https://docs.github.com/en/repositories/creating-and-managing-repositories/best-practices-for-repositories) | README, 浅い階層 |

詳細は `09_GAAS_Hands-on_Full_Naming_Rules_DRAFT.md` を参照。

---

## 1. 7 リポジトリ現状サマリ

| # | リポジトリ | ルート番号付き | docs/ | 備考 |
|---|-----------|----------------|-------|------|
| 1 | universal-guideline | 04, 05, 06, 07 | なし | tanaakk-*.mdc 多数、uuid-classification-rules/ |
| 2 | GAAS-dissipative-constraints | 04, 05, 06 | なし | 最小構成 |
| 3 | complex-physics-scale | **00, 01, 02, 03, 04, 05, 06** | なし | **Canonical**（参照モデル） |
| 4 | law-of-scale-verificator | 04, 05, 06 | 10-categories-matrix, verification-checklist | tanaakk-*.mdc |
| 5 | homotopical-coherence-engine | 04, 05, 06 | ARCHITECTURE, META_FRAMEWORK, WHITEPAPER 等 | src/, schemas/ |
| 6 | intangibles-valuation-logic | なし | intangibles-valuation-logic-case-classification | 最小構成 |
| 7 | operating-leverage-identifier | なし | spec, cash-flow-definition-alignment | src/, examples/, tests/ |

---

## 2. 番号付き命名ルール（NN_ / NN-）

### 2.1 ルート直下（NN_<Name>.md）

| NN | 用途 | 配置 | 備考 |
|----|------|------|------|
| **00** | 各リポジトリの中核概要 | 全リポジトリ | 読む順序の起点。README の要約または拡張 |
| **01** | レイヤー2: 中核の第1ドキュメント | リポジトリ依存 | 例: 01_Hardware_Mass_Production_Model |
| **02** | レイヤー3: 中核の第2ドキュメント | リポジトリ依存 | 例: 02_Regulatory_Compliance |
| **03** | レイヤー4: 中核の第3ドキュメント | リポジトリ依存 | 例: 03_Verification_Checklist |
| **04** | **リポジトリ対応関係** | **全 7 リポジトリ共通** | 04_Repository_Relationships.md（固定） |
| **05** | **フォルダ構成・命名規則** | **全 7 リポジトリ共通** | 05_Folder_Structure_Convention.md（固定） |
| **06** | **ユニバーサルスキーマ概念** | **全 7 リポジトリ共通** | 06_Universal_Schema_Concept.md（固定） |
| **07** | リポジトリ固有の補足 | 任意 | 例: 07_TANAAKK_Engineering_Methodology |
| **08** | リポジトリ固有の補足 | 任意 | 例: 08_GAAS_Hands-on_7Repo_Naming_Rules |

### 2.2 docs/ 内（NN-<kebab-case>.md または UPPER_SNAKE.md）

| パターン | 用途 | 例 |
|----------|------|-----|
| `NN-<kebab-case>.md` | 番号付き補足（読む順序あり） | `10-categories-matrix.md`, `11-verification-checklist.md` |
| `UPPER_SNAKE.md` | アーキテクチャ・ホワイトペーパー（順序なし） | `ARCHITECTURE.md`, `WHITEPAPER.md`, `META_FRAMEWORK.md` |

---

## 3. リポジトリ別 00_〜03_ マッピング（推奨）

### 3.1 universal-guideline（L1: 空間基底）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_Overview.md | なし | 新規作成（README から分離） |
| 01 | — | — | 不要（tanaakk-*.mdc が主役） |
| 02 | — | — | 不要 |
| 03 | — | — | 不要 |
| 04 | 04_Repository_Relationships.md | ✓ | 維持 |
| 05 | 05_Folder_Structure_Convention.md | ✓ | 維持 |
| 06 | 06_Universal_Schema_Concept.md | ✓ | 維持 |
| 07 | 07_TANAAKK_Engineering_Methodology.md | ✓ | 維持 |

### 3.2 GAAS-dissipative-constraints（L2: 散逸機構）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_Dissipative_Constraints.md | なし | 新規作成（README 内容を集約） |
| 01 | — | — | 任意 |
| 02 | — | — | 任意 |
| 03 | — | — | 任意 |
| 04 | 04_Repository_Relationships.md | ✓ | 維持 |
| 05 | 05_Folder_Structure_Convention.md | ✓ | 維持 |
| 06 | 06_Universal_Schema_Concept.md | ✓ | 維持 |

### 3.3 complex-physics-scale（L3: Canonical）※ 参照モデル

| NN | ファイル名 | 現状 | 備考 |
|----|-----------|------|------|
| 00 | 00_Meta_Framework.md | ✓ | 5層メタフレームワーク |
| 00 | 00_Screening.md | ✓ | 力学スクリーニング（00 重複） |
| 01 | 01_Hardware_Mass_Production_Model.md | ✓ | PLOG / P&L / DFP |
| 02 | 02_Regulatory_Compliance_US_JP_DE.md | ✓ | 法令適合 |
| 03 | 03_Verification_Checklist.md | ✓ | 検証チェックリスト |
| 04 | 04_Repository_Relationships.md | ✓ | 共通 |
| 05 | 05_Folder_Structure_Convention.md | ✓ | 共通 |
| 06 | 06_Universal_Schema_Concept.md | ✓ | 共通 |

※ 00 が2本ある（00_Meta_Framework, 00_Screening）→ 01_Screening へのリネーム検討

### 3.4 law-of-scale-verificator（L4: 系の残存・拡張）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_Law_of_Scale.md | なし | 新規作成（LSV 概要、PLOG、Design Auth Key） |
| 01 | — | — | 任意 |
| 02 | — | — | 任意 |
| 03 | — | — | 任意 |
| 04 | 04_Repository_Relationships.md | ✓ | 維持 |
| 05 | 05_Folder_Structure_Convention.md | ✓ | 維持 |
| 06 | 06_Universal_Schema_Concept.md | ✓ | 維持 |
| docs | 10-categories-matrix.md | ✓ | 維持 |
| docs | 11-verification-checklist.md | — | verification-checklist → 11- にリネーム検討 |

### 3.5 homotopical-coherence-engine（L5: 特異点突破）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_HCE_Overview.md | なし | 新規作成（docs/META_FRAMEWORK からの要約） |
| 01 | — | — | 任意 |
| 02 | — | — | 任意 |
| 03 | — | — | 任意 |
| 04 | 04_Repository_Relationships.md | ✓ | 維持 |
| 05 | 05_Folder_Structure_Convention.md | ✓ | 維持 |
| 06 | 06_Universal_Schema_Concept.md | ✓ | 維持 |
| docs | ARCHITECTURE.md, WHITEPAPER.md 等 | ✓ | UPPER_SNAKE 維持 |

### 3.6 intangibles-valuation-logic（財務・バリュエーション）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_Intangibles_Valuation_Overview.md | なし | 新規作成（README 拡張） |
| 01 | — | — | 任意 |
| 02 | — | — | 任意 |
| 03 | — | — | 任意 |
| 04 | 04_Repository_Relationships.md | なし | 追加（7 リポジトリ版に更新） |
| 05 | 05_Folder_Structure_Convention.md | なし | 追加（7 リポジトリ版に更新） |
| 06 | 06_Universal_Schema_Concept.md | なし | 追加（他リポジトリからコピー） |
| docs | 10-intangibles-valuation-case-classification.md | intangibles-valuation-logic-case-classification.md | リネーム検討 |

### 3.7 operating-leverage-identifier（ROIC スクリーナー）

| NN | 推奨ファイル名 | 現状 | アクション |
|----|----------------|------|------------|
| 00 | 00_Operating_Leverage_Overview.md | なし | 新規作成（README 拡張） |
| 01 | — | — | 任意 |
| 02 | — | — | 任意 |
| 03 | — | — | 任意 |
| 04 | 04_Repository_Relationships.md | なし | 追加（7 リポジトリ版に更新） |
| 05 | 05_Folder_Structure_Convention.md | なし | 追加（7 リポジトリ版に更新） |
| 06 | 06_Universal_Schema_Concept.md | なし | 追加（他リポジトリからコピー） |
| docs | 10-operating-leverage-identifier-spec.md | operating-leverage-identifier-spec.md | ルート or docs に 10- プレフィックス |
| docs | 11-cash-flow-definition-alignment.md | cash-flow-definition-alignment.md | 同上 |

---

## 4. 命名ロジック（決定ルール）

### 4.1 NN の割り当てロジック

```
00: 必ず各リポジトリに1本。中核概要。読む順序の起点。
01-03: リポジトリ固有。中核ドキュメントが複数ある場合に順次割り当て。
04: 固定。Repository Relationships。全リポジトリ共通。
05: 固定。Folder Structure Convention。全リポジトリ共通。
06: 固定。Universal Schema Concept。全リポジトリ共通。
07-99: リポジトリ固有の補足。必要に応じて割り当て。
```

### 4.2 docs/ 内の NN-

```
10-19: 仕様・マトリクス・チェックリスト（読む順序あり）
20-99: その他補足
UPPER_SNAKE: アーキテクチャ・ホワイトペーパー（順序なし、大文字スネーク）
```

### 4.3 フォルダ命名（ディレクトリ）

| パターン | 用途 | 例 |
|----------|------|-----|
| `uuid-classification-rules/` | 業種別ルール集 | universal-guideline |
| `docs/` | 補足ドキュメント | 全リポジトリ |
| `schemas/` | JSON Schema 等 | homotopical-coherence-engine |
| `scripts/` | 自動化スクリプト | complex-physics-scale |
| `src/` | ソースコード | HCE, OLI |
| `examples/` | サンプル | operating-leverage-identifier |
| `tests/` | テスト | operating-leverage-identifier |
| `.cursor/rules/` | Cursor .mdc | 全リポジトリ推奨 |

---

## 5. 移行優先順位（7 リポジトリ）

| 優先度 | 対象 | 作業 |
|--------|------|------|
| **P0** | intangibles, operating-leverage | 04, 05, 06 を追加（7 リポジトリ版） |
| **P1** | GAAS, law-of-scale, HCE, intangibles, OLI | 00_*.md を新規作成 |
| **P2** | universal-guideline | 00_Overview.md を新規作成 |
| **P3** | law-of-scale, intangibles, OLI | docs/ の NN- プレフィックス統一 |
| **P4** | complex-physics-scale | 00_Screening → 01_Screening リネーム検討 |

---

## 6. 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2026-02-27 | 初版作成（7 リポジトリ命名ルールドラフト） |
