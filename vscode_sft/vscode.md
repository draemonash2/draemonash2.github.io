
# Visual Studio Code

[トップに戻る](../index.md)

## おすすめ拡張機能

- 【Markdownlint】マークダウンのエラーチェック
- 【[Remote Development](https://anteku.jp/blog/develop/ssh%E6%8E%A5%E7%B6%9A%E5%85%88%E3%81%AE%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E6%8E%A5%E7%B6%9A%E5%85%83%E3%81%AEvisual-studio-code%E3%81%A7%E9%96%8B%E3%81%93%E3%81%86%EF%BC%81/)】ssh接続先のファイルを直接編集

## Tips

- [markdownlint 特定ルール除外方法](https://qiita.com/ryoheiszk/items/00620be5a53d632bd462)
    - 設定内容

        ```json
        {
          "MD003": { "style": "atx_closed" },
          "MD007": { "indent": 4 },
          "MD008": false,
          "no-hard-tabs": false,
          "whitespace": false
        }
        ```

    - 設定記載先
        - 以下のいずれか。
            - VSCodeの `setting.json`
            - 対象プロジェクトのルートディレクトリ直の `.markdownlint.json`

[トップに戻る](../index.md)
