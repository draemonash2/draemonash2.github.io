[トップに戻る](../index.md)

# Tips
- vbaのソースコードをタグとして登録する
	1. ルートディレクトリに移動する
	2. 以下のコマンドを実行
		- `ctags -R --language-force=Basic`
- exuberant-ctagsとuniversal-ctagsのどちらを使うべきか？
	- 結論：[universal-ctagsを使っておけば問題ない](https://qiita.com/meruneru/items/60e95c99afa8e51196a0)
		- exuberant-ctags
			- 複数のプログラミング言語に対応したctags。公式ページのリリース最新Version 5.8 [09 July 2009]とあるため、開発が10年前に止まっている。
		- universal-ctags
			- universal-ctagsは、exuberant-ctagsの開発を引き継いでいるプロジェクトとのこと。universal-ctagsを使っていれば間違いなさそう。
			- オプション `-R` が使えるのはこちら。
			- インストール方法は以下の通り。
				- Ubuntu：`sudo apt install universal-ctags`
				- Mac：`brew install universal-ctags`

[トップに戻る](../index.md)

