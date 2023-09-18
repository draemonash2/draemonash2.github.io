
# WinSCP

[トップに戻る](../index.md)


## コマンド

- 【接続（パスワード方式）】 `winscp.exe sftp://<user>:<password>@<address>:<port>`
- 【接続（公開鍵暗号方式）】 `winscp.exe sftp://<user>@<address>:<port> /privatekey=<ppk_file_path>`
- 【ファイル転送(remote→local)】 `winscp.exe /console /command "option batch on" "open user:password@example.com" "get examplefile.txt d:\" "exit"`
- 【ファイル転送(local→remote)】 `winscp.exe /console /command "option batch on" "open user:password@example.com" "cd ~" "put c:\test\examplefile.txt" "exit"`
    - ディレクトリ名も転送可能

## トラブルシューティング

- 公開鍵暗号方式によるWinSCP接続時、エラー「OpenSSH形式ではなくPuTTy形式の秘密鍵にしてね」が発生
    - 解決方法：[WinSCP 付属のPuTTYgenで秘密鍵をPuTTy形式の秘密鍵に変換する](https://www.codelab.jp/blog/?p=350)
        1. puttygen(WinSCPに同梱されています）を起動
        2. File->Load private key で変換したい秘密鍵を読み込み
        3. ウィンドウ上のsave private keyで保存
- 公開鍵暗号方式によるWinSCP接続時、「PuTTY key format too new」が発生
    解決方法：[PuTTYgenの設定で「PPK file version」を"2"に変更する](https://ccportal.ims.ac.jp/node/2913)

## ショートカットキー

### エクスプローラー風ショートカット

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||F5|更新|
|||Alt|←/→/↑|ディレクトリ移動(戻る/進む/親)|
|Ctrl|||\|ディレクトリ移動(ルート)|
|Ctrl|||h|ディレクトリ移動(ホーム)|
|Ctrl|||b|ブックマーク追加|
|Ctrl|||o|ブックマークウィンドウ表示|
|Ctrl||Alt|t|ツリー・パネル切替え|
|Ctrl||Alt|f|フィルタ|
||||F7|フォルダ作成|
||Shift||F4|ファイル作成|
|||Alt|F6|ショートカットファイル作成|
|Ctrl|Shift||c|ファイル名コピー|
|Ctrl|||[|フォルダパスコピー(ローカルパネル)|
|Ctrl|||]|フォルダパスコピー(リモートパネル)|
|Ctrl||Alt|c|ファイルパスコピー|
|Ctrl||Alt|h|隠しファイル表示/非表示切替え|
|Ctrl||Alt|t|ツリーパネル表示/非表示切替え|
|Ctrl|||F3|ソート(名前)|
|Ctrl||Alt|e|エクスプローラで開く(ローカルパネルのみ)|

[トップに戻る](../index.md)
