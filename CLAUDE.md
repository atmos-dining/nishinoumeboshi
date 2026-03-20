# 西のうめぼし サイト作業メモ

## プロジェクト概要
- サイト: https://www.nishinoumeboshi.com
- ホスティング: Netlify
- リポジトリ: `atmos-dining/nishiume-site`（GitHub）
- ブランチ: main

## ブログの仕組み
- ブログデータは `blog/posts.json` 一本で管理（`{ "posts": [...] }` 形式）
- 記事一覧: `blog/index.html`（posts.json を fetch して表示）
- 記事詳細: `blog/posts/post.html?slug=xxx`
- 画像: `images/` フォルダ

## CMS の状況

### 目標
Decap CMS（`/admin`）でブログ記事を管理できるようにする。
更新者：オーナー＋スタッフ複数名。全員 GitHub アカウントが必要。

### セットアップ手順（六本松ごえんと同じ方法）

**Step 1: admin/index.html の Netlify URL を設定**
- `admin/index.html` の `identity_url` と `gateway_url` を
  Netlify のサイト URL に変更する
  例: `https://xxxxx.netlify.app/.netlify/identity`

**Step 2: GitHub OAuth App の設定**
- GitHub → Settings → Developer settings → OAuth Apps
- 以下を設定：
  - Homepage URL: `https://www.nishinoumeboshi.com`
  - Authorization callback URL: `https://www.nishinoumeboshi.com/admin/`

**Step 3: スタッフを GitHub リポジトリに招待**
- リポジトリ → Settings → Collaborators → Add people
- ブログ更新するスタッフ全員を Collaborator として招待

### admin/ の構成
- `admin/index.html`: Decap CMS 本体（手動初期化設定）
