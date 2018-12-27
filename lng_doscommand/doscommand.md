# ToDo

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
- ファイルパス展開について
	- I:数字（0:実行中のバッチファイル、1～:バッチファイルの引数）
 [パス]   [説明]                  [出力結果]
 %I       文字列そのまま          "C:\Users\draem\_000\Desktop\test\test 1-1.bat"
 %~I      すべての引用句 " 削除   C:\Users\draem\_000\Desktop\test\test 1-1.bat
 %~fI     完全修飾パス名          C:\Users\draem\_000\Desktop\test\test 1-1.bat
 %~dI     ドライブ文字            C:
 %~pI     パス                    \Users\draem\_000\Desktop\test\
 %~dpI    ディレクトリパス        C:\Users\draem\_000\Desktop\test\
 %~nI     ファイル名              test 1-1
 %~xI     ファイル拡張子          .bat
 %~sI     短いパス                C:\Users\DRAEM\_~1\Desktop\test\TEST1-~1.BAT
 %~aI     ファイル属性            --a--------
 %~tI     ファイル日付/時刻       2016/10/27 16:11
 %~zI     ファイルサイズ          1397
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
	- 詳細は以下
 http://d.hatena.ne.jp/jak-san/20110709/1310168663
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
- 「start」コマンドと「スペース」の相性が悪い！
	- http://d.hatena.ne.jp/mizuki\_astral/20100715/1279203356
- pushd コマンド
	- cd コマンドはドライブを跨いだ移動ができない。（/d オプションが必要）
	- pushd コマンドはドライブを跨いだ移動ができる！

# 構文

- 【変数定義】set LOGDIR=C:\Users\Dropbox
- 【列挙型定義】-
- 【ブロック脱出】-
- 【ヘルプ】help dir

- 【if】if %TAG\_TYPE% == a ( ～処理～ ) else if %TAG\_TYPE% == c ( ～処理～ ) else ( ～処理～ )
- 【if（否定）】if not %TAG\_TYPE% == a
- 【for】★
- 【コメント】::コメント
- 【出力】echo Hello world!
- 【出力（改行のみ）】echo.
- 【出力抑制】\>NUL 2>&1

- 【文字列 切取１】%VAR% ⇒変数Vの値全体
- 【文字列 切取２】%VAR:~m% ⇒m文字目から、最後まで
- 【文字列 切取３】%VAR:~m,n% ⇒m文字目から、n文字分
- 【文字列 切取４】%VAR:~m,-n% ⇒m文字目から、最後のn文字分を除いたもの
- 【文字列 切取５】%VAR:~-m% ⇒後ろからm文字目から、最後まで
- 【文字列 切取６】%VAR:~-m,n% ⇒後ろからm文字目から、n文字分
- 【文字列 切取７】%VAR:~-m,-n% ⇒後ろからm文字目から、最後のn文字分を除いたもの
- 【文字列 切取８】%VAR:c1=c2% ⇒文字c1を文字c2に置換する。それぞれ複数の文字を指定することも可能

- 【ファイル 削除】del /a /q "c:\test\a.txt"
	- <<オプション>>
		- /a：読み取り専用、システムファイル、隠しファイル、アーカイブも含めて削除
		- /q：削除前に確認メッセージを表示しない
		- /s：指定されたファイルをすべてのサブディレクトリから削除する
	- <<応用例>>
		- "C:\test\b" フォルダ配下（サブディレクトリ含む）にある .dat ファイル全削除
			- del /s /a /q "C:\test\b\\*.dat"
- 【ファイル 移動】move "c:\test\a.txt" "c:\test\dst"
- 【ファイル コピー】copy "c:\test\a.txt" "c:\test\dst"
- 【フォルダ 名称変更】rename "c:\test\a.txt" "b.txt"
	- <<特記事項>>
		- 変更後のファイル &bold(){名} を指定します。パスを指定することはできません。

- 【フォルダ 作成】mkdir "c:\test\a"
- 【フォルダ 削除】rmdir /s /q "c:\test"
	- <<オプション>>
		- /s：ファイルやサブディレクトリも含めて削除する
		- /q：/sで削除する際に確認メッセージを表示しない
- 【フォルダ 移動】move "c:\test\src" "c:\test\dst"
	- <<特記事項>>
		- "c:\test\dst\src" が作成される。
- 【フォルダ コピー】echo d | xcopy /e /h /r /y "c:\test\src" "c:\test\dst\src"
	- <<特記事項>>
		- フォルダかファイルかを聞かれるため、「echo d」が必要。
		- 「xcopy /e /h /r /y "c:\test\src" "c:\test\dst"」では、"c:\test\dst\src" より下のファイル/フォルダはコピーされるが、"src" フォルダ自体はコピーされない。
	- <<オプション>>
		- /e：ファイルが存在しなくてもディレクトリごとコピーする
		- /h：隠しファイルやシステムファイルも全てコピーする
		- /r：読み取り専用属性のファイルも上書きコピーできるようにする
		- /y：同名のファイルが存在する場合、上書きの確認を行わない
		- /-y：同名のファイルが存在する場合、上書きの確認を行う
