[トップに戻る](../index.md)

# Tips
- CSV モード
	- メニューバーの表示⇒タブストップ⇒CSVモード
- 連続Grep方法
	- 正規表現で複数単語を指定
		- ex) (XXX|YYY)
		- ただしこの方法は秀丸の「検索・Grep の最大文字数：4000文字」を満たす必要があるため、&br()膨大な数を検索したい場合には不利。
	- 連続Grepできる秀丸マクロ
		- ★TODO★
- 複数行をGrep置換
	- 検索する文字列
		- ^volatile\s(\w+)\s(K_DIAG_YYY)\n.*\nvolatile\s(\w+)\s(K_DIAG_XXX)
	- 置換する文字列
		- [\2\t\1][\4\t\3]
	- 置換前
		``` c
		volatile UB K_DIAG_XXX
		volatile UB K_DIAG_YYY
		volatile UW K_DIAG_XXXX
		volatile UB K_DIAG_XXX
		volatile UD K_DIAG_ZZZ
		```
	- 置換後
		``` c
		volatile UB K_DIAG_XXX
		[K_DIAG_YYY	UB][K_DIAG_XXX	UB]
		volatile UD K_DIAG_ZZZ
		```

# 設定
- 置換時の一括アンドゥ
	- メインメニュー「その他」→「動作環境」→「編集」→「全置換のやり直し」で"まとめて"を選択
	- メインメニュー「その他」→「動作環境」→「パフォーマンス」→「詳細」→「やり直しバッファサイズ」を"10240KB"に変更

[トップに戻る](../index.md)
