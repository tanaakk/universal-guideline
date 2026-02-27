# GAAS Hands-on ワークスペース起動

## 起動時のポップアップ

**universal-guideline** をフォルダとして開いた場合、[Auto-Open Workspace](https://marketplace.visualstudio.com/items?itemName=zoma.vscode-auto-open-workspace) 拡張が `gaas-hands-on.code-workspace` を検出し、**QuickPick でワークスペースを開くよう案内**します。

### セットアップ

1. Cursor で universal-guideline フォルダを開く
2. 推奨拡張の通知が出たら **Install** をクリック（または Extensions で `Auto-Open Workspace` を検索してインストール）
3. 次回からフォルダを開くと、ワークスペース選択のポップアップが表示される

### 動作

- **フォルダを開いたとき**: QuickPick「1 workspace-file(s) found! Select to open…」が表示され、`gaas-hands-on.code-workspace` を選択して 7 リポジトリを一括で開ける
- **すでにワークスペースを開いているとき**: ポップアップは出ない（`File > Open Workspace from File` で手動切り替え可能）
