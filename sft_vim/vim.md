[トップに戻る](../index.md)

# インストール手順

- Vim Kaoriya ダウンロード
- Vim 設定ファイルダウンロード
- Git インストール (コマンドプロンプトにて git clone が実行できる状態にしておく)
- コマンドプロンプトにて、下記コマンドを実行
	- cd ★VIM インストールフォルダ★
	- git clone https://github.com/Shougo/neobundle.vim bundle/neobundle.vim
- vimを起動し、下記コマンドを実行
	-:NeoBundleInstall

# 設定

- 起動オプション
	- ウィンドウ１つで起動
		`--remote-tab-silent`
	- 行番号指定
		- `C:\prg_exe\Vim\gvim.exe C:\codes\_update_codes.vbs +5`

# ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||Shift||[/]|移動 前/次の空行|
||||gv|再度同じ範囲を選択|
||||ge|前単語の末尾へ移動|
||||<C-r> /|最後に検索に使用したワード検索|
||||v ⇒ o |選択範囲の末尾にカーソルを移動|
||||挿入モード⇒<C-r>=0xFFFF|簡易16⇒10進数変換（例では65535）|
||||/\V |テキストで検索|
||Shift||h/m/l|カーソル移動 画面 最上行/中央/最下行|
||||+/-|先頭に移動 次行/前行|
|Ctrl|||f/b|移動 1画面分 上/下|
|Ctrl|||u/d|移動 半画面分 上/下|

# コマンド

