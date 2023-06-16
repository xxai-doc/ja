<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.アート

ウェブサイトのコードの一部はオープンソースです。翻訳の最適化にご協力ください。

## フロントエンドコード

* [フロントエンドコード](https://github.com/xxai-art/web)
* [サイト全体の言語パック](https://github.com/xxai-art/web/tree/main/i18n)
* [ログインモジュール用の言語パック](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [ウェブサイトの多言語ドキュメント](https://github.com/xxai-doc)

フロントエンド プログラミング言語は[@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus)で、coffeescript 構文に基づいていくつかの機能が追加されます。 [./coffee_plus.md](./coffee_plus.md)を参照してください。

## Web サイトとドキュメントの国際化

次の 3 つのプロジェクトをベースに構築

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

拡張子`.mdt`が付いたマークダウン テンプレートは、 `<+ ./coffee_plus/import.js>`に似た構文で外部ファイルを参照できます。

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

マークダウン翻訳では、コードやリンクは翻訳されず、翻訳された文がキャッシュされます。翻訳が変更されても元のテキストが変更されていない場合、再実行しても翻訳の変更は上書きされません。

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

`yaml`で生成された Web サイトを翻訳するための言語ファイル。
