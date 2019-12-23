[トップに戻る](../index.md)

# アドイン
- [VbePlus](http://www.vector.co.jp/soft/dl/win95/prog/se176543.html)
	- インストール後、VBEのツールバー→アドイン→アドインマネージャ
	- VbePlus のロード方法を「起動時/ロード」に変更
- [MZTools](http://zabi.0am.jp/?p=2676)
	- インストールしても表示されない場合、HKEY\_CURRENT\_USER に必要なレジストリキーが登録されていない可能性がある。
	- Administrator の HKEY\_CURRENT\_USER からコピーすること。

# Tips
- モジュール名と関数名を同じにすることはできない。
- 二次元配列の再定義について
	- 一次元目の要素数は変更できない。二次元目のサイズのみ拡張できる。
	- 二次元目の要素数を変更した場合、一次元目にまで影響する。&br()（ex. (0, 1)、(1, 1) の要素数を持つ配列に対して (1, 1) ⇒ (1, 3) と要素数を変更した場合、(0, 3)、(1, 3) の配列となる）
- エラー「定数式が必要です」について
	- デバッグを途中で停止すると、設定しているはずの値が未定義扱いとなりコンパイルエラーが発生することがある。
	- 対策は ENUM 定義名を編集して再度戻す。
- Sheets と Worksheets の違い
	- Excel のシートには複数の種類がある。（ex.グラフシート、モジュールシート、ワークシート…）
	- Sheets は「上記のすべてを包含した」オブジェクト
	- Worksheets は「ワークシートのみ」のオブジェクト
- IntegerとLongどちらが良い？
	- 型の違いによる速度比較
		- ５千万回値の代入を行った結果、Integer型：515ms、Long型：465ms かかった。（10%程Long型の方が早い）
			- 環境：Windows 7 64bit
			- オフィス：Office 2013 32bit
		- 理由は動作環境が 32bit Office のため、 4Byte 型変数の方がアクセスが早いためと思われる。
	- 型の違いによるサイズ比較
		- Integer型変数（2Byte）なら１GB満たすまで５億個変数宣言できる
		- Long型変数（4Byte）なら１GB満たすまで2.5億個変数宣言できる（容量の圧迫は気にならない）
	- 上記を踏まえると Long 型を使用するのが良い！（アクセスも早いし、容量も気にするほど大きくないため）
- Const配列の作り方
	- Const配列は VBA では定義できないが、Const 文字列を Split することで実現可能。（書き換えられてしまうが。。）
	- Const C\_AAA = "Hello!,World!" : asArray = Split(C\_AAA, ",")
- CreateObject 関数について
	- 作成したオブジェクトは、使用後に必ず Nothing を設定すること！
	- オブジェクトが解放されなくなりメモリに残り続けることになる！
- 連続した空白を持つ文字列を Split 関数で分割した場合、空文字列の要素ができてしまう問題
	- 事前に連続した空白を一つにまとめてから Split する
		```vba
		'連続した空白を一つにまとめる
		Do While InStr(sTrgtLine, "  ")
			sTrgtLine = Replace$(sTrgtLine, "  ", " ")
		Loop
		sTrgtLine = Trim$(sTrgtLine)
		asSplitLine = Split(sTrgtLine, " ")
		```
- クラスモジュールのメリット・デメリット
	- デメリット
		- インスタンス化したオブジェクトを他クラスで参照できない。
			- ⇒オブジェクトを生成したクラスをグローバルにすれば良い
		- Property を使用する場合、コード量が多い
		- 構造体が使えない
			- クラスは入れ子にすることができる。
				```vba
				'Classモジュール ClassString
				Public Function GetDup( _
					ByVal sVal As String
				) As String
					GetDup = sVal & sVal
				End Function
				
				'Classモジュール ClassCom
				Public STR As New ClassString
				
				'標準モジュール Module1
				Public C As New ClassCom
				Sub Test02()
					Debug.Print C.STR.GetDup("はい")
				End Sub
				```
		- 列挙体が使えない
	- メリット
		- グローバル変数を隠蔽できる。
			- グローバル変数を変更する場合の影響範囲をクラス内に制限できる
		- 別クラスなら同じ関数名を使える。
			- インターフェース
				```vba
				Private Sub Class_Initialize()
				End Sub
				
				Public Function Execute() As String
				End Function
				```
			- クラス１
				```vba
				Implements ClassCmn
				
				Dim a As String
				
				Private Sub Class_Initialize()
					a = "A"
				End Sub
				
				Public Function ClassCmn_Execute() As String
					ClassCmn_Execute = a
				End Function
				```
			- クラス２
				```vba
				Implements ClassCmn
				
				Dim b As String
				
				Private Sub Class_Initialize()
					b = "B"
				End Sub
				
				Public Function ClassCmn_Execute() As String
					ClassCmn_Execute = b
				End Function
				```
			- 使用箇所
				```vba
				Sub test()
					Dim clChkExecTable(1) As ClassCmn
				
					Set clChkExecTable(0) = New Class1
					Set clChkExecTable(1) = New Class2
				
					Debug.Print clChkExecTable(0).Execute
					Debug.Print clChkExecTable(1).Execute
				
				End Sub
				```
		- 初期化処理呼び出し不要。
- 高速化方法まとめ
	- csv ファイル取り込み方法
	- 一覧へのアクセスは Dictionary を使う。
	- セルへのアクセスは variant 型変数へ代入してから書き戻す。
	- グラフ生成は極力オプションを減らす。
	- 正規表現検索は極力使わない。InStr で代用（先頭にあるかどうかは InStr() = 0 で判定する）
	- 空白埋めは一つ一つセルに代入せず、空白セル選択からの一括値代入。
	- With を使う。
	- Integer ではなく Long を使う。
- 配列・Collection・Dictionary の速度
	- 詳細な測定結果は添付ファイル「Array・Collection・Dictionary速度比較.xlsm」参照
		- 配列
			- 全体的に爆速！インデックスアクセスだけなら配列を使うこと！
		- Dictionary
			- インデックスアクセスは遅すぎるので、絶対インデックスアクセスするな！必ず For Each でアクセスすること！
		- Collection
			- 大きな要素番号にアクセスする際は遅くなる！ので、要素数が予想できない場合は基本使わない。ただし、Key アクセスの場合は問題なし！
- CPU 使用率抑える方法
	- 長い処理の間に sleep 1 を追加する。
	- 処理は長くなるが、バックグラウンドでの処理がはかどる。
- ファイルオープン「バイナリモード」について
	- 改行コードなどを区切り文字として扱わず、１バイト単位でファイルの先頭から逐次読み書きする。
	- バイナリファイルの読み書きをする際に使用する。
- Like 演算子について
	- 正規表現の「ように」比較できる。
	- 使用例：If sAddress Like "[!東京,横浜,千葉]\*" Then ～
		- 「東京、横浜、千葉ではない住所」の場合～
			
| 記号         | 意味                                        | 使用例      | マッチする文字列          |
|:---|:---|:---|:---|
| ?            | 任意の1文字                                 | たな?       | たなか、たなべ、たなし(など)       |
| \*           | 0個以上の任意の文字                         | たか\*      | たかだ、たかなか、たかやなぎ(など) |
| #            | 1文字の数値(0～9)                           | ##          | 01、26、95(など) |
| [charlist]   | charlistに指定した文字の中の1文字           | [A-F]       | A、B、C、D、E、F |
| [!charlist]  | charlistに指定した文字の中に含まれない1文字 | [!A-F]      | G 、H、I(など) |

- On Error の入れ子について
	- On Error は関数を跨いだ入れ子をしても問題なし。
	- ただし、関数内の入れ子は適用されない。
		```vb
		Sub main()
			On Error Resume Next
			On Error Resume Next
			Call subfunction
			Debug.Print 5 / 0 '⇒実行時エラー無し
			On Error GoTo 0
		   'Debug.Print 5 / 0 '⇒実行時エラーが発生してプログラムが停止する。
			On Error GoTo 0
		End Sub
		Sub subfunction()
			On Error Resume Next
			Debug.Print 5 / 0 '⇒実行時エラー無し
			On Error GoTo 0
			Debug.Print 5 / 0 '⇒実行時エラー無し
		End Sub
		```
- 大きさの単位「ポイント」と「ピクセル」について
	- ポイント：Microsoftが定義する単位（おそらく）。8.38 ポイントはMSゴシック11ポイント(半角) で8文字と少し表示できる幅。
	- ピクセル：ディスプレイの表示やプリンタの出力を構成する最小単位（小さな点）
- 無限ループによりExcelが操作不可になった場合の対処方法
	- ESCを押したままタスクバーでEXCEL・VBE・他のウィンドウをランダムにクリック
		- https://kotori-chunchun.hatenablog.com/entry/2019/01/13/010851
- 【型一覧】

| データ型 | 名称 | 消費メモリ | 格納できる範囲 |
|:---------|:-----|:-----------|:---------------|
| Integer | 整数型 | 2バイト | -32,768 ～ 32,767 |
| Long | 長整数型 | 4バイト | -2,147,483,648 ～ 2,147,483,647 |
| Single | 単精度浮動小数点数型 | 4バイト | -3.402823E38 ～ -1.401298E-45(負の値) 1.401298E-45 ～ 3.402823E38(正の値) |
| Double | 倍精度浮動小数点数型 | 8バイト | -1.79769313486232E308 ～ -4.94065645841247E-324(負の値) 4.94065645841247E-324 ～ 1.79769313486232E308(正の値) |
| Currency | 通貨型 | 8 バイト | -922,337,203,685,477.5808 ～ 922,337,203,685,477.5807 |
| String | 文字列型 | 2バイト | 最大約20億文字まで |
| Date | 日付型 | 8 バイト | 西暦100 年1月1日～西暦9999年12月31日までの日付と時刻 |
| Object | オブジェクト型 | 4 バイ | オブジェクトを参照するデータ型 |
| Variant | バリアント型 | 16バイト | 可変長の文字列型の範囲と同じ。 |
| Boolean | ブール型 | 2 バイト | 真 (True) または偽 (False) |

- 【演算子】

| 演算子 | 意味 | 変数への代入例 |
|:-------|:-----|:---------------|
| ＋ | 加算する | i = 15 + 5 ( ｉ の値は20) |
| － | 減算する | i = 15 - 5 ( ｉ の値は10) |
| ＊ | 乗算する | i = 5 * 4 ( ｉ の値は20) |
| ／ | 除算する | i = 15 / 5 ( ｉ の値は3) |
| ￥ | 除算の商 | i = 15 \ 2 ( ｉ の値は7) |
| Mod | 除算の余り | i = 15 Mod 2 ( ｉ の値は1) |
| ＾ | べき乗する | i = 2 ^ 5 ( ｉ の値は32) |

- 【エラー種別】
	- ex) CVErr(xlErrNum)
	
| 定数       | エラー番号 | セルのエラー値 |
|:-----------|:-----------|:---------------|
| xlErrDiv0  | 2007       | #DIV/0!        |
| XlErrNA    | 2042       | #N/A           |
| xlErrName  | 2029       | #NAME?         |
| XlErrNull  | 2000       | #NULL!         |
| XlErrNum   | 2036       | #NUM!          |
| XlErrRef   | 2023       | #REF!          |
| XlErrValue | 2015       | #VALUE!        |

- A1形式とR1C1形式の表記法

| 参照方法   | A1 表記 | R1C1 表記    | 説明                                          |
|:---|:---|:---|:---|
| 相対参照   | =A1     | =R[-2]C[-2]  | A1セルはC3セルから見て2行手前の2列手前のセル  |
| 絶対参照   | =$A$1   | =R1C1        | A1セルはどこから見てもA列の第1行目のセル      |

- [フォームコントロールとactiveXコントロール違い](https://www.ipentec.com/document/office-excel-difference-between-form-control-and-activex-control)
	- フォーム コントロール
		- セルの値を変更する用途、簡単なマクロの呼び出しに使う場合に最適
	- ActiveX コントロール
		- マクロのコードからの参照、コントロールの変化(イベント)でマクロを実行した場合に最適

# 構文

[こちらを参照](https://github.com/draemonash2/codes/blob/master/%E6%A7%8B%E6%96%87.xlsx)

# ライブラリ
- [【ＸＬＳファイル存在確認～オープン～クローズ】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelFile.bas)
- [【ＴＸＴファイル存在確認～オープン～クローズ】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【ＴＸＴファイル存在確認～オープン～クローズ（キャラクタセット指定）】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【フォルダ作成（再帰処理）】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【ファイル名一覧取得】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【ファイル・ディレクトリ 判別】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【ファイル・ディレクトリ 選択ダイアログ】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileSys.bas)
- [【ファイル・フォルダ情報取得】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/FileInfo.bas)
- [【コマンド実行】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/SysCmd.bas)
- [【プログレスバー表示】]
- [【性能測定】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/StopWatch.cls)
- [【エラー処理】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/Error.bas)
- [【配列の Push, Pop 関数】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ArrayMng.bas)
- [【イミディエイトウィンドウクリア】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/VbaMng.bas)
- [【シート一覧】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelOpe.bas)
- [【ツリー図オブジェクト生成】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelOpe.bas)
- [【ファイル名・フォルダ名抽出関数】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/StringMng.bas)
- [【セル範囲文字結合/分割関数】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelOpe.bas)
- [【セル属性取得関数】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelOpe.bas)
- [【ビット演算関数】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/ExcelOpe.bas)
- [【キー送信】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/SendKeys.bas)
- [【特殊貼り付け】](https://github.com/draemonash2/codes/tree/master/vba/MacroBook/lib/SpecialPaste.bas)

# サンプルコード
- [【プログラムテンプレート】](vba_プログラムテンプレート.md)
- 【シート存在確認】
	```vba
	'シート存在確認
	Dim bIsSheetExist As Boolean
	bIsSheetExist = False
	For Each wSheet In ThisWorkbook.Worksheets
		If wSheet.Name = sTrgtSheetName Then
			bIsSheetExist = True
		Else
			'Do Nothing
		End If
	Next wSheet
	```
- 【セル検索（存在しない場合を考慮）】
	- セル検索
		```vba
		Dim rFindResult As Range
		Dim sSrchKeyword As String
		Dim lSrchCellRow As Long
		Dim lSrchCellClm As Long
		
		With ThisWorkbook.Sheets(INPUT_SHEET_NAME)
			sSrchKeyword = KYWD_INPUT_DIR_PATH
			Set rFindResult = .Cells.Find(sSrchKeyword, LookAt:=xlWhole)
			If rFindResult Is Nothing Then
				MsgBox sSrchKeyword & "が見つかりませんでした"
			Else
				lSrchCellRow = rFindResult.Row
				lSrchCellClm = rFindResult.Column
			End If
		End With
		```
	- 直近セル情報取得
		```vba
		Public Type T_EXCEL_NEAR_CELL_DATA
			bIsCellDataExist As Boolean
			lRow As Long
			lClm As Long
			sCellValue As String
		End Type
		
		Public Function GetNearCellData( _
			ByVal shTrgtSht As Worksheet, _
			ByVal sSrchKey As String, _
			ByVal lRowOffset As Long, _
			ByVal lClmOffset As Long _
		) As T_EXCEL_NEAR_CELL_DATA
			Dim rFindResult As Range
			Set rFindResult = shTrgtSht.Cells.Find(sSrchKey, LookAt:=xlWhole)
			If rFindResult Is Nothing Then
				GetNearCellData.bIsCellDataExist = False
			Else
				GetNearCellData.bIsCellDataExist = True
				GetNearCellData.lRow = rFindResult.Row + lRowOffset
				GetNearCellData.lClm = rFindResult.Column + lClmOffset
				GetNearCellData.sCellValue = shTrgtSht.Cells( _
													GetNearCellData.lRow, _
													GetNearCellData.lClm _
												 ).Value
			End If
		End Function
		```
- 【セル重複削除】
	```vba
	For iRowIdx = .Cells(Rows.Count, 1).End(xlUp).Row To 2 Step -1
		For iChkTargetRowIdx = iRowIdx - 1 To 2 Step -1
			If .Cells(iRowIdx, 1) = .Cells(iChkTargetRowIdx, 1) Then
				.Cells(iChkTargetRowIdx, 1).EntireRow.Delete Shift:=xlShiftUp
			Else
				'Do Nothing
			End If
		Next iChkTargetRowIdx
	Next iRowIdx
	```
- [【グラフ作成＆画像変換】](vba_グラフ作成＆画像変換.md)
- 【テキストボックス作成】
	```vba
	Dim spTxtBox As Shape
	Set spTxtBox = shTrgtSht.Shapes.AddTextbox( _
						Orientation:=msoTextOrientationHorizontal, _
						Left:=10, _
						Top:=10, _
						Width:=10, _
						Height:=10 _
				   )
	With spTxtBox
		.TextFrame.Characters.Text = "エラーフレームなし"
		.TextFrame.AutoSize = True
	End With
	```
- 【正規表現】
	- 正規表現と文字列検索 InStr の速度についての考察…
		- マッチングを 500000 回繰り返すと、正規表現は約 2800 ms、InStr では約 50 ms。
		- 正規表現は 56 倍遅い！
	- 参考URL: http://officetanaka.net/excel/vba/tips/tips38.htm
		```vba
		Dim sSearchPattern As String
		Dim sTargetStr As String
		
		Dim iMatchIdx As Integer
		Dim iSubMatchIdx As Integer
		
		Dim oMatchResult As Object
		Dim oRegExp As Object
		Set oRegExp = CreateObject("VBScript.RegExp")
		
		sSearchPattern = "(\w+)\((\w+) (\w+)\)"
		sTargetStr = "TestFunc01(char aaa) TestFunc02(int bbb)"
		
		oRegExp.Pattern = sSearchPattern               '検索パターンを設定
		oRegExp.IgnoreCase = True                      '大文字と小文字を区別しない
		oRegExp.Global = True                          '文字列全体を検索
		Set oMatchResult = oRegExp.Execute(sTargetStr) 'パターンマッチ実行
		
		Debug.Print oMatchResult.Count
		For iMatchIdx = 0 To oMatchResult.Count - 1
			Debug.Print oMatchResult(iMatchIdx).SubMatches.Count
			For iSubMatchIdx = 0 To oMatchResult(iMatchIdx).SubMatches.Count - 1
				Debug.Print oMatchResult(iMatchIdx).SubMatches(iSubMatchIdx)
			Next iSubMatchIdx
		Next iMatchIdx
		```
- 【連想配列】
	- 連想配列を使用することにより、膨大な件数(※)の検索が劇的に早くなる。
		- ※ 検索対象 15 件以上（それ未満だと配列検索のほうが早い。.Exists API のオーバーヘッドのせい？）
			```vba
			Dim oPriceOfFruit As Object
			Set oPriceOfFruit = CreateObject("Scripting.Dictionary")
			
			'登録
			oPriceOfFruit.Add "リンゴ", "100円"
			oPriceOfFruit.Add "イチゴ", "400円"
			oPriceOfFruit.Add "メロン", "1000円"
			
			'存在確認
			If oPriceOfFruit.Exists("リンゴ") Then
				Debug.Print "Exists!"
			Else
				Debug.Print "Not Exists!"
			End If
			
			Set oPriceOfFruit = Nothing
			```

# VBE
## 設定
- Excel リボンに「開発」を追加
	- ツール ⇒ オプション ⇒ リボンユーザー設定にて [\*] 開発
- 変数宣言を強制 (変数名が誤りでも実行時までエラーが発生しないため変更)
	- ツール ⇒ オプション ⇒ 編集 ⇒ [\*] 変数の宣言を強制する
- 自動構文チェックを無視 (改行の度に警告ウィンドウが発生するため)
	- ツール ⇒ オプション ⇒ 編集 ⇒ [\_] 自動構文チェック
- エディタ文字・背景色の変更
	- ツール ⇒ オプション ⇒ エディタ ⇒ コードの表示色 を良しなに…
- 複数行コメントアウトボタン設置
	- 表示 ⇒ ツールバー ⇒ [\*] 編集 ⇒ オプション

## ショートカットキー

| 項目 | キー配置 |
|:---|:---|
| IntelliSense 実行 | Ctrl+Space |
| IntelliSense 選択 | Tab        |
| マクロ強制終了    | Ctrl+Break |
| 定義へ移動（≒タグジャンプ）  | Shift+F2 |
| 元の場所へ移動（≒タグジャンプ）  | Ctrl+Shift+F2 |

[トップに戻る](../index.md)
