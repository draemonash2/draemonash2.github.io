[トップに戻る](../index.md)

# コマンド

- 圧縮
	- コマンド）`7z.exe a <圧縮先ファイルパス> <圧縮対象ファイル/フォルダパス>`
	- 実行例）`7z.exe a C:\test\ahk_archive.zip C:\codes\ahk`
		- 圧縮前
			```
				ahk
				　├ A
				　└ B
			```
		- 圧縮後
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
	- 実行例）`7z.exe x -o"C:\codes" "C:\test\ahk_archive.zip"`
		- 解凍前
			```
				ahk_archive.zip
				　├ A
				　└ B
			```
		- 解凍後
			```
				ahk
				　├ A
				　└ B
			```
	- 注意事項１）「-o」と「<解凍先フォルダ/ファイルパス>」の間はスペース不要
	- 注意事項２）「<解凍先フォルダ/ファイルパス>」は親フォルダパスを指定する

- 分割圧縮
	- コマンド）`7z.exe a -v<分割サイズ> <圧縮先ファイルパス> <圧縮対象ファイル/フォルダパス>`
	- 実行例）`7z.exe a -v50m C:\test\ahk_archive.zip C:\codes\ahk`

- 分割解凍
	- 以下コマンドで結合後に解凍する。
		- `COPY /B file.zip.001+file.zip.002+file.zip.003 file.zip`

[トップに戻る](../index.md)
