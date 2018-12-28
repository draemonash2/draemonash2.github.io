[トップに戻る](../index.md)

- 参考URL
	- http://www.atmarkit.co.jp/ait/articles/0702/15/news122_2.html

- 使用例
	``` vb
	Option Explicit
	
	On Error Resume Next
	
	Dim lResult
	lResult = 1 / 0
	
	Select Case Err.Number
	
		Case 0    'エラーなし
			'Do Nothing
		Case 11   '0除算エラー。
			MsgBox "0で割ることはできません。" & vbNewLine & Err.Description
			WScript.Quit
		Case 13   '型不一致エラー。
			MsgBox "数値を入力してください。" & vbNewLine & Err.Description
			WScript.Quit
		Case Else 'そのほかのエラーの場合。
			MsgBox "想定外のエラーです。" & vbNewLine & Err.Description
			WScript.Quit
	End Select

	On Error Goto 0

	'【出力結果】
	'0で割ることはできません。
	'0 で除算しました。
	```

[トップに戻る](../index.md)
