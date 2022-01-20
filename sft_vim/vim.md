[トップに戻る](../index.md)

# インストール手順

1. Vim Kaoriya ダウンロード
1. Vim 設定ファイルダウンロード
1. Git インストール (コマンドプロンプトにて git clone が実行できる状態にしておく)
1. コマンドプロンプトにて、下記コマンドを実行
	1. cd ★VIM インストールフォルダ★
	1. git clone https://github.com/VundleVim/Vundle.vim.git bundle/Vundle.vim
1. 「\_vimrc」(もしくは.vimrc)に以下の行を追加する

```
set nocompatible
filetype off
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()

Plugin 'VundleVim/Vundle.vim'

" 導入したいプラグインを以下に列挙
" Plugin '[Github Author]/[Github repo]' の形式で記入
Plugin 'airblade/vim-gitgutter'

call vundle#end()
filetype plugin indent on

"　その他のカスタム設定を以下に書く
```

- vimを起動し、下記コマンドを実行
	- :PluginInstall

# 設定

- 起動オプション
	- ウィンドウ１つで起動
		`--remote-tab-silent`
	- 行番号指定
		- `C:\prg_exe\Vim\gvim.exe C:\codes\_update_codes.vbs +5`
- [リモートのVimからssh越しにクリップボード書き込み](http://tateren.hateblo.jp/entry/2017/07/21/213020)
- [プラグインサイト VimAwesome](https://vimawesome.com/)

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
|共通			| vim -O file1 file2									| 垂直分割起動 |
|共通			| vim -o file1 file2									| 水平分割起動 |
|共通			| vimdiff file1 file2									| vim で diff |
|共通			| :args AAA.txt BBB.txt CCC.txt							| argsコマンドで一度に複数のファイルを開く |
|共通			| :w %<													| 現在開いているバッファ名 (拡張子を除いたもの) 取り出し(:w hoge と同等) |
|共通			| :e #N  (Nは任意の数字)								| #N は、そのN番目のバッファの名前と同じ値になる |
|共通			| q:													| コマンド履歴を表示（ Ctrl+C でカーソル位置のコマンドをコマンドウィンドウに転送） |
|共通			| q/													| 検索履歴を表示（ Ctrl+C でカーソル位置のコマンドをコマンドウィンドウに転送） |
|共通			| %!xxd -g 1											| バイナリモードに変更 |
|共通			| :set ic												| 検索・置換時、大文字小文字の区別を有効 |
|共通			| :set noic												| 検索・置換時、大文字小文字の区別を無効 |
|共通			| :set ★?												| 現在の値を表示 ex) set number? |
|共通			| :set ★&												| デフォルト値に戻す ex) set number& |
|共通			| :set ★!												| On/Offのトグル  ex) set number! |
|共通			| 入力モードで <c-x><c-k>								| 辞書ファイルから単語補完 |
|共通			| ;mes													| エラーメッセージがすぐ消える場合、エラー表示させる |
|共通			| :reg													| レジスタ一覧表示 |
|共通			| gv													| 直前選択範囲の再選択 |
|共通			| /\c													| 一時的に大/小文字無視検索 |
|共通			| /\C													| 一時的に大/小文字区別検索 |
|共通			| :windo set scb										| 同時スクロール |
|共通(edit)		| :%s/\v\_(.)/\u\1/g									| スネークケース→キャメルケース変換 |
|共通(edit)		| :%s/\v([A-Z])/\_\L\1/g								| キャメルケース→スネークケース変換 |
|共通(edit)		| "[a-z\*+-]p または Ctrl-r[a-z\*+-]					| 指定したレジスタの内容をペースト |
|共通(edit)		| :ls													| バッファのリストを表示 |
|共通(edit)		| Ctrl + a												| 数字インクリメント |
|共通(edit)		| Ctrl + x												| 数字デクリメント |
|共通(jumpl)	| :ju													| ジャンプリストを表示する |
|共通(jumpl)	| :cle													| ジャンプリストを空にする |
|共通(mark)		| :marks												| マーク一覧表示 |
|共通(mark)		| m[a-zA-Z]												| マーク追加(カーソル位置) |
|共通(mark)		| ``													| マーク移動(to直前マーク) |
|共通(mark)		| C-o													| マーク移動(to古いマーク) |
|共通(mark)		| C-i													| マーク移動(to新規マーク) |
|共通(mark)		| `[a-zA-Z]												| マーク移動(to指定マーク) |
|共通(mark)		| '[a-zA-Z]												| マーク移動(to指定マーク行頭) |
|共通(mark)		| :delm [a-zA-Z]										| マーク削除 |
|共通(mark)		| :delm!												| マーク一括削除 |
|共通(fold)		| zi													| 折りたたみの有効無効の切り替え |
|共通(fold)		| zf													| 折りたたみの作成(範囲選択の開始行と終了行の末尾にマーカーを追加する) |
|共通(fold)		| za													| 折りたたみの開閉 |
|共通(fold)		| zA													| 折りたたみの再帰的開閉 |
|共通(fold)		| zd													| 折りたたみの削除 |
|共通(fold)		| zE													| 全折りたたみ削除 |
|共通(fold)		| zR													| 全折りたたみ開く |
|共通(fold)		| zM													| 全折りたたみ閉じる |
|共通(win)		| :b0, :b1, ...											| バッファ0,1,..に移動 |
|共通(win)		| :buffers												| 編集中のバッファ一覧を表示 |
|共通(win)		| :Sex													| ウインドウを分割してファイルエクスプローラを開く |
|共通(win)		| :vertical diffsplit <filepath>						| [カレントバッファと指定ファイルの差分をとる](https://nanasi.jp/articles/howto/diff/diff_text.html) |
|共通(win)		| :windo diffthis										| [開いている2バッファ同士の差分をとる](https://qiita.com/isseium/items/36b54171c430f381e232) |
|共通(win)		| :set scrollbind										| [分割したバッファのスクロール同期](https://qiita.com/murayama/items/497b275b31a378921f6a) |
|共通(win)		| :set noscrollbind										| [分割したバッファのスクロール同期を解除](https://qiita.com/murayama/items/497b275b31a378921f6a) |
|共通(win)		| Ctrl+w → w											| 画面移動 |
|共通(win)		| Ctrl+w → p											| 画面移動 |
|共通(win)		| Ctrl+w → k											| 画面移動(上) |
|共通(win)		| Ctrl+w → j											| 画面移動(下) |
|共通(win)		| Ctrl+w → l											| 画面移動(右) |
|共通(win)		| Ctrl+w → h											| 画面移動(左) |
|共通(win)		| Ctrl+w → +											| 選択されている画面を１行分拡大する |
|共通(win)		| Ctrl+w → -											| 選択されている画面を１行分縮小する |
|共通(win)		| Ctrl+w → =											| 画面のサイズを等しくする |
|共通(cmd)		| コマンド\|コマンド									| コマンド連続実行 |
|共通(cmd)		| :redir end											| コマンドリダイレクト 終了 |
|共通(cmd)		| :redir > file											| コマンドリダイレクト 開始 |
|共通(LF)		| :set ff=dos											| 改行コード 書換(\*1) (dos/mac/unix)|
|共通(LF)		| :set ffs=unix,dos,mac									| 改行コード 表示方法変更（閲覧時の自動判別用）br()→カンマで区切って優先度の高い順に指定 |
|共通(LF)		| :e ++ff=dos											| 改行コード 表示方法変更（自動判別失敗時の読み直し用）(dos/mac/unix) |
|共通(char)		| :set enc=utf-8										| 文字コード(デフォルト) 書換(\*2) (euc-jp/shift\_jis/utf-8/..) |
|共通(char)		| :set fenc=utf-8										| 文字コード(現在ファイル) 書換(\*2) (euc-jp/shift\_jis/utf-8/..) |
|共通(char)		| :set fencs=euc-jp,shift\_jis,utf-8					| 文字コード 表示方法変更（閲覧時の自動判別用）br()→カンマで区切って優先度の高い順に指定 |
|共通(char)		| :e ++enc=utf-8										| 文字コード 表示方法変更（自動判別失敗時の読み直し用） (euc-jp/shift\_jis/utf-8/..) |
|Grep			| :vim {pattern} %\|cw									| vimgrepを実行&br()ex.vimgrep /hogehoge/j c:/test/\*\*/\*.txt\|cw |
|Grep			| :bufdo vimgrepa {pattern} %\|cw						| バッファすべてに vimgrep &br()（★貼り付け時は「｜」を半角に★） |
|Grep			| :RGrep 文字列 C:\00\_work\trunk\C\jsp-1.4.4-full\*.c	| 特定のフォルダ配下のCファイルを再帰検索 |
|Align			| :Align ,（範囲選択後）								| インデント調整(","のほかには"=" "+" "-"がある)(\*3) |
|Align			| \abox（範囲選択後）									| ボックスコメント設定(\*4) |
|DrawIt!		| \di（範囲選択後）										| 描画モード開始 |
|DrawIt!		| \ds（範囲選択後）										| 描画モード終了 |
|DrawIt!		| \b （範囲選択後）										| 四角形ボックス描画 |
|DrawIt!		| \e （範囲選択後）										| ひし形ボックス描画 |
|DrawIt!		| v  （範囲選択後）										| v描画 |
|DrawIt!		| ^  （範囲選択後）										| ^描画 |
|DrawIt!		| >  （範囲選択後）										| >描画 |
|DrawIt!		| <  （範囲選択後）										| <描画 |
|Vundle			| :PluginInstall										| プラグインインストール |
|surround		| S'													| ビジュアルモードで選択した部分を ' で囲む |
|surround		| yss'													| 行全体を ' で囲む |
|neosnippet		| :NeoSnippetEdit										| スニペットを編集 |
|QuickFix		| :copen												| QuickFixウィンドウを開く |
|QuickFix		| :cw													| 認識されたエラーや結果があればQuickFixウィンドウを開く (注) エラーや結果が何もなければ開かれない |
|QuickFix		| :cclose または :ccl									| QuickFixウィンドウを閉じる |
|QuickFix		| :.cc													| QuickFix内のカーソル下の箇所に移動 |
|QuickFix		| :cn													| QuickFix内の次検索結果に移動 |
|QuickFix		| :cN													| QuickFix内の前検索結果に移動 |
|QuickFix		| :cbuffer												| QuickFixバッファ再読み込み |
|showmarks		| :DoShowMarks											| マーク表示＠現在バッファ |
|showmarks		| :DoShowMarks!											| マーク表示＠全バッファ |
|showmarks		| :NoShowMarks											| マーク非表示＠現在バッファ |
|showmarks		| :NoShowMarks!											| マーク非表示＠全バッファ |
|showmarks		| :[count]ShowMarksOnce									| Display marks for [count] Cursorhold events. Mostly for mapping it like : nnoremap ` :ShowMarksOnce<cr>` |
|showmarks		| :[count]PreviewMarks									| Display marks of current buffer in pvw.  Like ':marks', but at the top of the window ;-).  [count] is the same sa above. |
|Vaffle			| ~														| $HOMEを開く |
|Vaffle			| h														| 親を開く |
|Vaffle			| l														| 子を開く |
|Vaffle			| t														| 新しいタブで開く |
|Vaffle			| <Space>												| 選択、解除 |
|Vaffle			| *														| 全て選択、全て解除 |
|Vaffle			| .														| 隠しファイルを表示、隠しファイルを非表示 |
|Vaffle			| R														| 更新 |
|Vaffle			| m														| 移動 |
|Vaffle			| d														| 削除 |
|Vaffle			| r														| 名前変更 |
|Vaffle			| i														| ファイル作成 |
|Vaffle			| o														| ディレクトリ作成 |
|Vimdiff		| vim -d file1 file2									| vimdiff 起動 |
|Vimdiff		| vimdiff file1 file2									| vimdiff 起動 |
|Vimdiff		| :e													| vimdiff 再比較 |
|Vimdiff		| :diffupdate											| vimdiff 再比較 |
|Vimdiff		| [c													| vimdiff カーソル移動 次のdiff |
|Vimdiff		| ]c													| vimdiff カーソル移動 前のdiff |
|Vimdiff		| do													| vimdiff 現在位置へ差分取り込み(diff obtain) |
|Vimdiff		| dp													| vimdiff 現在位置から差分コピー(diff put) |
|Vimdiff		| :diffg												| vimdiff 現在位置へ差分取り込み(diffget) |
|Vimdiff		| :diffpu												| vimdiff 現在位置から差分コピー(diffput) |
|Vimdiff		| :diffoff												| vimdiff diffモード終了 |
|Vimdiff		| :set diffopt+=vertical								| vimdiff 垂直分割 |
|Vimdiff		| :set diffopt+=horizontal								| vimdiff 水平分割 |
|Vimdiff		| :set diffopt+=icase									| vimdiff 大小文字無視 |
|Vimdiff		| :set diffopt+=iwhite									| vimdiff 空白数差異無視 |
|Vimdiff		| :set diffopt+=iwhiteall								| vimdiff 空白変更全無視 |

★linediff
★blockdiff
★neosnipet
★tagbar
★winresizer
★vim-surround

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
					- ＝秀丸の通常検索
				- \v（very magic）
					- それ以降の、'0'-'9'、'a'-'z'、'A'-'Z'、'_'、以外のすべての ASCII 文字は特別な意味を持ちます。
					- ＝秀丸の正規表現検索
				- \M（nomagic）
					- ★
				- \V（very nomagic）
					- それ以降はバックスラッシュと終端文字 (/ や ?) だけが特別な意味を持ちます。
	- 検索文字列のタグ指定：\1,\2,\3,...
		- ex) :s/\v^(\w+).*/\1/g
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

- [エスケープが必要な文字一覧](http://deris.hatenablog.jp/entry/2013/05/15/024932)

| \v（very magic） | \m（magic）（デフォルト） | \M（nomagic） | \V（very nomagic） |
| \ | \ | \ | \ |
| . | . | ^ |  |
| * | * |  |  |
| + |  |  |  |
| ? |  |  |  |
| = (\*1) |  |  |  |
| { |  |  |  |
| ^ | ^ |  |  |
| $ | $ | $ |  |
| ( |  |  |  |
| ) |  |  |  |
| | |  |  |  |
| \[ | \[ |  |  |
| & (\*1) |  |  |  |
| @ (\*1) |  |  |  |
| ~ (\*1) | ~ (\*1) |  |  |
| / (\*2) | / (\*2) | / (\*2) | / (\*2) |

(\*1) =,&,@,~は、Perlの正規表現方言ではメタ文字ではないのでハマりポイント
(\*2) 検索コマンド/で検索する場合、/でパターンを囲う場合

- [正規表現比較](http://deris.hatenablog.jp/entry/2013/05/15/024932)

| Perlのメタ文字 | Vimのメタ文字(very magic) | 説明 | 備考 |
| . | 同じ | 任意の1文字 |  |
| * | 同じ | 直前のアトムの繰り返し(0回以上) | 最長マッチ |
| + | 同じ | 直前のアトムの繰り返し(1回以上) | 最長マッチ |
| ? | 同じ(=も同じ) | 直前のアトム(0回、または1回) | 最長マッチ |
| {n,m} | 同じ | 直前のアトムの繰り返し(n回以上m回以下) | 最長マッチ |
| ^ | 同じ | 先頭にマッチ |  |
| $ | 同じ | 末尾にマッチ |  |
| (...) | 同じ | グループ化してアトムにする |  |
| | | 同じ | 選択の区切り |  |
| [...] | 同じ | [...]内の任意の1文字にマッチ |  |
| \w | 同じ | 単語を構成する文字([0-9A-Za-z\_]) |  |
| \W | 同じ | 単語を構成する文字以外([\^0-9A-Za-z\_]) |  |
| \d | 同じ | 数字([0-9]) |  |
| \D | 同じ | 数字以外([\^0-9]) |  |
| \s | 同じ | 空白文字(微妙に違う。後述) |  |
| \S | 同じ | 空白文字以外(微妙に違う。後述) |  |
| \*? | {-} | 直前のアトムの繰り返し(0回以上) | 最短マッチ |
| +? | {-1,} | 直前のアトムの繰り返し(1回以上) | 最短マッチ |
| ?? | {-0,1} | 直前のアトム(0回、または1回) | 最短マッチ |
| {n,m}? | {-n,m} | 直前のアトムの繰り返し(n回以上m回以下) | 最短マッチ |
| \b | <?or?> | 単語の境界にマッチ(<は単語先頭、>は単語末尾) |  |
| (?=atom) | atom@= | 幅ゼロの肯定先読み     | kimura( takuya)@= （後に" takuya"が含まれる"kimura"を検索）  |
| (?!atom) | atom@! | 幅ゼロの否定先読み     | kimura( takuya)@! （後に" takuya"が含まれない"kimura"を検索  |
| (?<=atom) | atom@<= | 幅ゼロの肯定後読み   | (inagaki )@<=goro （前に"inagaki "が含まれる"goro"を検索）   |
| (?<\!atom) | atom@<\! | 幅ゼロの否定後読み | (inagaki )@<\!goro（前に"inagaki "が含まれない"goro"を検索） |
| (?\>atom) | atom@> | 幅ゼロの否定後読み |  |
| (?:...) | %(...) | グループ化して部分正規表現としてカウントしない |  |

# スニペット
- [neosnippet使い方](http://d.hatena.ne.jp/adragoona/touch/20130929/1380437722)

[トップに戻る](../index.md)
