
# X-Finder

[トップに戻る](../index.md)

## 設定方法

- 設定については、[こちら](http://www.eonet.ne.jp/~gakana/xf.html)参照

## インストールアドイン

- [FFXII.exe](http://www.eonet.ne.jp/~gakana/download/ffxii.html)

## Tips

- 複数ファイルフィルタ

    ```text
    \*aaa.txt\*;\*bbb.txt\*;\*ccc.txt\*
    ```

- vbs 呼び出しテンプレート

    ```vb
    Script:VBScript
    Option Explicit
    Const EXECUTION_MODE = 1
    WScript.Include( "C:\codes\vbs\tools\win\file_ope\CreateSymbolicLink.vbs" )
    ```

## ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||\|ルートに移動|
||||/|すべての選択を解除|
||||\*|すべての選択を反転|
||||@|アドレスバーに移動|
||||’|アドレスバーに移動|
||||,|インクリメンタル サーチ|
||||.|拡張子のインクリメンタル サーチ|
||||-|フォルダの表示設定を保存|
||||=|ウインドウサイズを揃える|
||||?|他のウインドウとの入れ替え|
||||+|ポップアップメニュー1|
||||;|ポップアップメニュー2|
||||:|ドライブリスト|
||||<|分割の切り替え|
||||>|分割画面の切り替え|
||||Space|フォーカスしたアイテムの選択を反転して次のアイテムにフォーカスを移動|
||||BackSpace|一つ上の階層に移動|
||||→/←/↑/↓|右/左/上/下に移動|
|||Alt|←|戻る|
|||Alt|↑|他のウインドウのパス一覧|
|||Alt|↓|タブの履歴|
|Ctrl|||←|左のタブに移動|
|Ctrl|||→|右のタブに移動|
|Ctrl|Shift||Tab|左のタブに移動|
|Ctrl|||Tab|右のタブに移動|
|Ctrl|||↑|タブ メニュー|
|Ctrl|||↓|タブの一覧|
|Ctrl|Shift||←/→|タブを左/右に移動|
||Shift|Alt|←/→|タブを左/右に移動|
|Ctrl|Shift||↑/↓|ツールフォルダの場合は項目を上/下に移動|
|Ctrl|Shift||Space|ナビゲートロックの切り替え|
||Shift||Esc|別ウインドウを開く|
||||Ins|パスの抽出|
|Ctrl|Shift||Ins|最近閉じたタブの一覧|

## shell

| 名前 | 説明 | パス |
|:---|:---|:---|
| shell:DesktopFolder | デスクトップ |  |
| shell:DriveFolder | PC |  |
| shell:ControlPanelFolder | コントロールパネル |  |
| shell:RecycleBinFolder | ゴミ箱 |  |
| shell:SendTo | 送るフォルダ | %USERPROFILE%\AppData\Roaming\Microsoft\Windows\SendTo |
| shell:StartUp | スタートアップ | %USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\StartUp |
| shell:Personal |  |  |

## トラブルシューティング

- TortoiseGitのコンテキストメニューが表示されない
    - 解決方法：[TortoiseGit の設定でエクスプローラー以外のソフトにもコンテキストメニューを表示できるように設定する。](https://www.5cho-me.com/archives/143620)
        1. エクスプローラー上で、任意のファイルを選択して右クリック
        1. TortoiseGit -> 設定(S) をクリック
        1. 左側「アイコンオーバーレイ」を選択し、「エクスプローラー上でのみオーバーレイとコンテキストメニューを表示(O)」にチェックを入れる

[トップに戻る](../index.md)
