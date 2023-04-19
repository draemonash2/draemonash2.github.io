
# Visual Studio Code

[トップに戻る](../index.md)

## おすすめ拡張機能

- 【Markdownlint】マークダウンのエラーチェック
- 【[Remote Development](https://anteku.jp/blog/develop/ssh%E6%8E%A5%E7%B6%9A%E5%85%88%E3%81%AE%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%82%92%E6%8E%A5%E7%B6%9A%E5%85%83%E3%81%AEvisual-studio-code%E3%81%A7%E9%96%8B%E3%81%93%E3%81%86%EF%BC%81/)】ssh接続先のファイルを直接編集

## Tips

- ポータブル版VSCodeの設定ファイル格納先
    - `<vscode_program_dir>\data\user-data\User\keybindings.json`
    - `<vscode_program_dir>\data\user-data\User\settings.json`
- [markdownlint 特定ルール除外方法](https://qiita.com/ryoheiszk/items/00620be5a53d632bd462)
    - 設定先
        - 以下のいずれか。
            - VSCodeの `setting.json`

                ```json
                "markdownlint.config": {
                    "MD003": { "style": "atx_closed" },
                    "MD008": false,
                    "no-hard-tabs": false
                }
                ```

            - 対象プロジェクトのルートディレクトリ直下の `.markdownlint.json`

                ```json
                {
                    "MD003": { "style": "atx_closed" },
                    "MD008": false,
                    "no-hard-tabs": false
                }
                ```

    - 注意事項
        - `.markdownlint.json` に除外ルールが設定されている場合は、 上の設定が無視される。（共存できない）  
        そのため、`setting.json` を有効化したい場合は、`.markdownlint.json` 内の除外ルールを `{　}` ごと削除すること。
        - VSCode上でディレクトリを開いており、そのルートディレクトリに`.markdownlint.json`を格納していれば、  
        配下の全 `.md` ファイルに除外ルールが適用される。  
        反対に、ディレクトリで開いていない場合は、ルートディレクトリに格納されていても除外ルールが適用されない。

[トップに戻る](../index.md)
