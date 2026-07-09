# イラストギャラリー (minagal)

青い髪のオリジナルヒロインを描いたイラストレーション全15点のギャラリーサイト。
ビルドステップ不要の純粋な静的サイトです(HTML + CSS + Vanilla JS のみ、依存パッケージなし)。

## 構成

```
index.html          ギャラリー本体(単一ファイル、依存なし)
404.html            404ページ
_headers            Cloudflare Pages 用ヘッダー設定(キャッシュ・セキュリティ)
favicon.svg         ファビコン
robots.txt          クローラー設定
images/
  thumb/            グリッド表示用サムネイル(WebP、幅720px)
  full/             ライトボックス表示用フルサイズ(WebP)
```

## Cloudflare Pages へのデプロイ設定

このリポジトリはビルド不要なので、以下の設定で必ずデプロイが成功します。

| 設定項目 | 値 |
|---|---|
| Production branch | `master` |
| Framework preset | **None** |
| Build command | **(空欄のまま)** |
| Build output directory | `/` |

手順: Cloudflare ダッシュボード → **Workers & Pages** → **Create** → **Pages** →
**Connect to Git** でこのリポジトリを選択し、上記の設定でデプロイ。

デプロイ成功後、プロジェクトページ上部に `https://<プロジェクト名>.pages.dev` が表示されます。
URL が表示されない場合は **Deployments** タブで本番ブランチへのデプロイが
Success になっているかを確認してください。

## ローカルでの確認

```sh
python3 -m http.server 8000
# → http://localhost:8000
```

## 特徴

- 依存ゼロ・ビルド不要(デプロイ失敗要因を排除)
- 画像は WebP に最適化済み(元PNG 約33MB → 約3.5MB)
- サムネイル + フルサイズの2段構成で高速表示(遅延読み込み、隣接画像の先読み)
- ネイティブ `<dialog>` によるライトボックス(キーボード操作、スワイプ、フォーカス管理)
- JS 無効環境でも全作品閲覧可能(プログレッシブエンハンスメント)
- アクセシビリティ対応(altテキスト、スキップリンク、`prefers-reduced-motion`)
- OGP / 構造化データ / セキュリティヘッダー設定済み
