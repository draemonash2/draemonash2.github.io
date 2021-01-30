[トップに戻る](../index.md)

# Tips
- バッチファイルにてPathが設定されていないような挙動となる
	- Path 設定後、OS 再起動しないとバッチファイルでは Path が設定されない
- シンボリックリンクについて
	-  シンボリックリンク／ハードリンク／ショートカットの違い
		- http://qiita.com/opengl-8080/items/c2b6a93dfca5b61f9e6a
	- シンボリックリンク（フォルダ）実行例
		- mklink /d "C:\Users\draem\_000\AppData\Roaming\Apple Computer\MobileSync\Backup" "X:\810\_BackUp\_iTunes\MobileSync\Backup"
		```
		【リンク元】
		  C:
		  └ Users
			└ draem\_000
			  └ AppData
				└ Roaming
				  └ Apple Computer
					└ MobileSync
					  └ Backup
		【リンク先】
		  X:
		  └ 810\_BackUp\_iTunes
			└ MobileSync
			  └ Backup
				└ e197dbc615bfdf9375672cf9b26f6928bb655cb3
		【表示例】
		  C:
		  └ Users
			└ draem\_000
			  └ AppData
				└ Roaming
				  └ Apple Computer
					└ MobileSync
					  └ Backup（＝X:\810\_BackUp\_iTunes\MobileSync\Backup）
						└ e197dbc615bfdf9375672cf9b26f6928bb655cb3 
		```
- ワイルドカードを使用して、テキストファイルを一括変更する
	- rename \*.txt \*.xls
- SET 文の間にスペースは入れない！
	``` bat
	:: <<OK 例>>
	set ARG\_NUM=9
	echo %ARG\_NUM%
	:: ⇒ 9

	:: <<NG 例>>
	set ARG\_NUM = 9
	echo %ARG\_NUM%
	:: ⇒ ECHO は OFF です
	```
- if 文で判定する変数に何も入っていない可能性がある場合は、その変数を if 文で使用する際に "" や {} で囲うこと！
	``` bat 
	:: <<NG例>>
	::  「if %2 == /a」は、引数が一つしかない場合「( の使い方が誤っています。」というエラーになる。
	::  下の例の中のでは、引数１に 1 が入っていて「if %2 == /a」のパスが通らなくても、最外側のif文が一文としてとらえられるため上記と同様エラーになる。
	if %1 == 2 (
		if %2 == /a (
			echo a
		) else (
			echo b
		)
	) else (
		echo c
	)
	
	:: <<OK例>>
	::  「if "%2" == "/a"」は、引数が一つしかない場合でもエラーにならないため、正常に動作する。
	if "%1" == "2" (
		if "%2" == "/a" (
			echo a
		) else (
			echo b
		)
	) else (
		echo c
	)
	```
- if 文の中にコメントは入れない！
- FOR文やIF文で変数の中身が消える
	- [詳細はこちら](http://d.hatena.ne.jp/jak-san/20110709/1310168663)
- setlocal / endlocalコマンドは環境変数のローカル化のためにあります。
	- ローカル化とはsetlocalからendlocalの範囲内で定義した変数がその中だけ有効でその外部の同名の変数に影響を及ぼさないようにすることです。
- 一つのコマンドを複数行に分けて記述する方法
	- 行末に「^」を記述する。２行目以降は行頭に空白を記載すること。
		```
		"C:\prg\_exe\Vim\gvim.exe" ^
		  "c:\work1\test.c" ^
		  "c:\work2\test.h" ^
		  ""
		```
- [「start」コマンドと「スペース」の相性が悪い！](http://d.hatena.ne.jp/mizuki\_astral/20100715/1279203356)
- pushd コマンド
	- cd コマンドはドライブを跨いだ移動ができない。（/d オプションが必要）
	- pushd コマンドはドライブを跨いだ移動ができる！
- %CD%と%~dp0の違い
	- どちらもカレントフォルダを取得する方法だが、作業フォルダを示すところが違う。
	- 「c:\BBB\test.bat - ショートカット」を実行した場合の出力結果例を以下に示す
		- 例
			- c:\AAA\test.bat
				``` bat
				@echo off
				echo %CD%
				echo %~dp0
				```
			- c:\BBB\test.bat - ショートカット
				- 指示先：c:\AAA\test.bat
				- 作業フォルダ：なし
			- c:\BBB\test.bat - ショートカット2
				- 指示先：c:\AAA\test.bat
				- 作業フォルダ：c:\CCC
		- 実行結果
			- c:\AAA\test.bat
				```
				c:\AAA
				c:\AAA\
				```
			- c:\BBB\test.bat - ショートカット
				```
				c:\BBB
				c:\AAA\
				```
			- c:\BBB\test.bat - ショートカット2
				```
				c:\CCC
				c:\AAA\
				```

# サンプルコード
- 【フォルダ/ファイル削除】
	- バッチファイル）DelFileOrFolder.bat
	- 使い方）call DelFileOrFolder.bat c:\test\path（パスはフォルダ＆ファイル双方指定可能）
		```
		@echo off
		
		setlocal
		
		set JDG\_FILE=%~a1
		set FILE=%1
		
		::ファイル存在確認
		if not exist %FILE% goto end
		
		::ファイルが存在した場合、削除
		if %JDG\_FILE:~0,1% == d (
			rmdir /S /Q %FILE%
			echo Directry %FILE% is Deleted!
		) else if %JDG\_FILE:~0,1%==- (
			del /Q /F %FILE%
			echo File %FILE% is Deleted!
		) else (
			echo %FILE% is not File/Folder Path!
		)
		
		:end
		endlocal
		```
- 引数の数チェック
	```bat
					 set ARG\_NUM=9
	if "%~9" == "" ( set ARG\_NUM=8 ) else ( goto exec )
	if "%~8" == "" ( set ARG\_NUM=7 ) else ( goto exec )
	if "%~7" == "" ( set ARG\_NUM=6 ) else ( goto exec )
	if "%~6" == "" ( set ARG\_NUM=5 ) else ( goto exec )
	if "%~5" == "" ( set ARG\_NUM=4 ) else ( goto exec )
	if "%~4" == "" ( set ARG\_NUM=3 ) else ( goto exec )
	if "%~3" == "" ( set ARG\_NUM=2 ) else ( goto exec )
	if "%~2" == "" ( set ARG\_NUM=1 ) else ( goto exec )
	if "%~1" == "" ( set ARG\_NUM=0 ) else ( goto exec )
	:exec
	```
- 指定フォルダ配下の .svn フォルダをすべて削除
	```bat
	cd "C:\Users\draem\_000\Desktop\codes\_sample"
	for /R %i in (.svn) do rmdir /Q /S "%i"
	```
- bat ファイルでコンソールを開かずにコマンド実行する
	```bat
	@echo off
	if not "%~0"=="%~dp0.\%~nx0" (
		 start /min cmd /c,"%~dp0.\%~nx0" %\*
		 exit
	)
	start "C:\prg\_exe\Vim\gvim.exe" "C:\test.txt"
	```

[トップに戻る](../index.md)
