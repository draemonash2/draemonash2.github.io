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
- マルチカラーで選択する方法
	- GUIで実行
		1. 検索ウィンドウにて「検索(S)」へ検索したい文字列を入力
		1. 「すべて検索(E)」をクリック
		1. 「すべて検索 - 色つけ(B)」を実行
	- ショートカットキーで実行
		1. 検索ウィンドウにて「検索(S)」へ検索したい文字列を入力
		1. “Alt+b”を押下
- Grepウィンドウのタブ色等を変える
	1. Grepウィンドウを表示する
	1. 「ファイルタイプ別の設定」を開く
	1. 「設定のリスト」を開く
	1. Grepウィンドウを追加

# 設定
- 置換時の一括アンドゥ
	- メインメニュー「その他」→「動作環境」→「編集」→「全置換のやり直し」で"まとめて"を選択
	- メインメニュー「その他」→「動作環境」→「パフォーマンス」→「詳細」→「やり直しバッファサイズ」を"10240KB"に変更

# ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||F1|タグジャンプ|
||||F2|バックタグジャンプ|
||||F4|カーソル位置の単語色付け|
||||F11|アウトライン解析|
|Ctrl|||F1|ダイレクトタグジャンプ|
|Ctrl|||F3|ウィンドウ分割 上下|
|Ctrl|||F4|ウィンドウ分割 左右|
|Ctrl|||F6|表示/非表示 アウトライン解析枠|
|Ctrl|||F7|表示/非表示 ファイルマネージャー枠|
|Ctrl|||F8|表示/非表示 アウトプット枠|
||Shift||F1|コピー 相対ファイルパス|
||Shift||F2|コピー ファイル名|
||Shift||F3|コピー フォルダパス|
||Shift||F4|コピー 拡張子|
|Ctrl|Shift||F1|タグファイルの作成|
|Ctrl|Shift||↑/↓|BOX選択開始|
|Ctrl|Shift||c|タブを空白に置換してコピー|
|Ctrl|Shift||x|行切り取り|
|Ctrl|Shift||v|BOX貼り付け|
|Ctrl|Shift||del|行削除|
|Ctrl|||g|Grep|
|Ctrl|Shift||g|Grep置換|
|||Alt|b|検索文字列に色を付ける＠検索ウィンドウ|

[トップに戻る](../index.md)