- 【フォルダ 名称変更】rename "c:\test\_old" "test\_new"
	- <<特記事項>>
		- 変更後のフォルダ &bold(){名} を指定します。パスを指定することはできません。
- 【フォルダ同期】robocopy "c:\test\src" "c:\test\dst" /MIR /XD "System Volume Information"
	- <<特記事項>>
		- "c:\test\src\a.txt" が "c:\test\dst\a.txt" としてコピーされるイメージ
	- <<オプション>>
		- /MIR：ディレクトリ ツリーをミラー化する。
		- /XD dir [ディレクトリ]... ：指定された名前/パスに一致するディレクトリを除外する。
		- /XF file [ファイル]... ：指定された名前/パス/ワイルドカードに一致するファイルを除外する。

- 【ファイル＆フォルダ ツリー取得】（隠しファイル、システムファイルは表示できない）
	- 【ファイル＆フォルダ】tree /f
	- 【フォルダのみ】tree
- 【ファイル＆フォルダ 一覧取得】（隠しファイル、システムファイル含む）
	- 【ファイル＆フォルダ】dir /b /s /a
	- 【フォルダのみ】dir /b /s /a:d
	- 【ファイルのみ】dir /b /s /a:a-d
		- 【.c、.hファイルのみ(※)】dir \*.c \*.h /b /s /a:a-d
			- (※)「\*.cc」のような「\*.c」を文字列として含まれる拡張子は省かれる。便利！

- 【システム属性設定】attrib +S C:\test.txt
- 【システム属性解除】attrib -S C:\test.txt
- 【隠し属性設定】attrib +H C:\test.txt
- 【隠し属性解除】attrib -H C:\test.txt

- 【２分後にシャットダウン】shutdown /s /t 120
- 【２分後に再起動】shutdown /r /t 120
- 【シャットダウンをキャンセル】shutdown /a

- 【シンボリックリンク作成（フォルダ）】mklink /d "c:\test" "d:\program files\test"
- 【シンボリックリンク作成（ファイル）】mklink "c:\test.txt" "d:\program files\test.txt"

- 【遅延展開変数設定】setlocal ENABLEDELAYEDEXPANSION ～ endlocal

- 【プログラム終了】exit /B 0

- 【環境変数 設定】setx MYPATH\_CODES "C:\codes"
- 【環境変数 解除】reg delete HKCU\Environment /v MYPATH\_CODES
- 【環境変数 存在確認】if {%MYPATH\_CODES%} == {0} ( ～環境変数が未存在～ )

- 【Windows 60秒後にシャットダウン】shutdown -s -t 60
- 【Windows 60秒後に再起動】shutdown -r -t 60

- for 文について
	- [参考] http://qiita.com/sawa\_tsuka/items/67be34bab1fdf3fb87f9
	- FOR (オプション) %%アルファベット１文字 IN (ループ処理の対象) DO コマンド
		- <<オプション>>
			- (オプション無し)：フォルダ内を対象にとる
			- /D：フォルダ名を対象にとる
			- /R：フォルダ名及びそのサブフォルダ内（そのフォルダの中のファイル名やフォルダ名）を対象にとる
			- /L：値を指定して代入する
			- /F：テキストファイル内の文章に対してトークンを取り出して代入する
	- 【フォルダ内対象】FOR %%アルファベット１文字 IN (ループ処理の対象) DO コマンド （例： FOR %%I IN (\*.bat) DO TYPE %%I）
	- 【フォルダ内のディレクトリのみ】FOR /D (ファイルパス) %%アルファベット１文字 IN (ループ処理の対象) DO コマンド （例： FOR /D C:\ %%I IN (\*.txt) DO TYPE %%I）
	- 【フォルダ配下の中身全部】FOR /R (ファイルパス) %%アルファベット１文字 IN (ループ処理の対象) DO コマンド （例： FOR /R C:\ %%I IN (\*.txt) DO TYPE %%I）
	- 【変数に値を代入してコマンドを実行】FOR /L %%アルファベット１文字 IN (開始値、増分、終了値) DO コマンド （例： FOR /L %%I IN (1,2,10) DO ECHO %%I）
	- 【その他】FOR /F "トークンオプション" %%アルファベット１文字 IN (ループ処理の対象) DO コマンド
		- <<トークンオプション>>
			- tokens= ：何番目のトークンを指定するか？
			- delims= ：トークンの区切り文字を指定
			- eol= ：この文字から始まる行を無視
			- skip= ：先頭から指定された行数、スキップする。
			- usebackq ：コマンドの出力を対象にする

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
