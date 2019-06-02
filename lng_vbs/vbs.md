[トップに戻る](../index.md)

# Todo

# Tips
- On Error Goto ラベルが使えない（On Error Resume Next は OK）
- VBA では使えるはずの未定義配列判定用の関数 Sgn() は使えない。
	- 代替方法の一つ目は、初期化直後に要素数 -1 配列として再定義し、判定時には要素数-1＝未定義配列として判定する。
	- 二つ目は、On Error を使ってエラー発生を検出する方法。
- プログラムを強制終了したい場合は、ESCキーを押し続ければ終了する「場合」がある。
- format関数は存在しない。そのため、数値を０埋めしたい場合、String関数を使う必要がある　
	- 例）String( 2 - Len(lNum), "0" ) & lNum
- WScript.Shell の .CurrentDirectory の危険性について
	- 上記メソッドは、スクリプトに対するドラッグ＆ドロップにて起動した場合ドラッグ元で使用するファイラーのパスになってしまう。
		- 【実験】
			- <<プログラム（OutputTest.vbs）>>
				- MsgBox WScript.CreateObject( "WScript.Shell" ).CurrentDirectory & " ： " & Replace( WScript.ScriptFullName, "\" & WScript.ScriptName, "" )
			- <<条件>>
				- 「C:\codes\vbs\a.mp3」を「C:\codes\vbs\OutputTest.vbs」に向けて X-Finder からドラッグ＆ドロップした場合
			- <<出力結果>>
				- C:\prg\_exe\xf11-10 ： C:\codes\vbs
- 文字列のバイト数を返却する関数 LenB() は、Unicode のバイト数を返却するため半角文字も２バイトとして返却する。
	- LebB( "あああ " ) ⇒ 8
- メッセージ出力処理の違い
	- 結論
		- MsgBox
			- タイトル,アイコンを変更できる！
			- cscriptから実行してもポップアップしてしまう！
			- 自動的に改行する(≒puts)
				- → GUIからの使用のみを想定している場合に使用する！
		- WScript.Echo
			- タイトル,アイコンを変更できない！
			- cscript/wscriptの使い分けでポップアップと標準出力を分けられる！
			- 自動的に改行する(≒puts)
				- → GUI/CUI双方からの使用を想定している場合に使用する！
		- Wscript.StdOut.WriteLine は使用禁止！
			- ダブルクリックから使用できない！
			- 自動的に改行しない(≒printf)
				- → CUIからのみかつ、自動的に改行させたくない場合に使用する！
	- 実行可否比較

|                    | MsgBox           | WScript.Echo     | Wscript.StdOut.WriteLine |
|:---|:---|:---|:---|
| ダブルクリック起動 | ポップアップ出力 | ポップアップ出力 | 実行不可 |
| wscript.exe        | ポップアップ出力 | ポップアップ出力 | 実行不可 |
| cscript.exe        | ポップアップ出力 | 標準出力         | 標準出力 |

- バッチファイルで設定した環境変数を参照する方法
	- test.bat
	``` bat
	set MATCH_DIR_NAME=codes
	set REMOVE_DIR_LEVEL=0
	.\test.vbs
	```
	- test.vbs
	``` vb
	Dim objWshShellEnv
	Set objWshShellEnv = WScript.CreateObject("WScript.Shell").Environment("Process")
	sMatchDirName = objWshShellEnv.Item("MATCH_DIR_NAME")
	lRemeveDirLevel = objWshShellEnv.Item("REMOVE_DIR_LEVEL")
	```

# 構文
## 「～」は改行を示す。
```
【変数強制定義】Option Explicit
【変数定義①】Dim 変数名
【変数定義②】Private 変数名
【変数定義③】Public 変数名
【変数定義④】ReDim 変数名
【配列定義】Dim 配列変数名(最終要素番号) '要素数ではなく最終要素番号！
【定数定義】Const 定数名
【関数定義】Function FuncA( ByVal Val1, ByRef Val2 ) ～ FuncA = Val1 ～ End Function
【関数呼出】Call FuncA()
【クラスインスタンス生成】Dim oLog ～ Set oLog = New LogMng
【クラスインスタンス破棄】Set oLog = Nothing
【ブロック脱出（Sub/Function/For/Do）】Exit (Sub|Function|For|Do)
【連続コマンド実行】Dim sStr : sStr = "abc"
【プログラム終了】WScript.Quit

【if】If iVal = 1 Or iVal = 2 Then ～ ElseIf iVal = 3 Then ～ Else ～ End If
【if（空オブジェクト確認）】If objTest Is Nothing Then ～ Else ～ End If
【switch】Select Case iVal ～ Case 1 ～ Case Else ～ End Select
【for】For iVal1 = 1 To 3 [Step 1] ～ Next
【for each】For Each Value in Values ～処理～ Next
【while】Do ～(条件式＝真)～ Loop While 条件式
【do while】Do While 条件式 ～(条件式＝真)～ Loop
【do until】Do Until 条件式 ～(条件式＝偽)～ Loop
【with】With オブジェクト名 ～ End With
【コメント】'コメント
【入力】sStr = InputBox( "テキストを入力してください", "title", "default value" )
【出力①】MsgBox "Hello world", vbOKCancel, "title"
【出力②】WScript.Echo "Hello world"
【出力③】Wscript.StdOut.WriteLine "Hello world" '出力先は標準出力。ただし、この方法は cscript.exe からの起動に限られる。例）cscript.exe xxx.vbs
【確認処理】Dim vAnswer ～ vAnswer = MsgBox("処理を継続しますか？", vbOKCancel, "タイトル") '第二引数は表示ボタンの種類を指定。ボタンの種類は [こちら](http://www.kanaya440.com/contents/script/vbs/function/others/msgbox.html) 参照。

【正規表現】サンプルコード参照

【連想配列 定義】Dim oPriceOfFruit ～ Set oPriceOfFruit = CreateObject("Scripting.Dictionary") 
  【連想配列 キー/項目追加】oPriceOfFruit.Add "リンゴ", "100円"
  【連想配列 存在確認】oPriceOfFruit.Exists("リンゴ")
  【連想配列 キー取得（For Each）】For Each vKey In oPriceOfFruit ～ MsgBox vKey ～ Next 'vKey は variant 型
  【連想配列 項目取得（キー）】oPriceOfFruit.Item("リンゴ")
  【連想配列 キー取得（インデックス）】oPriceOfFruit.Keys()(0) '０オリジン（アクセスが遅すぎるので注意！）
  【連想配列 項目取得（インデックス）】oPriceOfFruit.Items()(0) '０オリジン（アクセスが遅すぎるので注意！）
  【連想配列 キー置換】oPriceOfFruit.Key("リンゴ") = "りんご"
  【連想配列 キー関連付け】oPriceOfFruit.Item("リンゴ") = "200円"
  【連想配列 キー/項目数取得】oPriceOfFruit.Count
  【連想配列 キー/項目削除】oPriceOfFruit.Remove("リンゴ") '指定されたキーが存在しない場合はエラー
  【連想配列 キー/項目全削除】oPriceOfFruit.RemoveAll
  【連想配列 配列変換（項目）】asFruitPrice = oPriceOfFruit.Items 'Variant型配列、０オリジン
  【連想配列 配列変換（キー）】asFruitName = oPriceOfFruit.Keys 'Variant型配列、０オリジン
  【連想配列 設定変更】oPriceOfFruit.CompareMode = vbBinaryCompare '大/小文字区別 /vbTextCompare（大/小文字区別しない

【コレクション 定義】Dim cTrgtPaths ～ Set cTrgtPaths = CreateObject("System.Collections.ArrayList")
  【コレクション 追加】cTrgtPaths.Add "c:\test\a.txt"
  【コレクション 値取り出し（単一）】cTrgtPaths.Item(0) 'c:\test\a.txt（０オリジン）
  【コレクション 値取り出し（ループ）】Dim sTrgtPath ～ For Each sTrgtPath In cTrgtPaths ～ MsgBox sTrgtPath ～ Next
  【コレクション 要素数取得】cTrgtPaths.Count '要素数（末尾の要素番号ではない）
  【コレクション 削除】cTrgtPaths.Remove "c:\test\b.xlsx" '要素の値を指定する。要素番号では削除できない。
  【コレクション 挿入】cTrgtPaths.Insert 2, "c:\test\e.ppt" '要素番号2へ挿入される（元要素番号2以降が一要素ずれる）
  【コレクション ソート】cTrgtPaths.Sort
  【コレクション 配列変換】Dim avTrgtPaths ～ avTrgtPaths = cTrgtPaths.ToArray() 'Variant型配列に変換
  【コレクション 全要素削除】cTrgtPaths.Clear

【エラー設定】On Error Resume Next
【エラー解除】On Error Goto 0
【エラー番号】Err.Number
【エラー内容】Err.Description

【WScriptShellObject 取得】Dim objWshShell ～ Set objWshShell = WScript.CreateObject("WScript.Shell")
  【バッチ実行①】objWshShell.Exec("C:\test.bat") 'Execは標準入出力できるが、WSH 5.6以降からしかサポートされていないので注意
  【バッチ実行②】objWshShell.Run "C:\test.bat", 0, True '第二引数：ウィンドウの表示スタイル（ウィンドウを非表示、別のウィンドウをアクティブ）、第三引数：プログラムの実行が終了するまでスクリプトを待機させるかどうか（詳細は[こちら](https://msdn.microsoft.com/ja-jp/library/cc364421.aspx)）
  【コマンド実行】objWshShell.Run "cmd /c echo.> ""C:\test.txt""", 0, True
  【レジストリ読込】objWshShell.RegRead("HKCU\WshTest\Test1")
  【レジストリ書込】objWshShell.RegWrite("HKCU\WshTest\Test1", "test", "REG\_SZ") 'キー/値,設定値,データ型
  【環境変数 値取得＆更新】objWshShell.Environment("User").Item("MYPATH\_CODES") 'User:現在のユーザー, Process:現在のプロセス, System:全ユーザー, Volatile:現在のログオン
  【特殊フォルダのパス取得】objWshShell.SpecialFolders("Desktop") 'デスクトップフォルダ
    ↑取得できるフォルダは「AllUsersDesktop」 「AllUsersStartMenu」 「AllUsersPrograms」 「AllUsersStartup」 「Desktop」 「Favorites」 「Fonts」 「MyDocuments」 「NetHood」 「PrintHood」 「Programs」 「Recent」 「SendTo」 「StartMenu」 「Startup」 「Templates」
  【ショートカット 作成】With objWshShell.CreateShortcut( "c:\test\src.txt.lnk" ) ～ .TargetPath = "c:\test\dst.txt" ～ .Save ～ End With
  【ショートカット 指示先パス取得】objWshShell.CreateShortcut( "c:\test\src.txt.lnk" ).TargetPath '参照だけでなく変更も可
  【ショートカット 指示先パス更新】With objWshShell.CreateShortcut( "c:\test\src.txt.lnk" ) ～ .TargetPath = "c:\test\dst2.txt" ～ .Save ～ End With
  【ショートカット コメント更新】With objWshShell.CreateShortcut( "c:\test\src.txt.lnk" ) ～ .Description = "テストコメント" ～ .Save ～ End With
  【ショートカット 引数更新】With objWshShell.CreateShortcut( "c:\test\src.txt.lnk" ) ～ .Arguments = " /b" ～ .Save ～ End With

【FileSystemObject 取得】Dim objFSO ～ Set objFSO = CreateObject("Scripting.FileSystemObject")
  【ファイル コピー①】objFSO.CopyFile "C:\codes\a.txt", "C:\codes\test\" '<src> <dst> [<overwrite>] 、<dst>の末尾に "\" をつけること！
  【ファイル コピー②】objFSO.CopyFile "C:\codes\a.txt", "C:\codes\test\a.txt" '<src> <dst> [<overwrite>]
  【ファイル 削除】objFSO.DeleteFile "c:\test", True
  【ファイル 移動/リネーム】objFSO.MoveFile "C:\codes\src.txt", "C:\codes\dst.txt"
  【ファイル 存在確認】objFSO.FileExists("c:\codes\a.txt") 'True
  【ファイル 情報取得】objFSO.GetFile( "C:\codes\a.txt" ).Attributes '32 (※)値の意味は [【ファイル・フォルダ情報取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs) 参照
  【ファイル 隠しファイル化】objFSO.GetFile( "C:\codes\a.txt" ).Attributes = 2
  【ファイル 絶対パス取得】objFSO.GetAbsolutePathName( "C:\codes\a.txt" ) ' C:\codes\a.txt
  【ファイル ドライブ名取得】objFSO.GetDriveName( "C:\codes\a.txt" ) ' C:
  【ファイル ファイル名取得】objFSO.GetFileName( "C:\codes\a.txt" ) ' a.txt
  【ファイル ファイルベース名取得】objFSO.GetBaseName( "C:\codes\a.txt" ) ' a
  【ファイル 拡張子取得】objFSO.GetExtensionName( "C:\codes\a.txt" ) ' txt
  【ファイル 親フォルダパス取得】objFSO.GetParentFolderName( "C:\codes\a.txt" ) ' C:\codes
  【フォルダ コピー】objFSO.CopyFolder "C:\codes\src", "C:\codes\dst", True '配下フォルダ/ファイルも丸ごとコピー
  【フォルダ 削除】objFSO.DeleteFolder "C:\codes\test", True '配下フォルダ/ファイルも丸ごと削除
  【フォルダ 作成】objFSO.CreateFolder( "C:\codes\test" ) '親フォルダがない場合、エラーになる
  【フォルダ 移動/リネーム】objFSO.MoveFolder "C:\codes\src", "C:\codes\dst" '配下フォルダ/ファイルも丸ごと移動/リネーム
  【フォルダ 情報取得】objFSO.GetFolder( "C:\codes" ).Attributes '32 (※)値の意味は [【ファイル・フォルダ情報取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs) 参照
  【フォルダ 存在確認】objFSO.FolderExists( "C:\codes" ) 'True
  【親フォルダパス取得】objFSO.GetParentFolderName( "C:\codes\src" ) ' C:\codes
  【ＴＸＴファイル オープン】Set objTxtFile = objFSO.OpenTextFile("c:\codes\test\a.txt", 1, True) '第二引数：IOモード（1:読出し、2:新規書込み、8:追加書込み）、第三引数：新しいファイルを作成するかどうか
  【ＴＸＴファイル クローズ】objTxtFile.Close
  【ＴＸＴファイル 読込（逐次）】Do Until objTxtFile.AtEndOfStream ～ strLine = objTxtFile.ReadLine ～ Loop
  【ＴＸＴファイル 読込（一括）】sTextAll = objTxtFile.ReadAll
  【ＴＸＴファイル 書込】objTxtFile.WriteLine strLine

【置換】Replace(文字列変数, "  ", "")
【文字列検索（前方）】InStr("abcabc", "bc") ' 先頭からの位置、１オリジン（いない場合は0が返る
【文字列検索（後方）】InStrRev("abcabc", "bc")  '末尾からの位置、１オリジン（いない場合は0が返る
【文字列 長さ（文字数）】Len("リンゴ") '3
【文字列 長さ（バイト数）】LenB("リンゴ") '6
【文字列結合】"abcdef" & "gh"
【文字列抽出 左】Left("abcd", 3) 'abc
【文字列抽出 中】Mid("abcdefgh", 3, 2) 'cd（１オリジン）
【文字列抽出 右】Right("abcd", 2) 'cd
【文字列⇒ASCII 変換】Asc(文字)
【文字列の数値判定】IsNumeric( sStr ) '1⇒True、"a"⇒False、""⇒False
【ASCII⇒文字列 変換】Chr(ASCIIコード) (ex. Chr(Asc("①") + 1) ⇒ ② )
【文字列繰り返し】"a" & String(4, "b") 'abbbb
【大文字化】UCase("aaa")
【小文字化】LCase("AAA")
【配列再定義】ReDim Preserve 配列名(5) '要素数は０オリジン。左の例では要素数６の配列が作成される
【配列最大要素数】UBound(配列名) '返却値は０オリジン。返却値が３の場合、0～3 の配列であることを示す
【要素数０（未初期化）/要素数１配列判定】Dim asArray() ～ ReDim asArray(-1) ～ If Ubound(asArray) = -1 Then ～（未定義配列）～ Else ～（定義済み配列）～ End If
【配列 結合】Join(配列, ",")
【配列 分割】objWords = Split( sFilePath , "\" ) ' 格納先の変数は、配列ではなくオブジェクトとして定義しなければならないことに注意！
【型取得（文字列）】TypeName("Test") 'String
【型取得（値）】VarType("Test") '8（値の詳細は [こちら](http://www.kanaya440.com/contents/script/vbs/function/data/var_type.html) 参照）
【10⇒16進数変換】変数 = Hex(734)
【16⇒10進数変換】変数 = CLng("&H" & "FA")
【符号つき16進数表現】&HFFF0
【符号なし16進数表現】&HFFF0&
【数値⇒文字列 変換】CStr(234.5) ' "234.5"
【文字列⇒数値 変換①】CDbl("234.5") ' 234.5
【文字列⇒数値 変換②】CLng("234.5") ' 234
【改行】( vbNewLine | vbCr | vbLf | vbCrLf )
【少数 正数 切り捨て①】Fix( 99.224 ) '99
【少数 正数 切り捨て②】Int( 99.224 ) '99
【少数 負数 切り捨て①】Fix( -99.224 ) '-99 (※)負数の場合は切り上げ
【少数 負数 切り捨て②】Int( -99.224 ) '-100 (※)負数の場合は切り下げ
【少数 正数 四捨五入（第一位）】Round( 99.555, 0 ) '100
【少数 正数 四捨五入（第二位）】Round( 99.555, 1 ) '99.6
【少数 正数 四捨五入（第三位）】Round( 99.555, 2 ) '99.56
【少数 負数 四捨五入（第一位）】Round( -99.555, 0 ) '-100
【少数 負数 四捨五入（第二位）】Round( -99.555, 1 ) '-99.6
【少数 負数 四捨五入（第三位）】Round( -99.555, 2 ) '-99.56
【少数 正数 切り上げ（第一位）】Round( 99.224 + 0.5, 0 ) '100
【少数 正数 切り上げ（第二位）】Round( 99.224 + 0.05, 1 ) '99.3
【少数 負数 切り上げ（第一位）】Round( -99.224 - 0.5, 0 ) '-100
【少数 負数 切り上げ（第二位）】Round( -99.224 - 0.05, 1 ) '-99.3
【少数 正数 切り下げ（第一位）】Round( 99.224 - 0.5, 0 ) '99 （＝切り捨て）
【少数 正数 切り下げ（第二位）】Round( 99.224 - 0.05, 1 ) '99.2
【少数 負数 切り下げ（第一位）】Round( -99.224 + 0.5, 0 ) '-99 （＝切り捨て）
【少数 負数 切り下げ（第二位）】Round( -99.224 + 0.05, 1 ) '-99.2

【現在時刻取得】Now() 'YYYY/DD/MM HH:MM:SS
【現在年月日取得】Date() 'YYYY/MM/DD
【0:00から現在までの経過時間（秒数）】Timer() '49229.781（13:40:29 .781）
【日付比較】If DateDiff("s", sCmpBaseTime, sModDate ) > 0 Then ～（ sModDate が新しい）～ ElseIf DateDiff("s", sCmpBaseTime, sModDate ) < 0 Then ～（ sModDate が古い）～ Else ～（ sModDate = sCmpBaseTime）～ End If '日付は "YYYY/MM/DD" の文字列として指定する
【Wait処理】WScript.sleep(3000) 'ms単位

【実行スクリプト ファイルパス】WScript.ScriptFullName
【実行スクリプト ファイル名（拡張子あり）】WScript.ScriptName
【実行スクリプト ファイルベース名①】Mid( WScript.ScriptName, 1, InStrRev( WScript.ScriptName, "." ) - 1 )
【実行スクリプト ファイルベース名②】objFSO.GetBaseName( WScript.ScriptName )
【実行スクリプト フォルダパス①】Replace( WScript.ScriptFullName, "\" & WScript.ScriptName, "" )
【実行スクリプト フォルダパス②】objFSO.GetParentFolderName( WScript.ScriptFullName )
【実行スクリプト フォルダパス③】objWshShell.CurrentDirectory
  ↑実行スクリプトがインクルードによって実行された場合、カレントフォルダが変わってしまうため使用しない。

【コマンドライン引数 カウント】WScript.Arguments.Count
【コマンドライン引数 取得】WScript.Arguments(0) '０オリジン（例：test.vbs aaa bbb の時、WScript.Arguments(0) は aaa）

【名前定義 追加】ThisWorkbook.Names.Add Name:="テスト", RefersTo:="=indirect(""R1C1"",false)" 'R1C1で指定すること
【名前定義 削除】ThisWorkbook.Names("テスト").Delete

【キー操作送信】Application.SendKeys "+{DOWN}", True ' "+"：Shift、"^"：Ctrl、"%"：ALT、"{DOWN}"：下キー

【Excel コマンド実行】Application.CommandBars.ExecuteMso "CellsDelete" 'セル削除
  ↑アンドゥはできないので注意。
【条件付き書式 追加】.Range("A1:B2").FormatConditions.Add Type:=xlExpression, Formula1:="=$A1=""あ"""
【条件付き書式 書式設定①】.Range("A1:B2").FormatConditions(1).Interior.Color = RGB(255, 255, 0)
【条件付き書式 書式設定②】.Range("A1:B2").FormatConditions(1).Font.Color = RGB(0, 255, 0)
```

# ライブラリ
- [【ログ出力クラス】](https://github.com/draemonash2/codes/blob/master/vbs/lib/Log.vbs)
- [【プログレスバークラス】](https://github.com/draemonash2/codes/blob/master/vbs/lib/ProgressBar.vbs)
- [【ストップウォッチクラス】](https://github.com/draemonash2/codes/blob/master/vbs/lib/StopWatch.vbs)
- [【IEウィンドウ出力クラス】](https://github.com/draemonash2/codes/blob/master/vbs/lib/IE.vbs)

- [【定義済み配列判定】](https://github.com/draemonash2/codes/blob/master/vbs/lib/Array.vbs)
- [【ファイル・フォルダパス一覧出力】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【フォルダ作成（再帰的）】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【ファイル・フォルダ判定】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【ファイル・ディレクトリ 選択ダイアログ】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【ファイル・フォルダ情報取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【ドライブ情報取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【空フォルダ削除（再帰的）】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【"\_XXX"付与パス取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/FileSystem.vbs)
- [【文字列：末尾区切り文字以降の文字列取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：末尾区切り文字以降の除去】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：フォルダパス取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：ファイル名取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：ファイル名（拡張子なし）取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：拡張子取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【文字列：文字列バイト長取得】](https://github.com/draemonash2/codes/blob/master/vbs/lib/String.vbs)
- [【管理者権限実行】](https://github.com/draemonash2/codes/blob/master/vbs/lib/Windows.vbs)
- [【コマンド実行（VBS版）】](https://github.com/draemonash2/codes/blob/master/vbs/lib/Windows.vbs)
- [【X-Finder  ini ファイル操作】](https://github.com/draemonash2/codes/blob/master/vbs/lib/X-Finder.vbs)
- [【iTunes 操作ライブラリ】](https://github.com/draemonash2/codes/blob/master/vbs/lib/iTunes.vbs)
- [【vbs から vba マクロ呼び出し】](https://github.com/draemonash2/codes/blob/master/vbs/lib/Excel.vbs)
- [【外部プログラムインクルード】](https://github.com/draemonash2/codes/blob/master/vbs/lib/_include_sample.vbs)

# サンプルコード
- [【iTuneControl】](https://github.com/draemonash2/vbs/vbs_itunes.md)
- [【エラー処理（VBS版）】](https://github.com/draemonash2/vbs/vbs_error.md)
- 【正規表現（VBS版）】
	``` vb
	Dim sSearchPattern
	Dim sTargetStr
	sSearchPattern = "((\w+)\((\w+) (\w+)\))"
	sTargetStr = "TestFunc01(char aaa) TestFunc02(int bbb)"
	
	Dim oRegExp
	Set oRegExp = CreateObject("VBScript.RegExp")
	oRegExp.Pattern = sSearchPattern                '検索パターンを設定
	oRegExp.IgnoreCase = True                       '大文字と小文字を区別しない
	oRegExp.Global = True                           '文字列全体を検索
	
	Dim oMatchResult
	Set oMatchResult = oRegExp.Execute(sTargetStr)  'パターンマッチ実行
	
	Dim iMatchIdx
	Dim iSubMatchIdx
	Dim sOutStr
	sOutStr = "マッチ数：" & oMatchResult.Count
	For iMatchIdx = 0 To oMatchResult.Count - 1
		sOutStr = sOutStr & vbNewLine & "サブマッチ数：" & oMatchResult(iMatchIdx).SubMatches.Count
		For iSubMatchIdx = 0 To oMatchResult(iMatchIdx).SubMatches.Count - 1
			sOutStr = sOutStr & "　" & oMatchResult(iMatchIdx).SubMatches(iSubMatchIdx)
		Next
	Next
	
	MsgBox sOutStr
	
	'【出力結果】
	' マッチ数：2
	' サブマッチ数：4　TestFunc01(char aaa)　TestFunc01　char　aaa
	' サブマッチ数：4　TestFunc02(int bbb)　TestFunc02　int　bbb
	```
- 【配列の Push, Pop 関数】★
- 【ビット演算関数】★
- 【配列、連想配列 内容出力】

# その他
- 【演算子】

| 演算子 | 意味 |
|:---|:---|
| - | 減算 |
| * | 積算 |
| / | 除算 |
| \ | 除算(まるめ) |
| Mod | 剰余 |
| < | 小さい |
| > | 大きい |
| <= | 小さいか等しい |
| >= | 大きいか等しい |
| == | 等しい |
| <> | 異なる |
| And | 論理積 |
| Or | 論理和 |
| Not | 否定 |
| Xor | 排他的論理和 |
| & | 文字列連結 |
| + | 文字列連結 |

[トップに戻る](../index.md)
