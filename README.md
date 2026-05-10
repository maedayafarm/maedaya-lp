# maedaya-lp

`maedaya-lp` は、お米の前田屋の「発芽する玄米」を紹介するLPです。

このリポジトリは静的HTMLをGitHub Pagesで公開する前提の、かなり小さな構成です。LP本体の見た目、文言、導線は制作意図が強く反映されるため、変更するときはLinear Issue上で目的と変更範囲を明確にしてから作業します。

## 構成

```txt
.
├── index.html
└── .github/
    └── workflows/
        └── pages.yml
```

- `index.html`: LP本体です。HTML、Tailwind CDN設定、ページ内スタイルがまとまっています。
- `.github/workflows/pages.yml`: GitHub Pagesへのデプロイ workflow です。

現時点では画像用の `assets/` ディレクトリやビルド工程はありません。

## 公開とデプロイ

`main` ブランチへpushされると、GitHub Actionsの `Deploy to GitHub Pages` workflow が動きます。

workflow の概要:

1. `actions/checkout@v4` でリポジトリを取得
2. `actions/configure-pages@v4` でPagesを設定
3. `actions/upload-pages-artifact@v3` でリポジトリルートをアップロード
4. `actions/deploy-pages@v4` でGitHub Pagesへデプロイ

正式な公開URLは、GitHub Pagesの設定またはActionsのデプロイ結果で確認します。運用上の正式URLはまだ人間判断として扱います。

## 編集方針

LP本体を変更する場合は、先にLinear Issueで以下を確認します。

- 何を変更するか
- LPの見た目や文言に影響するか
- 人間判断が必要な素材、URL、価格、訴求が含まれるか
- 確認方法は何か

特に以下は勝手に変更しません。

- FVや各セクションのコピー
- デザインの方向性
- 画像素材
- 商品CTAの遷移先
- 価格表記
- 購入導線

## 確認手順

静的HTMLなので、基本的には `index.html` をブラウザで開いて確認できます。

ローカルサーバーで確認する場合:

```sh
python3 -m http.server 8000
```

確認観点:

- desktop / mobile でレイアウトが崩れていないか
- CTAが意図した場所へ遷移するか
- 外部リンクを追加した場合、別タブ指定や計測方針が意図通りか
- 画像を追加した場合、alt、表示サイズ、トリミング、読み込み方式が適切か
- GitHub Pages workflow が成功しているか

## Linear運用メモ

関連Issue:

- `MAE-7`: 画像プレースホルダーを実画像に差し替える
- `MAE-8`: 商品CTAを実際の購入導線へ接続する
- `MAE-9`: SEO/OGP/構造化データを追加する
- `MAE-10`: Tailwind CDN依存を本番向けに整理する
- `MAE-11`: READMEと運用メモを追加する

`MAE-7` と `MAE-8` は人間判断が必要な要素が大きいため、素材やURLが決まるまでLP本体は変更しません。

## Codexに依頼するときの注意

Codexへ依頼するときは、Issue本文またはコメントに以下を書きます。

- 変更してよいファイル
- 変更してはいけない範囲
- 判断済みの素材、URL、文言
- 実装だけでよいのか、調査コメントまでか
- PRを作るか、コメントだけで止めるか

Codexは、明示されていないLPの文言、デザイン、画像、購入導線を推測で変更しません。

## 未確定事項

以下は今後の人間判断です。

- 正式な公開URL
- 画像素材の出どころと管理場所
- 商品CTAの購入先URL
- 玄米 / 白米の導線分け
- 価格表記の更新方針
- OGP画像とSNS表示方針
- Tailwind CDNを維持するか、ビルド工程を導入するか
