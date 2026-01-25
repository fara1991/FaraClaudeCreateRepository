# 🤖 Claude Repository Creator

AIが自動でプロジェクトを作成するシステムです。Issueを作成するだけで、Claudeが完全なプロジェクトを生成し、新しいGitHubリポジトリを自動作成します。

## ✨ 特徴

- 🎯 **簡単操作**: Issueフォームに記入するだけ
- 🤖 **AI生成**: Claude AIが完全なコードを自動生成
- 📦 **即座にデプロイ可能**: README、package.json、.gitignoreなど全て含まれる
- 🔄 **自動化**: リポジトリ作成からコミット・プッシュまで全自動

## 🚀 使い方

### 1. Issueを作成

1. このリポジトリの [**Issues**](../../issues) タブを開く
2. 「**New issue**」をクリック
3. 「**新しいプロジェクトをリクエスト**」を選択（緑色の「Get started」ボタン）

### 2. フォームに記入

以下の項目を入力：

- **リポジトリ名**: 作成したいリポジトリ名（例: `my-todo-app`）
- **プロジェクトタイプ**: Webアプリ、ブログ、ライブラリなど
- **技術スタック**: React、Next.js、Vue.jsなど
- **プロジェクトの説明**: どんなアプリを作りたいか詳しく説明
- **必要な機能**: 実装してほしい機能（任意）
- **公開設定**: プライベート/パブリック
- **ライセンス**: MIT、Apache 2.0など

### 3. 送信して待つ

「**Submit new issue**」をクリックすると、自動的に処理が開始されます。

**所要時間**: 約1〜3分

### 4. 完成！

処理が完了すると：
- ✅ Issueに完成報告のコメントが付きます
- ✅ 新しいリポジトリが作成されます
- ✅ コードが全てコミット・プッシュされます
- ✅ Issueは自動でクローズされます

## 📋 初期セットアップ（管理者向け）

このシステムを自分のアカウントで使う場合、以下のセットアップが必要です。

### 1. リポジトリを作成

1. このリポジトリをForkまたはテンプレートとして使用
2. プライベートリポジトリとして作成（推奨）

### 2. API キーを取得

#### Claude API キー

1. [Anthropic Console](https://console.anthropic.com/) にアクセス
2. **API Keys** → **Create Key** をクリック
3. 名前を入力（例: `GitHub Actions`）
4. 表示される `sk-ant-api03-xxxxx...` をコピー
5. **クレジットを購入**（最低$5、推奨$10〜$20）
   - Settings → Billing → Purchase credits

**料金**: 1プロジェクト生成あたり約$0.10〜$0.30（15円〜45円）

#### GitHub Personal Access Token (PAT)

1. [GitHub Settings → Tokens](https://github.com/settings/tokens) にアクセス
2. **Generate new token** → **Generate new token (classic)**
3. 以下を設定：
   - **Note**: `Claude Repository Creator`
   - **Expiration**: 90 days（推奨）
   - **Scopes**: ✅ `repo`（これだけチェック）
4. **Generate token** をクリック
5. 表示される `ghp_xxxxx...` をコピー（一度しか表示されません！）

### 3. Secrets を設定

1. リポジトリの **Settings** → **Secrets and variables** → **Actions**
2. **New repository secret** をクリック
3. 以下の2つを追加：

| Secret名 | 値 |
|---------|-----|
| `ANTHROPIC_API_KEY` | `sk-ant-api03-xxxxx...` |
| `PAT_TOKEN` | `ghp_xxxxx...` |

### 4. ラベルを作成

1. **Issues** → **Labels** → **New label**
2. 以下を入力：
   - **Label name**: `create_repo`
   - **Description**: プロジェクト作成リクエスト
   - **Color**: お好みで（緑色など）
3. **Create label** をクリック

### 5. 完了！

これで使用準備完了です。Issueを作成して試してみましょう！

## ⚡ 生成できるプロジェクト例

### Webアプリケーション
- ToDoリストアプリ
- タイマーアプリ
- カレンダーアプリ
- チャットアプリ
- 在庫管理システム

### Webサイト
- ブログサイト（マークダウン対応）
- ポートフォリオサイト
- ランディングページ
- 企業サイト
- ドキュメントサイト

### ライブラリ・ツール
- JavaScriptライブラリ
- Reactコンポーネント集
- CLIツール
- APIクライアント
- ユーティリティ関数集

### その他
- Chrome拡張機能
- データビジュアライゼーション
- ゲーム
- APIサーバー
- ...あらゆるプロジェクト！

## 🔧 技術スタック

このシステムは以下の技術で構築されています：

- **GitHub Actions**: ワークフロー自動化
- **Claude API**: AIによるコード生成
- **GitHub API**: リポジトリ作成・管理
- **Node.js**: スクリプト実行環境

## 📖 仕組み

1. **Issueテンプレート** でユーザーが要件を入力
2. **GitHub Actions** がIssue作成を検知
3. **Node.jsスクリプト** がIssue内容を解析
4. **Claude API** にプロジェクト生成を依頼
5. Claudeが完全なプロジェクトコードを生成
6. **GitHub API** で新しいリポジトリを作成
7. 生成されたコードをコミット・プッシュ
8. Issueに完了報告のコメントを投稿

## 🛡️ セキュリティ

- ✅ すべての機密情報はGitHub Secretsで暗号化保存
- ✅ プライベートリポジトリ推奨
- ✅ PATは最小限の権限のみ付与（`repo`のみ）
- ✅ API keyは定期的に更新推奨

## ❓ トラブルシューティング

### Actionsがスキップされる

**原因**: `create_repo` ラベルが付いていない

**解決方法**:
1. Issueを開く
2. 右サイドバー → **Labels** → `create_repo` を追加

### "Resource not accessible by integration" エラー

**原因**: GitHub Actionsの権限不足

**解決方法**: ワークフローファイルに以下を追加済み
```yaml
permissions:
  contents: read
  issues: write
```

### "API key invalid" エラー

**原因**: ANTHROPIC_API_KEYが間違っている

**解決方法**: Secretsを再確認、または新しいAPI keyを発行

### "insufficient_quota" エラー

**原因**: Claude APIのクレジット不足

**解決方法**: [Anthropic Console](https://console.anthropic.com/) でクレジットを追加購入

### リポジトリが作成されない

**原因**: PAT_TOKENの権限不足、または有効期限切れ

**解決方法**: 
1. PATの `repo` 権限を確認
2. 有効期限を確認
3. 必要に応じて新しいトークンを発行

## 📝 ライセンス

MIT License

## 🙏 クレジット

- **Claude AI** by Anthropic
- **GitHub Actions** by GitHub
- インスピレーション: AI駆動開発の未来

---

**作成者**: [@fara1991](https://github.com/fara1991)

質問や提案がある場合は、Issueを作成してください！
