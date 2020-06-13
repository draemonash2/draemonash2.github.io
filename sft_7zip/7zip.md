[トップに戻る](../index.md)

# コマンド

- 圧縮
	- コマンド）`7z.exe a <圧縮先ファイルパス> <圧縮対象ファイル/フォルダパス>`
	- 実行例）`7z.exe a C:\test\ahk_archive.zip C:\codes\ahk`
		- 実行前
			```
				ahk
				　├ A
				　└ B
			```
		- 実行後
			```
				ahk_archive.zip
				　├ A
				　└ B
			```

- 圧縮(パスワード付き)
	- コマンド）`7z.exe a <圧縮先ファイルパス> <圧縮対象ファイル/フォルダパス> -p <パスワード>`
	- 実行例）`7z.exe a C:\test\ahk_archive.zip C:\codes\ahk -p abcd1234`

- 解凍
	- コマンド）`7z.exe x -o<解凍先フォルダ/ファイルパス> <解凍対象ファイルパス>`
	- 実行例）`7z.exe x -o"C:\codes\ahk" "C:\test\ahk_archive.zip"`
		- 【注意事項】「-o」と「<解凍先フォルダ/ファイルパス>」の間はスペース不要
		- 実行前
			```
				ahk_archive.zip
				　├ A
				　└ B
			```
		- 実行後
			```
				ahk
				　├ A
				　└ B
			```

[トップに戻る](../index.md)
