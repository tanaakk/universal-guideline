# 04_Repository_Relationships — 5 層フレームワーク対応リポジトリ一覧

本ドキュメントは、5 層メタフレームワークに対応する **5 つのリポジトリの対応関係**を定義する。**Canonical Source（正本）** は [complex-physics-scale](https://github.com/tanaakk/complex-physics-scale) である。詳細は `00_Meta_Framework.md` を参照。

---

## 正本と配布

| 項目 | 内容 |
|------|------|
| **Canonical Source** | [complex-physics-scale](https://github.com/tanaakk/complex-physics-scale) |
| **本ファイルの配置** | 5 リポジトリすべてに同一内容で配置可能 |
| **バージョン同期** | `scripts/sync-repository-relationships.sh` で他リポジトリへコピー・バージョン更新 |

---

## 5 層とリポジトリ対応表

```
[1. 空間基底] → [2. 散逸機構] → [3. 系の成立パターンのスクリーニング] → [4. 系の残存・拡張] → [5. 特異点突破条件]
```

| 層 | 名称 | リポジトリ | 役割 |
|----|------|-----------|------|
| **1** | 空間基底 | [universal-guideline](https://github.com/tanaakk/universal-guideline) | 全階層に共通する「場」。データスキーマ、API、SaaS の汎用指針 |
| **2** | 散逸機構 | [GAAS-dissipative-constraints](https://github.com/tanaakk/GAAS-dissipative-constraints) | 系外からのエネルギー流入が、系内で構造化するという熱力学的公理の応用 |
| **3** | 系の成立パターンのスクリーニング | [complex-physics-scale](https://github.com/tanaakk/complex-physics-scale) | ローカルな秩序の形成において、系の条件分岐を規定（力学、Cross Industry、法令） |
| **4** | 系の残存・拡張 | [law-of-scale-verificator](https://github.com/tanaakk/law-of-scale-verificator) | 系の空間・時間方向への残存、複製、拡張の条件を規定（LSV、PLOG、DFP） |
| **5** | 特異点突破条件 | [homotopical-coherence-engine](https://github.com/tanaakk/homotopical-coherence-engine) | 時間・有限・無限方向への遷移可能性のスクリーニング（HCE、HoTT） |

---

## 依存関係（上流→下流）

```
universal-guideline (L1)
    ↓ 場の定義を前提
GAAS-dissipative-constraints (L2)
    ↓ 散逸条件を前提
complex-physics-scale (L3)  ← Canonical Source
    ↓ 系の成立パターンを出力
law-of-scale-verificator (L4)
    ↓ 残存・拡張条件を出力
homotopical-coherence-engine (L5)
```

---

## 各リポジトリの参照先

| リポジトリ | URL |
|-----------|-----|
| universal-guideline | https://github.com/tanaakk/universal-guideline |
| GAAS-dissipative-constraints | https://github.com/tanaakk/GAAS-dissipative-constraints |
| complex-physics-scale | https://github.com/tanaakk/complex-physics-scale |
| law-of-scale-verificator | https://github.com/tanaakk/law-of-scale-verificator |
| homotopical-coherence-engine | https://github.com/tanaakk/homotopical-coherence-engine |

---

## 同期メタデータ

| 項目 | 値 |
|------|-----|
| **Synced from** | complex-physics-scale |
| **Framework version** | v2.1.2 |
| **Last sync** | 2026-02-23 |

※ 本ファイルを他リポジトリにコピーする際は、上記を更新すること。

### バージョンルール（05_Folder_Structure_Convention 参照）

- **v2.1.1**: 統一案の初版
- **パッチ**: v2.1.2, v2.1.3, ...（各リポジトリのパッチ更新で通し番号）
- **マイナー**: 全リポジトリを同時に v2.2.0 に更新

---

## 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2025-02-23 | 初版作成（5 リポジトリ対応関係、Canonical Source 定義） |
| 2025-02-23 | Framework version v2.1.1、バージョンルール追記 |
