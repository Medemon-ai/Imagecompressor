# Imagecompressor
# ImagePack JP — デプロイメントガイド

## ファイル構成

```
/
├── index.html       ← メインページ（ツール+SEO+全コンテンツ）
├── sitemap.xml      ← 検索エンジン向けサイトマップ
├── robots.txt       ← クローラー設定
├── manifest.json    ← PWA/ホーム追加対応
└── _headers         ← Cloudflare Pages / Netlify セキュリティヘッダー
```

## デプロイ手順

### Cloudflare Pages
1. GitHubリポジトリにプッシュ
2. Cloudflare Pages ダッシュボードで「新規プロジェクト」
3. ビルドコマンド: なし（静的HTML）
4. 出力ディレクトリ: `/`
5. カスタムドメイン: `jp.easypdfcompress.com` を設定

### Netlify
1. `netlify drag-and-drop deploy` でフォルダをドロップ
2. または GitHubと連携して自動デプロイ
3. カスタムドメインをNetlify DNSで設定

## AdSense 広告の追加方法

`index.html` 内に2箇所の `ad-unit` クラスのdivが用意されています：

### 1. ツール下部（728×90 リーダーボード）
```html
<!-- 現在のコード -->
<div class="ad-unit" aria-hidden="true">広告エリア（728×90）</div>

<!-- AdSense承認後に置き換え -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-XXXXXXXXXXXXXXXX"
     data-ad-slot="XXXXXXXXXX"
     data-ad-format="horizontal"></ins>
<script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
```

### 2. フィーチャーセクション下部（336×280 レクタングル）
同様に `ad-unit` divをAdSenseコードに置き換え。

### AdSenseスクリプトの追加（`<head>`内）
```html
<script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js?client=ca-pub-XXXXXXXXXXXXXXXX" crossorigin="anonymous"></script>
```

## SEO チェックリスト

- [ ] Google Search Console でサイト登録
- [ ] `sitemap.xml` をSearch Consoleに送信
- [ ] `robots.txt` の動作確認
- [ ] Google Analytics / Cloudflare Analytics の設定
- [ ] PageSpeed Insights でCore Web Vitals確認
- [ ] OGP画像（`og-image.png`、1200×630px）を作成して配置

## ターゲットキーワード

| キーワード | 月間検索数（推定） |
|---|---|
| 画像圧縮 | 40,000+ |
| 無料画像圧縮 | 10,000+ |
| オンライン画像圧縮 | 8,000+ |
| JPG圧縮 | 12,000+ |
| PNG圧縮 | 9,000+ |
| WEBP圧縮 | 3,000+ |
| 画像サイズ縮小 | 15,000+ |
| ブラウザ画像圧縮 | 2,000+ |

## 技術仕様

- **処理方式**: Canvas API（クライアントサイド）
- **対応フォーマット**: JPG / JPEG / PNG / WEBP
- **圧縮品質**:
  - 軽量: quality=0.88
  - 標準: quality=0.72
  - 最大: quality=0.45 + 2400px制限
- **依存関係**: なし（外部ライブラリ不使用）
- **フォント**: Google Fonts（Noto Sans JP + JetBrains Mono）
- 
