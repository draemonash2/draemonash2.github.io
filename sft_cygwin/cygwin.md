[トップに戻る](../index.md)

# インストール (参考: http://windowss7.web.fc2.com/special/cygwin/ )
- [こちら](http://cygwin.com/install.html) より setup-x86\_64.exe をインストール
- setup-x86\_64.exe を実行しインストールする。(パッケージは必要なものだけでよい。)
- setup-x86\_64.exe を C:\cygwin に移動(パッケージの再インストールのため)
- .bashrc に以下を加える (XXXはユーザ名)
	- alias cdh='cd C:/Users/XXX/Desktop'
- システム環境変数 に以下を加える。
	- set CYGWIN=ntsec tty
	- set HOME=/home/kakuchan
	- set MAKE\_MODE=UNIX
	- set SHELL=/bin/bash
- 完了！（環境変数 HOME の値は、 自分のホームディレクトリを指定するので、適当な値に変更してください）

# アンインストール
- cygwin フォルダ削除
- regedit より以下を削除
	- HKEY\_LOCAL\_MACHINE/SOFTWARE/Cygnus Solutions
	- HKEY\_CURRENT\_USER/Software/Cygnus Solutions
	
# Tips
- バッチシェル
	- 実行
		- sh XXX.sh
	- 注意！
		- シェルは必ずUNIXの改行コードとすること！
- リダイレクト
	- $XXX > result.txt
	- ※Windows のリダイレクト方法と同じ
- Grep
	- 実行例) grep -nr '^volatile.\*XXX.\*' C:/Users/XXXXXX/Desktop/a --include='\*.c'
- 日本語使用方法
	- Cygwin 画面上右クリック ⇒ Options
	- Text ⇒ Font ⇒ Select ⇒ MS ゴシック
	- Text ⇒ Locale ⇒ ja\_JP
	- Text ⇒ Character set ⇒ UTF-8

[トップに戻る](../index.md)
