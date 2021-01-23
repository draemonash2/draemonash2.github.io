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

- 入力補助
	- 【コマンド/ファイル名補完】Tab
	- 【1つ前コマンド履歴】Ctrl + p
	- 【1つ先コマンド履歴】Ctrl + n
	- 【コマンド履歴検索】Ctrl + r
	- 【文字入替(現在⇔1つ前)】Ctrl + t
	- 【文字削除(カーソル左)】Ctrl + h
	- 【文字削除(カーソル位置)】Ctrl + d
	- 【単語削除(カーソル左)】Ctrl + w
	- 【単語削除(カーソル右)】Alt + d
	- 【文字削除(カーソル左側全て)】Ctrl + u
	- 【文字削除(カーソル右側全て)】Ctrl + k
	- 【貼付け（上記Ctrl + w,Ctrl + kなどで削除した文字列をペーストできる）】Ctrl + y
	- 【ENTERと同じ】Ctrl + m
	- 【ENTERと同じ】Ctrl + j
	- 【ENTERと同じ】Ctrl + o
- 移動
	- 【カーソル移動(1個右)】Ctrl + f
	- 【カーソル移動(1個左)】Ctrl + b
	- 【カーソル移動(単語単位右)】Alt + f
	- 【カーソル移動(単語単位左)】Alt + b
	- 【カーソル移動(行頭)】Ctrl + a
	- 【カーソル移動(行末)】Ctrl + e
- 画面操作
	- 【画面水平(分割)】Alt + Shift + -
	- 【画面分割(垂直)】Alt + Shift + +
	- 【分割画面間 移動】Alt + ←↑→↓
	- 【分割画面サイズ変更】Alt + Shift + ←↑→↓
	- 【全画面モード】Alt + Enter or F11
	- 【画面更新 停止】Ctrl + s
	- 【画面更新 再開】Ctrl + q
	- 【タブ複製】Ctrl + Shift + D
	- 【タブ切替え】Ctrl + Tab
	- 【新規タブ作成】Ctrl + Shift + T
- 他
	- 【コマンドパレット表示】Ctrl + Shift + P
	- 【画面クリア】Ctrl + l
	- 【実行中プログラム強制終了】Ctrl + c
	- 【終了】Ctrl + d
	- 【ドロップダウンメニュー表示】Ctrl + Shift + Space
	- 【検索】Ctrl + Shift + F

[トップに戻る](../index.md)