| 機能 | コマンド | 説明 |
|:---|:---|:---|
|共通		| :args AAA.txt BBB.txt CCC.txt							| argsコマンドで一度に複数のファイルを開く |
|共通		| :w %<													| 現在開いているバッファ名 (拡張子を除いたもの) 取り出し(:w hoge と同等) |
|共通		| :e #N  (Nは任意の数字)								| #N は、そのN番目のバッファの名前と同じ値になる |
|共通		| q:													| コマンド履歴を表示（ Ctrl+C でカーソル位置のコマンドをコマンドウィンドウに転送） |
|共通		| %!xxd -g 1											| バイナリモードに変更 |
|共通		| :set ic												| 検索・置換時、大文字小文字の区別を有効 |
|共通		| :set noic												| 検索・置換時、大文字小文字の区別を無効 |
|共通		| :set ★?												| 現在の値を表示 ex) set number? |
|共通		| :set ★&												| デフォルト値に戻す ex) set number& |
|共通		| :set ★!												| On/Offのトグル  ex) set number! |
|共通		| :b0, :b1, ...											| バッファ0,1,..に移動 |
|共通		| :buffers												| 編集中のバッファ一覧を表示 |
|共通		| :Sex													| ウインドウを分割してファイルエクスプローラを開く |
|共通		| :ls													| バッファのリストを表示 |
|共通		| mx													| マークをつける(x:a～z) |
|共通		| :vertical diffsplit <filepath>						| [カレントバッファと指定ファイルの差分をとる](https://nanasi.jp/articles/howto/diff/diff_text.html) |
|共通		| :windo diffthis										| [開いている2バッファ同士の差分をとる](https://qiita.com/isseium/items/36b54171c430f381e232) |
|共通		| :set scrollbind										| [分割したバッファのスクロール同期](https://qiita.com/murayama/items/497b275b31a378921f6a) |
|共通		| :set noscrollbind										| [分割したバッファのスクロール同期を解除](https://qiita.com/murayama/items/497b275b31a378921f6a) |
|共通		| 入力モードで <c-x><c-k>								| 辞書ファイルから単語補完 |
|共通		| ``													| 直前のマークに移動 |
|共通		| :%s/\v\_(.)/\u\1/g									| スネークケース→キャメルケース変換 |
|共通		| :%s/\v([A-Z])/\_\L\1/g								| キャメルケース→スネークケース変換 |
|共通		| ;mes													| エラーメッセージがすぐ消える場合、エラー表示させる |
|共通		| コマンド\|コマンド									| コマンド連続実行 |
|共通		| :redir end											| コマンドリダイレクト 終了 |
|共通		| :redir > file											| コマンドリダイレクト 開始 |
|共通		| :set ff=dos											| 改行コード 書換(\*1) (dos/mac/unix)|
|共通		| :set ffs=unix,dos,mac									| 改行コード 表示方法変更（閲覧時の自動判別用）br()→カンマで区切って優先度の高い順に指定 |
|共通		| :e ++ff=dos											| 改行コード 表示方法変更（自動判別失敗時の読み直し用）(dos/mac/unix) |
|共通		| :set enc=utf-8										| 文字コード 書換（to VIM）(\*2) (euc-jp/shift\_jis/utf-8/..) |
|共通		| :set fenc=utf-8										| 文字コード 書換（to 現在バッファ）(\*2) (euc-jp/shift\_jis/utf-8/..) |
|共通		| :set fencs=euc-jp,shift\_jis,utf-8					| 文字コード 表示方法変更（閲覧時の自動判別用）br()→カンマで区切って優先度の高い順に指定 |
|共通		| :e ++enc=utf-8										| 文字コード 表示方法変更（自動判別失敗時の読み直し用） (euc-jp/shift\_jis/utf-8/..) |
|Grep		| :vim {pattern} %\|cw									| vimgrepを実行&br()ex.vimgrep /hogehoge/j c:/test/\*\*/\*.txt\|cw |
|Grep		| :bufdo vimgrepa {pattern} %\|cw						| バッファすべてに vimgrep &br()（★貼り付け時は「｜」を半角に★） |
|Grep		| :RGrep 文字列 C:\00\_work\trunk\C\jsp-1.4.4-full\*.c	| 特定のフォルダ配下のCファイルを再帰検索 |
|Align		| :Align ,（範囲選択後）								| インデント調整(","のほかには"=" "+" "-"がある)(\*3) |
|Align		| \abox（範囲選択後）									| ボックスコメント設定(\*4) |
|DrawIt!	| \di（範囲選択後）										| 描画モード開始 |
|DrawIt!	| \ds（範囲選択後）										| 描画モード終了 |
|DrawIt!	| \b （範囲選択後）										| 四角形ボックス描画 |
|DrawIt!	| \e （範囲選択後）										| ひし形ボックス描画 |
|DrawIt!	| v  （範囲選択後）										| v描画 |
|DrawIt!	| ^  （範囲選択後）										| ^描画 |
|DrawIt!	| >  （範囲選択後）										| >描画 |
|DrawIt!	| <  （範囲選択後）										| <描画 |
|surround	| S'													| ビジュアルモードで選択した部分を ' で囲む |
|surround	| yss'													| 行全体を ' で囲む |
|neosnippet	| :NeoSnippetEdit										| スニペットを編集 |

- (\*1) set ff コマンド
	- 「set ff=●」 は "UNIXの改行コード" から "●" の改行コードに変換するもの	
	- 「VIM 下部の"CR/LF=▲"表示」は、現在のファイルを「改行コード：▲」として表示するもの ⇒「set ff=●」をしたからといって、「VIM 下部の"CR/LF=▲"表示」が変わる訳ではない！
		![Vimのsetffコマンドについて](Vimのsetffコマンドについて.jpg)
- (\*2) enc と fenc コマンド
	- 'fileencoding' と 'encoding' が異なるとき、ファイルの書き出しの際に文字エンコーディングの変換が行われる。
	'fileencoding' が空の場合、'encoding' と同じ値が使われる (ファイルの読
	み書きの際に変換をしない)。
- (\*3) Align コマンド挙動（:Align , = + -）
	![Align](Align.jpg)
- (\*4) 範囲選択後、 \abox を実行
	![Align\_BoxComment](Align_BoxComment.jpg)
- 文字数を維持しながら置換するVimコマンド
	- 添付の「文字数を維持しながら置換するVimコマンドを作成する.xlsm」参照

# Tips
## 突然エラーが出るようになった
原因：設定ファイルが小文字になっている！

## 検索/置換について
- 概要
	- 単語単位検索：/\<the\>
	- ４桁数値検索：/\<\d\d\d\d\>
	- 大/小文字無視（デフォルト）：%s/★/●/i
	- 大/小文字無視しない：%s/★/●/I
	- 置換時のエラーを無視する：%s/★/●/e
	- 全単語の先頭大文字化：%s/\<./\u&/g
	- 全単語の先頭小文字化：%s/\<./\l&/g
	- "/"ではなく"/\v"を使うことで、正規表現時のわずらわしいエスケープを抑制することができる。(very magic指定)
		- 正規表現( verymagic 指定)
			- magic / very magic / no magic / very nomagic の比較
				- \m（magic）（デフォルト）
					- パターンの中でリテラルとして扱われる文字は、テキストの同じ文字とマッチします。しかし、バックスラッシュが前置されると、特別な意味を持つようになります。
				- \M（nomagic）
					- ★
				- \v（very magic）
					- それ以降の、'0'-'9'、'a'-'z'、'A'-'Z'、'_'、以外のすべての ASCII 文字は特別な意味を持ちます。
				- \V（very nomagic）
					- それ以降はバックスラッシュと終端文字 (/ や ?) だけが特別な意味を持ちます。
- 検索単語の置換方法
	- 置換したい単語を以下のいずれかの方法で検索
		- 「\*」を使用してカーソル下の単語を検索
		- 「/」による検索
	- コマンドモードに入り, %s//<置換文字列\>/g を実行（検索単語を省略できる）
- 複数行の置換
	- %s/\vRunnable Entity (\w\*)\n.\*\nTriggerd on (\w\*)msec/\1\t\2/g
		![複数行の置換](複数行の置換.jpg)
- global コマンドを用いた置換方法
	- :g/Second/s/Bar/Foo/g
	- ⇒ 末尾に「Second」が含まれる行の「Bar」を「Foo」に変える
		- 【参考】global コマンド の使い方 簡易版
			- g[lobal]/{pattern}/[cmd]
			- ⇒ {pattern}にマッチする行に対して、Exコマンド[cmd](省略した場合 ":p")を実行する。
		- 【置換結果】
			``` c 
			FooBarBazHogeBarFugaPiyoFirst
			FooBarBazHogeBarFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoFirst
			FooBarBazHogeBarFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoThird
			FooBarBazHogeBarFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoFirst
			FooBarBazHogeBarFugaPiyoThird
			↓
			FooBarBazHogeBarFugaPiyoFirst
			FooFooBazHogeFooFugaPiyoSecond
			FooFooBazHogeFooFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoFirst
			FooFooBazHogeFooFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoThird
			FooFooBazHogeFooFugaPiyoSecond
			FooBarBazHogeBarFugaPiyoFirst
			FooBarBazHogeBarFugaPiyoThird
			```
- 正規表現の先読み/後読み

| 手法          | 構文 | 使用例              | 説明                                    |
|:---|:---|:---|:---|
| 肯定先読み	| @=   | kimura( takuya)@=   | 後に" takuya"が含まれる"kimura"を検索   |
| 否定先読み	| @!   | kimura( takuya)@!   | 後に" takuya"が含まれない"kimura"を検索 |
| 肯定後読み	| @<=  | (inagaki )@<=goro   | 前に"inagaki "が含まれる"goro"を検索    |
| 否定後読み	| @<\!  | (inagaki )@<\!goro | 前に"inagaki "が含まれない"goro"を検索  |

# スニペット
- [neosnippet使い方](http://d.hatena.ne.jp/adragoona/touch/20130929/1380437722)

[トップに戻る](../index.md)
