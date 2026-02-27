# 10_Responsive_First_Rules

マルチデバイス対応の**レスポンシブファースト規則**。モバイル・タブレット・デスクトップで一貫した UX を提供するための基準を定義する。

**ステータス**: 有効（2026-02-27）

**関連**: `tanaakk-responsive-first.mdc`（Cursor ルール）、`tanaakk-ui-ux.mdc`（UI/UX 補足）

---

## 目次

1. [参照フレームワーク](#1-参照フレームワーク)
2. [ブレークポイント（Mobile-First）](#2-ブレークポイントmobile-first)
3. [Viewport メタタグ](#3-viewport-メタタグ必須)
4. [タッチターゲット（WCAG 2.2）](#4-タッチターゲットwcag-22)
5. [タイポグラフィ（Fluid）](#5-タイポグラフィfluid)
6. [レイアウト原則](#6-レイアウト原則)
7. [画像・メディア](#7-画像メディア)
8. [検証チェックリスト](#8-検証チェックリスト)
9. [他ドキュメントとの関係](#9-他ドキュメントとの関係)
10. [更新履歴](#10-更新履歴)

---

## 1. 参照フレームワーク

| 規格・ガイド | 用途 |
|-------------|------|
| [WCAG 2.2](https://www.w3.org/TR/WCAG22/) | アクセシビリティ（マルチデバイス含む） |
| [W3C Device Adaptation](https://www.w3.org/WAI/standards-guidelines/) | デバイス適応、メディアクエリ |
| [web.dev Responsive Web Design](https://web.dev/responsive-web-design-basics/) | レスポンシブの基本 |
| [Tailwind CSS Breakpoints](https://tailwindcss.com/docs/responsive-design) | ブレークポイント実装 |

---

## 2. ブレークポイント（Mobile-First）

**最小幅から順に定義**。未プレフィックス = 全幅適用、`sm:` 以上で上書き。

| プレフィックス | 最小幅 | 用途 |
|---------------|--------|------|
| （なし） | 0px | モバイル（基準） |
| `sm:` | 640px (40rem) | 大型スマートフォン・小型タブレット |
| `md:` | 768px (48rem) | タブレット |
| `lg:` | 1024px (64rem) | デスクトップ |
| `xl:` | 1280px (80rem) | 大デスクトップ |
| `2xl:` | 1536px (96rem) | ワイドディスプレイ |

```css
/* Tailwind 準拠。モバイルをデフォルト、大画面で拡張 */
.container { @apply w-full md:max-w-2xl lg:max-w-4xl mx-auto px-4; }
```

---

## 3. Viewport メタタグ（必須）

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

| 属性 | 説明 |
|------|------|
| **width=device-width** | デバイス幅に合わせる |
| **initial-scale=1** | 初期ズーム 100% |
| **user-scalable=yes** | ユーザーによるズームを許可（WCAG 準拠） |

---

## 4. タッチターゲット（WCAG 2.2）

| 項目 | 最小サイズ | 備考 |
|------|-----------|------|
| **クリック可能領域** | 44×44px | WCAG 2.5.5 Target Size (Level AAA) |
| **推奨** | 48×48px | 余裕を持たせた設計 |
| **間隔** | 8px 以上 | 誤タップ防止 |

```html
<!-- アイコン単体でも 44px 以上のヒット領域を確保 -->
<button class="p-3 min-w-[44px] min-h-[44px]" aria-label="設定">
  <Settings class="w-5 h-5" />
</button>
```

---

## 5. タイポグラフィ（Fluid）

| 項目 | ルール |
|------|--------|
| **単位** | rem を優先（px は避ける） |
| **Body** | 0.875rem ~ 1rem（14px ~ 16px） |
| **Title** | 1.25rem 以上（20px+） |
| **Line Height** | 1.5 ~ 1.6 |
| **横スクロール禁止** | `overflow-x: hidden` は最終手段。コンテンツを viewport 内に収める |

---

## 6. レイアウト原則

| 原則 | 内容 |
|------|------|
| **Fluid Layout** | 固定幅より `max-width` + `width: 100%` |
| **Flexbox / Grid** | 固定 px より `flex`, `grid`, `minmax()` |
| **コンテナ** | `max-w-*` + `mx-auto` + `px-4` で中央寄せ |
| **横スクロール禁止** | コンテンツは viewport 幅内に収める。`overflow-x: auto` は表など限定的に |

---

## 7. 画像・メディア

| 項目 | ルール |
|------|--------|
| **レスポンシブ画像** | `srcset`, `sizes`, `<picture>` を検討 |
| **アスペクト比** | `aspect-ratio` で CLS 防止 |
| **最大幅** | `max-w-full` で親をはみ出さない |

```html
<img src="image.jpg" alt="..." class="w-full max-w-full h-auto" loading="lazy" />
```

---

## 8. 検証チェックリスト

| # | 項目 | 基準 |
|---|------|------|
| 1 | Viewport メタタグ | 必須 |
| 2 | 320px 幅で表示 | 横スクロールなし |
| 3 | タッチターゲット | 44×44px 以上 |
| 4 | テキスト | 200% ズームでも読める（WCAG 1.4.4） |
| 5 | ブレークポイント | sm/md/lg でレイアウトが適切に変化 |
| 6 | タッチ操作 | ホバー依存の機能にタップ代替 |

---

## 9. 他ドキュメントとの関係

| ドキュメント | 関係 |
|-------------|------|
| **tanaakk-responsive-first.mdc** | 本ドキュメントの Cursor ルール版。同一内容を AI に適用 |
| **tanaakk-ui-ux.mdc** | カラー・タイポ・アイコン・44×44px タップ領域。本ルールで**マルチデバイス境界条件**を補足 |
| **tanaakk-language-selection.mdc** | Tailwind sm/md/lg ブレークポイントの利用方針 |
| **08_GAAS_Hands-on_7Repo_Naming_Rules** | 7 リポジトリ命名規則（本ドキュメントとは独立） |
| **09_GAAS_Hands-on_Full_Naming_Rules** | フル命名規則（本ドキュメントは 10_ 番号で docs に配置） |

---

## 10. 更新履歴

| 日付 | 変更内容 |
|-----|----------|
| 2026-02-27 | 初版作成（レスポンシブファースト規則） |
