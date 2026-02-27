# 01_IO_Specification — I/O 仕様の定義と本リポジトリの想定 I/O

**正本（Canonical）**: 日本語版。

本ドキュメントは、**I/O Specification（入出力仕様）** の定義を明確にし、本リポジトリ（universal-guideline）が想定する In/Out について注記する。I/O Specification の一般定義は [holographic-sphere-topology/01_HST_IO_Specification.md](https://github.com/tanaakk/holographic-sphere-topology/blob/main/01_HST_IO_Specification.md) を参照。

---

## 1. I/O Specification の定義

**I/O Specification（入出力仕様）** とは、ある Object（系・モジュール・ブラックボックス）に対して、**どのような Input（In）に対して、どのような Output（Out）を出力するか** を記述した仕様である。全リポジトリは I/O Specification により定義される。

---

## 2. 本リポジトリが想定する I/O

本リポジトリ（universal-guideline）は、**全階層に共通する「場」** として、L3（UUID v4）以降の階層を定義する。データスキーマ、API、SaaS の汎用指針を提供する。

### 2.1 想定される Input (In)

| 種類 | 内容 |
|------|------|
| **クエリ** | データスキーマ・API・SaaS・識別子・規格・セキュリティに関する設計・実装の問い |
| **例** | 「PK/FK は何を使うべきか」「UUID v4 と v7 の使い分けは」「産業分類コードはどう格納するか」「会計API連携の規格は」「マルチクラウド IAM の設計指針は」「URL・サイトマップの命名規則は」 |

### 2.2 想定される Output (Out)

| 種類 | 内容 |
|------|------|
| **回答** | L3/L4/L5 階層に準拠したルール・スキーマ・規格対応 |
| **含まれる要素** | tanaakk-universal-schema.mdc、tanaakk-uuid-hybrid.mdc、tanaakk-api-first.mdc、tanaakk-security.mdc、業種別ケーススタディ（70_uuid-classification-rules）、L4A/L4B/L4C 規格対応 |

### 2.3 I/O 対応図

```
[In] データスキーマ・API・SaaS・識別子・規格・セキュリティに関する設計・実装のクエリ
     │
     ▼
┌─────────────────────────────────────────────────────────┐
│  universal-guideline (本リポジトリ)                      │
│  L1: 空間基底。全階層に共通する「場」                     │
│  tanaakk-*.mdc、HIERARCHY.md 等を参照                    │
└─────────────────────────────────────────────────────────┘
     │
     ▼
[Out] L3/L4/L5 階層に準拠したルール・スキーマ・規格対応
     （UUID v4、規格階層、API First、セキュリティ、業種別ケーススタディ 等）
```

---

## 3. 参照

- [holographic-sphere-topology/01_HST_IO_Specification.md](https://github.com/tanaakk/holographic-sphere-topology/blob/main/01_HST_IO_Specification.md) — I/O Specification の一般定義
- [HIERARCHY.md](HIERARCHY.md) — ルールの階層・抽象度
- [README.md](README.md) — 本リポジトリ概要

---

## 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2026-02-27 | 初版作成（I/O Specification 定義、本リポジトリ想定 I/O 注記） |
