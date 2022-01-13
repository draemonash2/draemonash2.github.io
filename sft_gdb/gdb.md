[トップに戻る](../index.md)

# [コマンド](https://flex.phys.tohoku.ac.jp/texi/gdb-j/gdb-j_toc.html)
- 【デバッグ用コンパイル】`gcc -g ./a.out`
- 【デバッグ開始】`gdb ./a.out`
- 【デバッグ開始(スクリプト実行)】`gdb ./a.out -x scriptname`
- 【デバッグ開始(引数指定)】`gdb --args a.out AAAA`
- 【プロセスアタッチ】`attach pid`
- 【プロセスデタッチ】`detach`

- 【リセット＆実行(run)】`r`
- 【終了(quit)】`q`
- 【main()先頭まで実行】`start #main関数の入口に1回だけのブレークポイントを張ってプログラムを開始する`
- 【引数指定実行】`run --foo --bar`

- 【ステップ実行(1行ずつ/関数は飛ばす)(next)】`n`
- 【ステップ実行(1命令ずつ/関数は飛ばす)(nexti)】`ni`
- 【ステップ実行(1行ずつ/関数の中に入る)(step)】`s`
- 【ステップ実行(1命令ずつ/関数の中に入る)(stepi)】`si`
- 【処理実行(次ブレークポイントまで)(continue)】`c`
- 【処理実行(現在の関数を抜けるまで)(finish)】`fin`
- 【処理実行(現在のループを抜けるまで)(until)】`u`
- 【処理実行(特定アドレス到達まで)(until)】`u \*main+43`

- 【ステップアウト】`ret -1 #現在の関数を戻り値-1として強制的に抜ける`

- 【ブレークポイント設定】
	- 【関数指定(break)】`b funcname`
	- 【アドレス指定(break)】`b \*0x08048695`
	- 【一時的(tbreak)】`tb funcname`
	- 【行番号指定(break)】`b bubblesort.c:30`
	- 【条件付き(break)】`b filename if n == 1`
	- 【変数書込時】`watch i==10 #変数は静的変数のみ指定できる（＝ウォッチポイントともいう）`
	- 【変数読出時】`rwatch \*0xbffff76c`
	- 【変数読書時】`awatch \*0xbffff76c`
