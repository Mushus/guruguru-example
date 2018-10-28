# guruguru-example

circle ciを使ってみる。

## ディレクトリ構成

```
.
├── README.md       # このファイル
├── .circleci       # Circle CIの設定ディレクトリ
│   └── config.yml  # Circle CIの設定ファイル
└── dist            # デプロイ対象のファイル
    └── index.html  # お試しように配置してみたファイル達
```

詳細は `.config.yml` に記載しました。

### circle ci の設定

1. サイドメニューの `ADD PROJECT` をポチポチしてプロジェクトを Circle CI に追加する。
1. `BUILD SETTINGS` の `Environment Variables` に環境変数として接続先情報を追加する

* `FTP_USER` ユーザー名
* `FTP_PASSWORD` パスワード
* `FTP_HOST` ホスト名

にそれぞれ FTP の情報を入れて以下を入れたらアップロードが完了する。

```
# 接続情報でつないで、ミラーリングアップロードを「ローカルの./dist」から「リモートの/」にアップロードする
lftp -u $FTP_USER,$FTP_PASSWORD $FTP_HOST -e "mirror --reverse --delete --only-newer --verbose -X .DS_Store ./dist /; exit"
```

## その他ハマったこと

### Q. ファイルが見れなかった

A. パーミッションを644

```
chmod 644 *
```

### Q. FTP ログインできない

A. 接続先のサーバーからブロックされてるらしい？ 解決してないけどエックスなんちゃらサーバーダメそう
