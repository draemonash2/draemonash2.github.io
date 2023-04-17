[トップに戻る](../index.md)

# 関連リンク

- [Linux](../linux_sft/linux.md)
- [Raspberry Pi](../raspberrypi_sft/raspberrypi.md)

# インストール方法

- Microsoft Storeより「Windows Subsystem for Linux」をインストールする。
	- 2023/4現在、コンポーネント版とMicrosoft Store版が存在するが、後者に一本化される見込み。[[1]](https://ascii.jp/elem/000/004/120/4120511/)

# Tips

- WSL2 起動方法＠WSL2コンソール
	1. Windows にて「wsl」を検索して起動する
- WSL2 起動方法＠Windows Terminal
	1. Windows Terminal タイトルバーの下矢印をクリック
	1. 起動したいLinuxディストリビューションを選択
- [Windows Terminalからのデフォルト起動をWSL2に変更する方法](https://www.asobou.co.jp/blog/web/windows-terminal#3_Windows_TerminalWSL2)
	1. Windows Terminal にて「Ctrl + ,」押下
	1. 開いた設定ファイル(settings.json)内の「defaultProfile」を起動したいLinuxディストリビューションのGUIDに変更する
- [ディストリビューションのアップデート方法](https://qiita.com/matarillo/items/98d7452967987fe5d633)
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
- [Linux⇔Windows間のファイルアクセス方法](https://qiita.com/Uchitaso/items/6e0a7859e87bb8bdb527)
	- Windows上でLinuxのファイルにアクセス
		- エクスプローラからアドレス「\\wsl$」にアクセスする
	- Linux上でWindowsのファイルにアクセス
		- 「/mnt/」にアクセスする
- [ワンアクションで WSL2 を管理者権限起動する](https://www.xenos.jp/~zen/blog2/index.php/2020/05/31/post-3944/)
	1. 以下のバッチファイルを作成する。
		- `powershell start-process wt -verb runas`
	1. 上記バッチファイルのショートカットファイルを作成する
	1. 上記ショートカットファイルを管理者権限で実行するように変更する
- Windows Terminal 設定ファイル（settings.json）格納先
	- `%USERPROFILE%\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`
- 特定ディレクトリを垂直分割して Windows Terminal を起動する
	- `wt -d C:\codes_sample\c++\dokusyuC++; split-pane -V -D wsl.exe`
- OS間のシンボリックリンク挙動
	- linux(wsl2)上でシンボリックリンクを作るとwindows上で使える？
		- 使えない(0kbの不明なファイルが作られる)
	- windows上でシンボリックリンクを作るとlinux(wsl2)上で使える？
		- 問題なく使える
- [“ストア”にある3つの「Ubuntu」](https://forest.watch.impress.co.jp/docs/serial/yajiuma/1134055.html)
	- 「Ubuntu」：現行の「Ubuntu LTS」。新しいバージョンがでるたびに更新される。
	- 「Ubuntu 16.04」：2021年まで利用可能なLTS版
	- 「Ubuntu 18.04」：2023年まで利用可能なLTS版

# コマンド

- [こちら](../linux_sft/linux.md)

# ショートカットキー

- [こちら](../linux_sft/linux.md)

[トップに戻る](../index.md)
