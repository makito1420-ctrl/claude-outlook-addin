[README (1).md](https://github.com/user-attachments/files/29188305/README.1.md)
# Claude 返信アシスタント — セットアップ手順

Admin認証不要。個人のMicrosoftアカウントとGitHub（無料）だけで動きます。

---

## ステップ 1: GitHub Pages にファイルをアップロード

1. https://github.com/new でリポジトリを作成
   - Repository name: `claude-outlook-addin`
   - Public を選択
   - 「Create repository」をクリック

2. `taskpane.html` と `manifest.xml` をアップロード
   - 「Add file」→「Upload files」から両ファイルをドラッグ＆ドロップ
   - 「Commit changes」をクリック

3. GitHub Pages を有効化
   - リポジトリの「Settings」→「Pages」
   - Source: `Deploy from a branch`、Branch: `main`、フォルダ: `/ (root)`
   - 「Save」をクリック
   - 数分後に `https://YOUR-USERNAME.github.io/claude-outlook-addin/` で公開される

---

## ステップ 2: manifest.xml のURLを更新

`manifest.xml` の以下の行を自分のURLに書き換えてください：

```xml
<SourceLocation DefaultValue="https://YOUR-GITHUB-USERNAME.github.io/claude-outlook-addin/taskpane.html"/>
```

例：GitHubユーザー名が `makito` の場合：
```xml
<SourceLocation DefaultValue="https://makito.github.io/claude-outlook-addin/taskpane.html"/>
```

書き換えたら、GitHubにアップロードし直してください。

---

## ステップ 3: Outlookにアドインを登録

### Outlook on the web（推奨・最も簡単）
1. https://outlook.office.com を開く
2. 右上の歯車アイコン →「アドインを管理」
3.「カスタムアドイン」→「ファイルから追加」
4. ダウンロードした `manifest.xml` を選択
5. 警告が出ても「インストール」をクリック

### Outlook デスクトップアプリ（Windows）
1. Outlookを開く
2.「ファイル」→「アドインの管理」→ブラウザが開く
3. 上記と同じ手順でインストール

---

## ステップ 4: Claude API キーを取得

1. https://console.anthropic.com/settings/keys を開く
2. 「Create Key」をクリック
3. 生成されたキー（`sk-ant-api03-...`）をコピー

※ APIの料金目安：メール1通あたり約0.3〜1円（使った分だけ課金）

---

## 使い方

1. Outlookでメールを開く
2. 右側のアドインパネルに「Claude 返信アシスタント」が表示される
3. APIキーを入力（初回のみ。以降は自動保存）
4.「返信下書きを生成」ボタンをクリック
5. 下書きを確認し「返信欄に挿入」→そのまま送信

---

## トラブルシューティング

| 症状 | 対処 |
|------|------|
| アドインが表示されない | Outlookを再起動、またはブラウザをリロード |
| APIキーエラー | console.anthropic.com でキーを確認 |
| 本文が取得できない | メールを完全に開いてから再試行 |
| GitHub Pages が表示されない | 設定から5〜10分後に再アクセス |
