[トップに戻る](../index.md)

# Tips

- WSL2起動方法
	- プログラム「wsl」を起動する
- [Linux⇔Windows間のファイルアクセス方法](https://qiita.com/Uchitaso/items/6e0a7859e87bb8bdb527)
	- Windows上でLinuxのファイルにアクセス
		- エクスプローラからアドレス「\\wsl$」にアクセスする
	- Linux上でWindowsのファイルにアクセス
		- 「/mnt/」にアクセスする
- [WSL2コンソールのコピペ方法](https://qiita.com/kenji0x02/items/f77008985818583bf32b)
	- コピー
		- 方法１：テキストを選択してコピー
		- 方法２：テキストを選択してCtrl+Shift+C
			- ただし、設定を有効化する必要あり。
				- 「WSL2コンソールのプロパティ」->「編集」->「編集オプション」->「Ctrl+Shift+C/Vをコピー/貼り付けとして使用する(C)」をチェック
	- ペースト
		- 方法１：右クリック
		- 方法２：Ctrl+Shift+V
- Windows TerminalからWSL2を起動する方法
	1. Windows Terminal タイトルバーの下矢印をクリック
	1. 起動したいLinuxディストリビューションを選択
- [Windows Terminalからのデフォルト起動をWSL2に変更する方法](https://www.asobou.co.jp/blog/web/windows-terminal#3_Windows_TerminalWSL2)
	1. Windows Terminal にて「Ctrl + ,」押下
	1. 開いた設定ファイル(settings.json)内の「defaultProfile」を起動したいLinuxディストリビューションのGUIDに変更する

# コマンド
## Linux 共通コマンド

- [Linuxの基本コマンドはこちら](https://github.com/draemonash2/wiki/blob/master/sft_linux/linux.md)

## WSL2 関連コマンド

- VIM設定ファイル
	- ★

# ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||Tab|コマンド/ファイル名補完|
|Ctrl|||p/n|コマンド履歴呼出し(1つ前/1つ先)|
|Ctrl|||r|コマンド履歴検索|
|Ctrl|||l|画面クリア|
|Ctrl|Shift||f|検索|
|Ctrl|||c|実行中プログラム強制終了|
|Ctrl|||d|終了|
|Ctrl|||f/b|カーソル移動(1個右/左)|
|||Alt|f/b|カーソル移動(単語単位右/左)|
|Ctrl|||a/e|カーソル移動(行頭/行末)|
|Ctrl|||t|文字入替(現在⇔1つ前)|
|Ctrl|||h|文字削除(カーソル左)|
|Ctrl|||d|文字削除(カーソル位置)|
|Ctrl|||w|単語削除(カーソル左)|
|||Alt|d|単語削除(カーソル右)|
|Ctrl|||u/k|文字削除(カーソル左側/右側全て)|
|Ctrl|||y|貼付け（上記Ctrl + w,Ctrl + kなどで削除した文字列をペーストできる）|
|Ctrl|||m/j/o|ENTERと同じ|
||Shift|Alt|+/-|画面分割(垂直/水平)|
|||Alt|方向キー|分割画面移動|
||Shift|Alt|方向キー|分割画面サイズ変更|
|||Alt|Enter|全画面モード|
||||F11|全画面モード|
|Ctrl|||s/q|画面更新 停止/再開|
|Ctrl|Shift||d|タブ複製|
|Ctrl|||Tab|タブ切替え|
|Ctrl|Shift||t|新規タブ作成|
|Ctrl|Shift||p|コマンドパレット表示|
|Ctrl|Shift||Space|ドロップダウンメニュー表示|

[トップに戻る](../index.md)
