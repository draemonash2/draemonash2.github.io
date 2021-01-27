[トップに戻る](../index.md)

# 関連リンク

- [Linux](https://github.com/draemonash2/wiki/blob/master/sft_linux/linux.md)
- [Raspberry Pi](https://github.com/draemonash2/wiki/blob/master/sft_raspberrypi/raspberrypi.md)

# Tips

- WSL2 起動方法＠WSL2コンソール
	1. Windows にて「wsl」を検索して起動する
- WSL2 起動方法＠Windows Terminal
	1. Windows Terminal タイトルバーの下矢印をクリック
	1. 起動したいLinuxディストリビューションを選択
- [Windows Terminalからのデフォルト起動をWSL2に変更する方法](https://www.asobou.co.jp/blog/web/windows-terminal#3_Windows_TerminalWSL2)
	1. Windows Terminal にて「Ctrl + ,」押下
	1. 開いた設定ファイル(settings.json)内の「defaultProfile」を起動したいLinuxディストリビューションのGUIDに変更する
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
- [起動時「~/.bashrc」が読み込まれない](https://qiita.com/ozroro/items/0baac26be01ee5ab41d6)
	1. Windows Terminal の設定を開く（Ctrl + ,押下）
	1. "profiles" → name:"Ubuntu" に以下を追加する
		- `"commandline": "wsl -d Ubuntu bash"`

# コマンド
## Linux 共通コマンド

- [Linuxの基本コマンドはこちら](https://github.com/draemonash2/wiki/blob/master/sft_linux/linux.md)

## WSL2 関連コマンド

- VIM設定ファイル
	- ★

# ショートカットキー

- [こちら](https://github.com/draemonash2/wiki/blob/master/sft_linux/linux.md)

[トップに戻る](../index.md)
