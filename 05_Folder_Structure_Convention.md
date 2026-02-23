# 05_Folder_Structure_Convention — 5 リポジトリ統一フォルダ構成・命名規則

本ドキュメントは、5 層メタフレームワークに対応する **5 リポジトリ全体**で共通するフォルダ構成と命名規則を定義する。Canonical Source は [complex-physics-scale](https://github.com/tanaakk/complex-physics-scale)。

**Framework version**: v2.1.1（統一案の初版）

---

## 1. 統一ディレクトリ階層

```
<repo-root>/
├── .cursor/
│   └── rules/                    # Cursor ルール（*.mdc）
├── docs/                         # 補足ドキュメント（任意）
├── schemas/                      # JSON Schema 等（任意、HCE 等）
├── scripts/                      # 自動化スクリプト（任意）
├── src/                          # ソースコード（任意、HCE 等）
│
├── .cursorrules                  # Cursor メインルール（全ファイル適用）
├── .gitignore                    # 必要に応じて
├── 00_<Layer1>.md                # レイヤー1: 中核ドキュメント（番号付き）
├── 01_<Layer2>.md
├── 02_<Layer3>.md
├── ...
├── 04_Repository_Relationships.md # 5 リポジトリ対応関係（全リポジトリ共通）
├── CHANGELOG.md                  # 変更履歴（任意）
├── HIERARCHY.md                  # 階層・抽象度定義（universal-guideline 等）
├── LICENSE
├── package.json                  # 必要に応じて
├── README.md
├── user-rules-copy-paste.md      # User Rules 用（任意）
└── tanaakk-<domain>.mdc          # ドメイン別ルール（.cursor/rules/ に置く場合も可）
```

---

## 2. 命名規則

### 2.1 中核ドキュメント（Markdown）

| パターン | 用途 | 例 |
|----------|------|-----|
| `NN_<Name>.md` | 番号付き中核ドキュメント。`NN` は 2 桁（00–99）。読む順序を明示 | `00_Meta_Framework.md`, `01_Hardware_Mass_Production_Model.md` |
| `04_Repository_Relationships.md` | **全 5 リポジトリで共通**。sync スクリプトで同期 | 固定 |
| `HIERARCHY.md` | ルールの階層・抽象度。L0→L1→L2 の適用順 | universal-guideline, law-of-scale-verificator |
| `CHANGELOG.md` | バージョン別変更履歴 | law-of-scale-verificator, homotopical-coherence-engine |

### 2.2 Cursor ルール（.mdc）

| パターン | 用途 | 例 |
|----------|------|-----|
| `tanaakk-<domain>.mdc` | ドメイン別ルール。`<domain>` はハイフン区切り | `tanaakk-universal-schema.mdc`, `tanaakk-api-first.mdc` |
| `<repo>-<name>.mdc` | リポジトリ固有ルール | `tanaakk-complex-physics-scale.mdc`, `gaas-dissipative-constraints.mdc` |

### 2.3 補足ドキュメント（docs/）

| パターン | 用途 | 例 |
|----------|------|-----|
| `NN-<kebab-case>.md` | 番号付き補足 | `10-categories-matrix.md`, `verification-checklist.md` |
| `UPPER_SNAKE.md` | アーキテクチャ・ホワイトペーパー | `ARCHITECTURE.md`, `WHITEPAPER.md`, `META_FRAMEWORK.md` |

---

## 3. リポジトリ別推奨構成

### 3.1 universal-guideline（L1: 空間基底）

| 現状 | 推奨 | 備考 |
|------|------|------|
| フラットに tanaakk-*.mdc | `00_Overview.md` 新規、`tanaakk-*.mdc` は `.cursor/rules/` へ移動 or 維持 | 番号付き doc は 00 のみで可 |
| HIERARCHY.md | 維持 | L0→L3 の適用順を定義 |
| 04_Repository_Relationships.md | 維持 | sync で同期 |

**推奨構成**:
```
universal-guideline/
├── .cursor/rules/           # tanaakk-*.mdc をここに集約（オプション）
├── 00_Overview.md          # 規格 3 層構造の概要（README から分離）
├── 04_Repository_Relationships.md
├── HIERARCHY.md
├── LICENSE
├── README.md
├── user-rules-copy-paste.md
└── tanaakk-*.mdc           # 現状維持でも可
```

### 3.2 GAAS-dissipative-constraints（L2: 散逸機構）

| 現状 | 推奨 | 備考 |
|------|------|------|
| 最小構成 | `00_Dissipative_Constraints.md` 新規、README の内容を集約 | complex-physics-scale の 00_ スタイルに合わせる |
| .cursor/rules/ | 維持 | gaas-dissipative-constraints.mdc |

**推奨構成**:
```
GAAS-dissipative-constraints/
├── .cursor/rules/gaas-dissipative-constraints.mdc
├── 00_Dissipative_Constraints.md   # 散逸構造の公理、適用条件
├── 04_Repository_Relationships.md
├── LICENSE
└── README.md
```

### 3.3 complex-physics-scale（L3: 系の成立パターン）※ Canonical

| 現状 | 推奨 | 備考 |
|------|------|------|
| 00_–04_ 番号付き | **維持** | 既に統一規則に準拠 |
| scripts/ | 維持 | sync スクリプト |

**現状のまま** が参照モデル。

### 3.4 law-of-scale-verificator（L4: 系の残存・拡張）

| 現状 | 推奨 | 備考 |
|------|------|------|
| docs/ に補足 | `00_Law_of_Scale.md` 新規、docs は `docs/NN-*.md` に整理 | 番号付きで L3 と一貫 |
| tanaakk-*.mdc がルート | `.cursor/rules/` へ移動 | 他リポジトリと統一 |

**推奨構成**:
```
law-of-scale-verificator/
├── .cursor/rules/
│   ├── tanaakk-design-verification-data.mdc
│   └── tanaakk-statement-perfection-verificator.mdc
├── docs/
│   ├── 10-categories-matrix.md
│   └── verification-checklist.md
├── 00_Law_of_Scale.md           # LSV 概要、PLOG、Design Auth Key
├── 04_Repository_Relationships.md
├── CHANGELOG.md
├── HIERARCHY.md
├── LICENSE
├── README.md
└── user-rules-copy-paste.md
```

### 3.5 homotopical-coherence-engine（L5: 特異点突破）

| 現状 | 推奨 | 備考 |
|------|------|------|
| docs/, src/, schemas/ | 維持 | コードベースのため現状で妥当 |
| docs/META_FRAMEWORK.md | `00_Meta_Framework.md` にリネーム or シンボリックリンク | ルートに 00_ を置く |
| .cursor/rules/*.mdc | 維持 | ドメイン別ルール多数 |

**推奨構成**:
```
homotopical-coherence-engine/
├── .cursor/rules/*.mdc
├── docs/
│   ├── ARCHITECTURE.md
│   ├── META_FRAMEWORK.md
│   ├── WHITEPAPER.md
│   └── ...
├── schemas/
├── src/
├── 00_HCE_Overview.md           # ルートに 00_ を追加（docs からの要約）
├── 04_Repository_Relationships.md
├── LICENSE
├── README.md
└── package.json
```

---

## 4. 共通ルール一覧

| ルール | 内容 |
|--------|------|
| **04 は全リポジトリ共通** | `04_Repository_Relationships.md` は 5 リポジトリすべてに同一内容で配置 |
| **00_ は各リポジトリの中核** | 各リポジトリは `00_<RepoCore>.md` を 1 本持つことを推奨 |
| **.cursor/rules/** | Cursor 用 .mdc は原則ここに配置。ルート直下も許容 |
| **docs/** | 補足ドキュメントは `docs/` に集約。番号 or UPPER_SNAKE |
| **scripts/** | 自動化スクリプトは `scripts/` に集約 |

---

## 5. 移行の優先順位

| 優先度 | 対象 | 作業 |
|--------|------|------|
| **P0** | 全リポジトリ | `04_Repository_Relationships.md` の配置・同期（完了済み） |
| **P1** | GAAS, law-of-scale, HCE | `00_*.md` の追加（中核 doc の明示） |
| **P2** | universal-guideline | `00_Overview.md` 追加、tanaakk-*.mdc の整理 |
| **P3** | law-of-scale, HCE | `.cursor/rules/` への mdc 移動、docs の命名統一 |

---

## 6. バージョンルール（5 リポジトリ共通）

5 リポジトリは **Semantic Versioning（MAJOR.MINOR.PATCH）** に準拠し、以下のルールで同期する。

| ルール | 内容 |
|--------|------|
| **v2.1.1** | 統一案の初版。本ドキュメント（05_Folder_Structure_Convention）の策定時点 |
| **パッチ更新（v2.1.2, v2.1.3, ...）** | 各リポジトリが個別にパッチをリリースする際、**全リポジトリで通し番号**を付与。例: complex-physics-scale のパッチ → v2.1.2、次に universal-guideline のパッチ → v2.1.3 |
| **マイナー更新（v2.2.0）** | 機能追加・構成変更等でマイナーバージョンを上げる際は、**全 5 リポジトリを同時に v2.2.0 に更新**する |

### バージョン更新の流れ

```
v2.1.1（統一案）
    ├── リポジトリA パッチ → v2.1.2
    ├── リポジトリB パッチ → v2.1.3
    ├── リポジトリC パッチ → v2.1.4
    └── ...
    
マイナー更新時 → 全リポジトリ v2.2.0
```

---

## 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2025-02-23 | 初版作成（5 リポジトリ統一フォルダ構成・命名規則） |
| 2025-02-23 | バージョンルール追加（v2.1.1 統一案、パッチ v2.1.2 以降、マイナー時全リポジトリ v2.2.0） |
