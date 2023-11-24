
# Windows Terminal

[トップに戻る](../index.md)

# Tips

- WSL2 起動方法＠Windows Terminal
    1. Windows Terminal タイトルバーの下矢印をクリック
    1. 起動したいLinuxディストリビューションを選択
- [Windows Terminalからのデフォルト起動をWSL2に変更する方法](https://www.asobou.co.jp/blog/web/windows-terminal#3_Windows_TerminalWSL2)
    1. Windows Terminal にて「Ctrl + ,」押下
    1. 開いた設定ファイル(settings.json)内の「defaultProfile」を起動したいLinuxディストリビューションのGUIDに変更する
- [起動時「~/.bashrc」が読み込まれない](https://qiita.com/ozroro/items/0baac26be01ee5ab41d6)
    1. Windows Terminal の設定を開く（Ctrl + ,押下）
    1. "profiles" → name:"Ubuntu" に以下を追加する
        - `"commandline": "wsl -d Ubuntu bash"`
- Windows Terminal 設定ファイル（settings.json）格納先
    - `%USERPROFILE%\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json`
- 特定ディレクトリを垂直分割して Windows Terminal を起動する
    - `wt -d C:\codes_sample\c++\dokusyuC++; split-pane -V -D wsl.exe`

[トップに戻る](../index.md)
