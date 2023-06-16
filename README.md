<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

最初に nodejs、 [direnv](https://direnv.net) 、 [bun](https://github.com/oven-sh/bun)をインストールし、ディレクトリに入った後に`direnv allow`をお勧めします ( [.envrc は](https://github.com/xxai-art/doc/blob/main/.envrc)ディレクトリに入った後に自動的に実行されます)。

意味は、中国語から日本語、韓国語、英語、英語からその他すべての言語への翻訳です。中国語と英語のみをサポートしたい場合は、単に`zh: en`書くことができます。

## フロントエンドコード

* [フロントエンドコード](https://github.com/xxai-art/web)
* [サイト全体の言語パック](https://github.com/xxai-art/web/tree/main/i18n)
* [ログインモジュール用の言語パック](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [ウェブサイトの多言語ドキュメント](https://github.com/xxai-doc)

フロントエンド プログラミング言語は[@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus)で、coffeescript 構文に基づいていくつかの機能が追加されます。 [./coffee_plus.md](./coffee_plus.md)を参照してください。

## Web サイトとドキュメントの国際化

次の 3 つのプロジェクトをベースに構築

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  接尾辞は`.mdt`です。 `<+ ./coffee_plus/import.js>`に似た構文を使用して外部ファイルを参照し、接尾辞`.md`を使用してマークダウンを生成できます。

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  マークダウン翻訳では、コードやリンクは翻訳されず、翻訳された文がキャッシュされます。翻訳が変更されても元のテキストが変更されていない場合、再実行しても翻訳の変更は上書きされません。

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  `yaml`で生成された Web サイトを翻訳するための言語ファイル。

### 文書翻訳の自動化手順

コードリポジトリ[xxai-art/doc](https://github.com/xxai-art/doc)を参照してください。

最初に nodejs、 [direnv](https://direnv.net) 、 [bun](https://github.com/oven-sh/bun)をインストールし、ディレクトリに入った後に`direnv allow`をお勧めします ( [.envrc は](https://github.com/xxai-art/doc/blob/main/.envrc)ディレクトリに入った後に自動的に実行されます)。

大規模なコード ベースが数百の言語に翻訳されるのを避けるために、言語ごとに個別のコード ベースを作成し、コード ベースを保存する組織を作成しました。

環境変数`GITHUB_ACCESS_TOKEN`を設定して[create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee)を実行すると、コード ベースが自動的に作成されます。

もちろん、コードベースに組み込むこともできます。

翻訳スクリプトリファレンス[run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

スクリプト コードは次のように解釈されます。

[bunx](https://bun.sh/docs/cli/bunx)は npx の代替であり、より高速です。もちろん、bun がインストールされていない場合は、代わりに`npx`を使用できます。

`bunx mdt zh` zh ディレクトリ内の`.mdt` `.md`としてレンダリングします。以下の 2 つのリンクされたファイルを参照してください。

* [コーヒープラス.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [コーヒープラス.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n`は翻訳のコア コードです ( `nodejs`のみがインストールされていて、 `bun`と`direnv`がインストールされていない場合は、 `npx i18n`を実行して翻訳することもできます)。

[i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml)を解析します。このドキュメントの`i18n.yml`の構成は次のとおりです。

```
en:
zh: ja ko en
```

意味は、中国語から日本語、韓国語、英語、英語からその他すべての言語への翻訳です。中国語と英語のみをサポートしたい場合は、単に`zh: en`書くことができます。

最後のは[gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee)で、各言語の`README.md`のメイン タイトルと最初のサブタイトルの間のコンテンツを抽出して、エントリ`README.md`を生成します。コードは非常にシンプルなので、自分で確認できます。

無料翻訳にはGoogle APIを使用しております。 Google にアクセスできない場合は、次のようにプロキシを構成して設定してください。

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

翻訳スクリプトは、 `.i18n`ディレクトリに翻訳済みキャッシュを生成します。翻訳が繰り返されるのを避けるために、 `git status`でそれを確認し、コード リポジトリに追加してください。

翻訳を変更するたびに`bunx i18n`を実行してキャッシュを更新してください。

原文と訳文を同時に変更するとキャッシュが混乱するので、変更したい場合は片方だけ変更してから`bunx i18n`を実行してキャッシュを更新します。
