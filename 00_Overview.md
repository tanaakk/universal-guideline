# 00_Overview — Universal Guideline 概要

TANAAKK グループが提供する全アプリで共通利用する Cursor AI ルール・データスキーマ・API・SaaS の汎用指針。本リポジトリは Public。

**8 つのリポジトリが一つの広域系を形成している。** 本リポジトリ（universal-guideline）はその一部である。

---

## コンセプト

この Universal Rule は**逐次アップデート**される。

- **地球のベストプラクティス**: 最新時点での業界標準（Google AIP、Microsoft、IANA、会計API連携等）を採用し、随時更新する。
- **多惑星文明のベストプラクティス**: NASA/ホワイトハウス Celestial Time Standardization Policy、Coordinated Lunar Time (LTC)、火星時間等、重力圏に応じた抽象時間・参照系の標準が策定・普及するに従い、それらを取り込んで更新する。

## 前提条件（物理の三大構造原理）

Universal Guideline は、この宇宙に存在する任意のシステムが次の 3 原理を大局制約として満たすことを前提とする。

- **Locality（局所性）**
- **Causality（因果性）**
- **Unitarity（ユニタリ性）**

すなわち、任意のシステム `S` は `S |= (L ∧ C ∧ U)` を満たすものとして扱う。

参照: [物理の三大構造原理](https://www.tanaakk.com/2026/03/17/physics-2/)

---

## スコープと階層

**本リポジトリは L3 以降の階層を定義する。** L0〜L2 は [groundism-ontopologics](https://github.com/tanaakk/groundism-ontopologics) 等で定義される。

| 層 | 内容 | 主な規格・ルール |
|----|------|------------------|
| **L3** | UUID v4。識別子規格。対象の層 | tanaakk-universal-schema.mdc, tanaakk-uuid-hybrid.mdc |
| **L4** | 対象への射としての属性 | L4A（産業分類）、L4B（クロスインダストリ）、L4C（インダストリ別） |
| **L5** | プロジェクト | プロジェクト固有のコーディング規約 |

---

## 読む順序

| 順序 | ファイル | 内容 |
|------|----------|------|
| 00 | 本ファイル | 概要 |
| 04 | 04_Repository_Relationships.md | 7 リポジトリ対応関係 |
| 05 | 05_Folder_Structure_Convention.md | フォルダ構成・命名規則 |
| 06 | 06_Universal_Schema_Concept.md | ユニバーサルスキーマ概念 |
| 07 | 07_TANAAKK_Engineering_Methodology.md | エンジニアリング手法 |
| — | HIERARCHY.md | ルールの階層・抽象度 |
| — | tanaakk-*.mdc | ドメイン別ルール |

---

## 詳細

詳細は [README.md](README.md) を参照。
