# Tips
- 実行方法
	- コマンドプロンプト編
		- ①コマンドプロンプトを起動して、以下を実行する。
			- powershell -NoProfile -ExecutionPolicy Unrestricted c:\test\test.ps1
	- ショートカット作成編
		- ①「c:\test\test.ps1」のショートカットを作成する。
		- ②ショートカットを右クリックして「プロパティ->リンク」先の前に以下を追加します
			- powershell -ExecutionPolicy RemoteSigned -File
		- ③ショートカットをダブルクリックすする。
	- 参考URL
		- http://qiita.com/tomoko523/items/df8e384d32a377381ef9

# 構文
- 【ファイル更新日時変更】Set-ItemProperty -path "c:\test.txt" -Name LastWriteTime -Value "2016/10/10 10:23:43"
