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

## その他ハマったこと

### Q. ファイルが見れなかった

A. パーミッションを644

```
chmod 644 *
```
