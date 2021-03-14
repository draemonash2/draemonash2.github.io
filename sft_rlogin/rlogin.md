[トップに戻る](../index.md)

# 設定

- [フォントサイズ変更](https://qiita.com/haya2_/items/c50028594bff118e82b6)
	1. [表示]→[オプション設定]→[スクリーン]
	1. [フォントサイズから一行あたりの文字数を決定]にフォントサイズを入力
- [範囲指定でクリップボードコピー](https://sig9.hatenablog.com/entry/2020/09/02/000000)
	1. [設定] → [クリップボード]
	1. [左クリックの範囲指定だけでクリップボードにコピーする] にチェック

# Tips

- [RLogin.iniの注意点](https://tsukaman.hateblo.jp/entry/2017/12/06/130744)
	- RLogin.iniを使用すればレジストリではなくこのiniファイルに保存される。
	- ただし、複数のプロセスからの変更などに弱い。また、ファイルベースで意図せぬハングアップやファイルのコピーなどで壊れる場合がありレジストリベースよりリスクが高い。
- [チャットスクリプト保存](http://nanno.dip.jp/softlib/man/rlogin/faq.html)
	- ★
	- チャットスクリプトのサンプルは[こちら](https://qiita.com/pocket8137/items/23b978f802c4ca6bed72)
- [リモートのVimからssh越しにクリップボード書き込み](http://tateren.hateblo.jp/entry/2017/07/21/213020)

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
|Ctrl|||</>|カーソル移動(一文字) 左(\033\[D)/右(\033\[C)|
|Ctrl|Shift||</>|カーソル移動(単語) 左(\033\[1;5D)/右(\033\[1;5C)|
|||Alt|o|オプション設定($OPTION\_SET)|
|Ctrl|||s|全状態保存($FILE\_ALLSAVE)|

[トップに戻る](../index.md)
