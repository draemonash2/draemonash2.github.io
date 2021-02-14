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
- コマンドラインから実行する方法
	- 「cscript //nologo」をつけて実行する。
		- ex）cscript //nologo OutputShortcutTrgtPath.vbs -v C:\Users\test.txt.lnk

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

- フォルダ選択ダイアログ比較
	- FileDialog
		- 実行例
			- `CreateObject("Excel.Application").FileDialog(msoFileDialogFolderPicker)`
		- メリット/デメリット
			- ×：Excelを起動する必要があるため、起動が遅い
			- ○：デフォルトのフォルダを指定できる
	- BrowseForFolder
		- 実行例
			- `CreateObject("Shell.Application").BrowseForFolder(0, "フォルダを選択してください", &H200, "c:\codes")`
		- メリット/デメリット
			- ○：起動が早い
			- ×：デフォルトのフォルダを指定できない（ルートフォルダのみ指定できる）

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

- 環境変数展開比較
	- objWshShell.ExpandEnvironmentStrings("c:\%XXX%\test.log")
		- "ユーザ環境変数"と"システム環境変数"で同じ環境変数が定義されている場合、システム環境変数が参照される
		- 環境変数が入れ子になっている場合は再帰的に展開される
		- 環境変数が存在しない場合、展開されない。(%XXX%のまま返却される)
	- objWshShell.Environment("System").Item("XXX")
		- 環境変数が入れ子になっている場合は１回分のみ展開される

# 構文

[こちらを参照](https://github.com/draemonash2/codes/blob/master/%E6%A7%8B%E6%96%87.xlsx)

# ライブラリ

- [【ログ出力クラス】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/Log.vbs)
- [【プログレスバークラス】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/ProgressBar.vbs)
- [【ストップウォッチクラス】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/StopWatch.vbs)
- [【IEウィンドウ出力クラス】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/IE.vbs)

- [【定義済み配列判定】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/Array.vbs)
- [【ファイル・フォルダパス一覧出力】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【フォルダ作成（再帰的）】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【ファイル・フォルダ判定】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【ファイル・ディレクトリ 選択ダイアログ】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【ファイル・フォルダ情報取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)

- [【ドライブ情報取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【空フォルダ削除（再帰的）】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【"\_XXX"付与パス取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/FileSystem.vbs)
- [【文字列：末尾区切り文字以降の文字列取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：末尾区切り文字以降の除去】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：フォルダパス取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：ファイル名取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：ファイル名（拡張子なし）取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：拡張子取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【文字列：文字列バイト長取得】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/String.vbs)
- [【管理者権限実行】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/Windows.vbs)
- [【コマンド実行（VBS版）】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/Windows.vbs)
- [【X-Finder  ini ファイル操作】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/X-Finder.vbs)
- [【iTunes 操作ライブラリ】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/iTunes.vbs)
- [【vbs から vba マクロ呼び出し】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/Excel.vbs)
- [【外部プログラムインクルード】](https://github.com/draemonash2/codes/tree/master/vbs/_lib/_include_sample.vbs)

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
