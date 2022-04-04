[トップに戻る](../index.md)

# おススメ設定

- [フォントサイズ変更](https://qiita.com/haya2_/items/c50028594bff118e82b6)
	1. [表示] > [オプション設定] > [スクリーン]
	1. [フォントサイズから一行あたりの文字数を決定]にフォントサイズを入力
- [範囲指定でクリップボードコピー](https://sig9.hatenablog.com/entry/2020/09/02/000000)
	1. [設定] > [クリップボード]
	1. [左クリックの範囲指定だけでクリップボードにコピーする] にチェックを入れる
	1. [右クリックでペースト] にチェックを入れる
- [標準のサーバ設定を追加](https://dexlab.net/pukiwiki/index.php?Memo/Rlogin)
	1. サーバに接続 > 標準にしたいサーバを選択 > 右クリック > 標準の設定にする
	1. 他のサーバに標準の設定を適用する
		1. サーバに接続 > 表示 > 標準の設定に戻す
- 背景に接続先を設定
	1. [設定] > [背景設定] > [バックグラウンド画像にテキストを追加]にチェックを入れる
- マウスホイールのヌルヌル動作を無効にする
	1. [設定] > [マウス関連] > [マウスホイールのヌルヌル動作を無効にする]にチェックを入れる
- 画面サイズ変更時にサイズを表示しない
	1. [設定] > [拡張機能] > [サイズを表示しない]にチェックを入れる
- [チャットスクリプト保存](http://nanno.dip.jp/softlib/man/rlogin/faq.html)
	- 手順
		1. [設定] > [サーバー] > [チャットスクリプト(C)]
		1. [次回接続時にChatScriptを自動で作成する]にチェック
	- チャットスクリプトのサンプルは[こちら](https://qiita.com/pocket8137/items/23b978f802c4ca6bed72)
- [リモートのVimからssh越しにクリップボード書き込み](http://tateren.hateblo.jp/entry/2017/07/21/213020)
- [RLogin.ini](https://tsukaman.hateblo.jp/entry/2017/12/06/130744)
	- RLogin.iniを使用すればレジストリではなくこのiniファイルに保存される。
	- ただし、複数のプロセスからの変更などに弱い。また、ファイルベースで意図せぬハングアップやファイルのコピーなどで壊れる場合がありレジストリベースよりリスクが高い。
- [ファンクションキー キーコード一覧](https://qiita.com/thino-rma/items/c11420a189ee48204019)
- WSLにSSH接続する
	- [参考URL1](https://qiita.com/kenchan1193/items/896c416a4ee89cd4f95b)
	- [参考URL2](https://qiita.com/ezmscrap/items/30eaf9531e240c992cf1)

# ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
|Ctrl|||ドラッグ|矩形選択|
||Shift||ドラッグ|行選択|
|Ctrl|Shift||f|検索($SEARCH\_REG)|
|Ctrl|Shift||v|貼り付け($CLIPBOARD)|
||||F10|SFTPダイアログを開く($VIEW\_SFTP)|
||Shift|Alt|←|接続追加(複製)＋同ペイン($SPLIT\_OVER)|
||Shift|Alt|↓/→|接続追加(複製)＋縦($SPLIT\_HEIGHT)/横分割($SPLIT\_WIDTH)|
|Ctrl||Alt|↓/→|接続追加(新規)＋縦($SPLIT\_HEIGHTNEW)/横分割($SPLIT\_WIDTHNEW)|
|Ctrl||Alt|↑|ペイン移動($PANE\_ROTATION)|
|Ctrl|/Shift||tab|ペインフォーカス移動(次/前)|
||||F11|ウィンドウ整理(並べて表示($PANE\_TILEHORZ))|
||||F12|ウィンドウ整理(重ねて表示($PANE\_CASCADE)|
|Ctrl||Alt|w|分割を閉じる($PANE\_DELETE)|
|||Alt|n/w|接続開く($FILE\_NEW)/閉じる($FILE\_CLOSE)|
|Ctrl|||,/.|カーソル移動(一文字) 左(\033\[D)/右(\033\[C)|
|Ctrl|Shift||,/.|カーソル移動(単語) 左(\033b)/右(\033f)|
|Ctrl||Alt|,/.|カーソル移動 行頭(\001)/行末(\005)|
|||Alt|o|オプション設定($OPTION\_SET)|
|Ctrl|||s|全状態保存($FILE\_ALLSAVE)|
|Ctrl|||h/d|文字削除 カーソル左/右|
|Ctrl|||l|文字削除 カーソル右(\004)|
|Ctrl|Shift||h/d|文字削除 単語左(\027)/単語右(\033d)|

[トップに戻る](../index.md)