- 【ブレークポイント情報表示(info breakpoints)】`i b`
- 【ブレークポイント削除(ブレークポイント番号指定)(delete)】`d <bnum> #ブレークポイント番号(info breakpointsにて取得)を指定する`
- 【ブレークポイント削除(行番号指定)】`clear <bnum>`
- 【ブレークポイント無効化(行番号指定)】`disable <bnum>`
- 【ブレークポイント有効化(行番号指定)】`enable <bnum>`
- 【ブレーク時の動作設定】`command <bnum>`
	- 上記コマンドを入力後停止時のコマンドを入力する([こちら](https://www.ois-yokohama.co.jp/oisblog2018/archives/3424))
- 【ブレークポイント設定(システムコール時)】`catch syscall write`
- 【ブレークポイント指定回数無視】`ignore <bnum> 9 #ブレークポイント番号1を9回無視する`
- 【ブレークポイント停止条件追加】`condition <bnum> if n == 1`

- 【コード表示(現在実行行前後)(list)】`l`
- 【コード表示(関数指定)(list)】`l funcname`

- 【停止時表示変数表示】`display`
- 【停止時表示変数設定】`display varname`
- 【停止時表示設定表示】`info display`
- 【停止時表示無効化】`disable display 1 #info displayで取得した番号を指定する`
- 【停止時表示有効化】`enable display 1 #info displayで取得した番号を指定する`
- 【停止時表示削除】`undisplay 1 #info displayで取得した番号を指定する`

- 【ソースディレクトリ指定(dirname)】`dir ...`
	- 複数ディレクトリ指定時はコロンもしくは空白で区切る
	- カレントディレクトリは$cwdを指定する
	- ★$cdir
- 【ソースディレクトリ一覧出力】`show directories`

- 【レジスタ表示(info register)】`i r`
	- 表示対象レジスタ
		- eax：汎用レジスタ
		- ebx：汎用レジスタ
		- ecx：汎用レジスタ
		- edx：汎用レジスタ
		- esp：スタックポインタ
		- ebp：ベースポインタ
		- esi：汎用レジスタ
		- edi：汎用レジスタ
		- eip：インストラクションポインタ
		- ps (eflags)：プロセッサ・ステータス（フラグレジスタ）
		- cs：セグメントレジスタ
		- ss：セグメントレジスタ
		- ds：セグメントレジスタ
		- es：セグメントレジスタ
		- fs：セグメントレジスタ
		- gs：セグメントレジスタ
		- pc：インストラクションポインタの指す内容
- 【変数表示(print)】`p var1`
- 【変数表示(配列)(print)】`p array`
- 【変数表示(長さ指定)(print)】`p (char[8]) name`
- 【変数表示(アドレス)(print)】`p &name`
- 【変数表示(表示形式指定)(print)】`p/x name #16進表示`
	- 表示形式
		- x：１６進数
		- d：１０進数（デフォルト）
		- u：符号なし１０進数
		- o：８進数
		- t：２進数
		- a：アドレス
		- c：文字
		- f：浮動小数点数
		- i：命令
- 【型表示1】`whatis array`
- 【型表示2】`ptype array`
- 【変数値設定】`set array[3] = 199`

- 【メモリ配置確認(info proc mappings)】`i proc map`
- 【スタックフレーム表示】`frame 0 #フレーム番号`

- 【バックトレース(backtrace)】`bt #現在関数呼出しまでの経路表示`
- 【バックトレース全て(backtrace)】`bt full`
- 【バックトレース結果さかのぼり】`up`
- 【バックトレース結果下り】`down`
- 【バックトレース】`where #backtraceのエイリアス`

- 【マクロ定義表示】`info macro マクロ名	`
- 【変数表示(全ローカル変数)(info localvariables)】`i lo`
- 【ウォッチポイントを設定(watchpoint)】`w var1`
- 【シェルコマンド実行1】`shell ls`
- 【シェルコマンド実行2】`!ls`

- 【逆アセンブル表示】`disassemble /m`
- 【スクリプト実行】`source scriptname`
- 【gdbinit再読み込み】`source /home/tsuyoshi/.gdbinit`

- マルチスレッド
	- 【スレッド情報表示】`info threads`
	- 【スレッド切り替え】`thread 1 #info threadsで取得できるスレッド番号を指定する`

- 【ロギング設定】`set logging file <ログファイル名>`
- 【ロギング開始】`set logging on`
- 【ロギング終了】`set logging off`

- 【エンディアン確認】`show endian`
- 【エンディアン設定】`set endian (big|little)`

- 【コアダンプ解析】`gdb ./exefile <coreファイル>`

- 【エイリアス】`alias -a w = dashboard expression watch`
- 【関数定義】`define 関数名 ～ 処理 ～ end`


# コマンド(TUIモード)
- 概要
	- コードを表示しながらデバッグできる機能
	- Text User Interface の略

- 【TUIモード起動/終了】Ctrl+x → a
- 【TUIシングルキーモード開始/終了】Ctrl+x → s
- 【TUIモード移行(アセンブリモード)】`layout asm`
- 【TUIモード移行(ソースモード)】`layout src`
- 【TUIモード移行(レジスタ)】`layout regs`
- 【TUIモード脱出】`tui disable`
- 【全ウィンドウサイズ一覧表示】`info win`
- 【レイアウト切替 次】`layout next`
- 【レイアウト切替 前】`layout prev`
- 【レイアウト切替 ソース】`layout src`
- 【レイアウト切替 アセンブリ】`layout asm`
- 【レイアウト切替 ソース＋アセンブリ】`layout split`
- 【レイアウト切替 ソースorアセンブリ＋レジスタ】`layout regs`
- 【フォーカス切替 次】`focus next`
- 【フォーカス切替 前】`focus prev`
- 【フォーカス切替 ソース】`focus src`
- 【フォーカス切替 アセンブリ】`focus asm`
- 【フォーカス切替 レジスタ】`focus regs`
- 【フォーカス切替 コマンド】`focus cmd`
- 【画面リフレッシュ】`refresh`
- 【レジスタ表示切替 浮動小数点レジスタ】`tui reg float`
- 【レジスタ表示切替 一般レジスタ】`tui reg general`
- 【レジスタ表示切替 次レジスタグループ】`tui reg next`
- 【レジスタ表示切替 システムレジスタ】`tui reg system`
- 【ソースウィンドウ 現在の実行ポイント更新】`update`
- 【ウィンドウ高さ変更 上】`winheight <winname> +count`
- 【ウィンドウ高さ変更 下】`winheight <winname> -count`
- 【タブストップ幅設定】`tabset <nchars>`

# Tips
- [gdb開始後にmain関数先頭で停止させる方法](https://qiita.com/aosho235/items/e8efd18364408231062d)
	- `gdb -ex start`
- [set ～ 一覧](http://www.asahi-net.or.jp/~wg5k-ickw/html/online/gdb-5.0/gdb-ja_9.html)

# .gdbinit
- ~/.gdbinitはグローバルな設定ファイル。その中で下記の設定をしておくとカレントディレクトリから.gdbinitを読み込んでくれる。
- [.gdbinitのサンプル](https://qiita.com/aosho235/items/e8efd18364408231062d)

```
# コマンド履歴を保存する
set history save on
set history size 10000
set history filename ~/.gdb_history

# listコマンドで表示する行数
set listsize 25

# 配列の要素を全て表示する
set print elements 0

# 構造体のメンバを1行ずつ表示できる
set print pretty on

# quitコマンドで終了するときに確認しない
define hook-quit
    set confirm off
end

# エイリアス
# よく使うコマンドはガンガンエイリアスを定義しておくのがよいと思う
alias -a a = advance
alias -a w = disp
alias -a uw = undisp
alias -a ib = info b
alias -a ia = info args
alias -a il = info locals
alias -a bd = clear
```

[トップに戻る](../index.md)
