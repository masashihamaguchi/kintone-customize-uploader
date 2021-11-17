# kintone customize uploader for development

Cybozuがkintoneアプリのカスタマイズ開発者向けに提供しているcustomize-uploaderを簡単に使えるようにしたスクリプトです。
kintoneアプリを開発環境と本番環境で分けて開発・運用している方向けに作成しました。
カスマイズファイルをgitで管理して、開発環境で動作確認をしながら本番環境に反映させることを想定しています。


customize-uploaderについての詳しい情報はこちらから
> [customize-uploaderでカスタマイズ用のJS/CSSファイルをコマンドラインからアップロードしよう！](https://developer.cybozu.io/hc/ja/articles/360015889812-customize-uploader%E3%81%A7%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA%E7%94%A8%E3%81%AEJS-CSS%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3%E3%81%8B%E3%82%89%E3%82%A2%E3%83%83%E3%83%97%E3%83%AD%E3%83%BC%E3%83%89%E3%81%97%E3%82%88%E3%81%86-)

## 使い方

1. プロジェクトを任意の場所にcloneもしくはダウンロードして展開します。

2. `dest`ディレクトリ直下にある`customize-manifest-dev.json`に開発環境のアプリIDを、`customize-manifest-prd.json`に本番環境のアプリIDを入力します。

```json:customize-manifest-dev.json
{
  "app": "{アプリID}",
  "scope": "ALL",
  ...
}
```

3. customize-uploaderと同様に、kintoneアプリにアップロードするJavaScriptとCSSファイルを開発環境と本番環境の両方のマニフェストに追記します。

4. 以下のコマンドを使うことで開発環境と本番環境へのアップロードを簡単に行うことができます。

## コマンド
`npm run`の後に以下のスクリプト名を入れて実行すると、customize-uploaderの各スクリプトを実行できます。

|scripts|実行内容|
|:--:|:--|
|`install`|customize-uploaderをインストールします。|
|`init`|マニフェストファイルを作成します。|
|`import-dev`|開発環境のアプリのカスタマイズ情報を取得します。|
|`import-prd`|本番環境のアプリのカスタマイズ情報を取得します。|
|`dev`|作成したカスタマイズファイルを開発環境のアプリにアップロードします。|
|`prd`|作成したカスタマイズファイルを本番環境のアプリにアップロードします。|
|`dev-watch`|ファイルの更新を監視して、開発環境のアプリに都度アップロードします。|
|`prd-watch`|ファイルの更新を監視して、本番環境のアプリに都度アップロードします。|

例えば、開発環境のアプリにカスタマイズファイルをアップロードする場合は、

```
$ npm run dev
```

と入力します。

※`import-dev`, `import-prd`コマンドはcustomize-uploaderの仕様上、新しいマニフェストファイルが生成されてしまいます。