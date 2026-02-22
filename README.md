# TANAAKK Cursor Rules

TANAAKKグループが提供する全アプリで共通利用する Cursor AI ルールです。このレポジトリはPublicです。

## ルール一覧

| ファイル | 説明 |
|----------|------|
| `tanaakk-universal-schema.mdc` | データ設計・会計API連携（JGAAP/IFRS/US GAAP） |
| `tanaakk-language-selection.mdc` | 言語・フレームワーク選択指針 |
| `tanaakk-ui-ux.mdc` | 共通UI/UX（カラー・タイポ・アクセシビリティ） |

## 使い方

### プロジェクトに追加

各アプリの `.cursor/rules/` にこのフォルダの `*.mdc` をコピーするか、Git サブモジュールとして追加：

```bash
git submodule add https://github.com/<org>/tanaakk-cursor-rules.git .cursor/rules
```

### User Rules に貼る

`user-rules-copy-paste.md` の完全版を Cursor Settings > Rules for AI にコピー＆ペースト。
