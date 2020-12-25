[トップに戻る](../index.md)

# インストール方法
-Git msysgit をインストール
-下記サイトより、Git クライアントのインストールファイルと言語ファイルをダウンロード
 http://code.google.coam/p/tortoisegit/wiki/Download
-Git クライアントのインストール
-言語ファイルのインストール (各サイトで日本語化方法を紹介しているが、最新版では日本語ファイルをインストールするだけで日本語化が可能)

# Tips
- [Push時、毎回認証画面が表示される対策](https://gist.github.com/stakiran/ab47411c1767e4e26b561925dbc2ddb3)
	1. Tortoise Gitの設定を開く（Git管理対象ファイルを右クリック→Setting）
	1. 「Git」→「Edit systemwide gitconfig」を押下
	1. メモ帳にて開かれたgitconfig内の以下項目を変更して保存
		- 変更前：helper = manager
		- 変更後：helper = wincred

[トップに戻る](../index.md)
