[トップに戻る](../index.md)

# [コマンド](https://flex.phys.tohoku.ac.jp/texi/gdb-j/gdb-j_toc.html)
	
	- 【デバッグ用コンパイル】gcc -g ./a.out
	- 【デバッグ開始】gdb ./a.out
	- 【デバッグ開始(スクリプト実行)】gdb ./a.out -x scriptname
	- 【デバッグ開始(引数指定)】gdb --args a.out AAAA
	- 【プロセスアタッチ】attach process
	- 【プロセスデタッチ】detach
	
	- 【リセット＆実行(run)】r
	- 【★】start
	- 【終了(quit)】q
	
	- 【ステップ実行(1行ずつ実行/関数は飛ばす)(next)】n
	- 【ステップ実行(1行ずつ実行/関数は飛ばす)(nexti)★】ni
	- 【ステップ実行(1行ずつ実行/関数の中に入る)(step)】s
	- 【ステップ実行(1行ずつ実行/関数の中に入る)(stepi)★】si
	- 【処理実行(次ブレークポイントまで)(continue)】c
	- 【処理実行(現在の関数を抜けるまで)(★)】f
	- 【処理実行(現在のループを抜けるまで)(★)】u
	- 【処理実行(現在関数復帰まで)(finish)】fin
	- 【処理実行(特定アドレス到達まで)(until)】u \*main+43
	
	- 【ステップアウト】ret -1 #現在の関数を戻り値-1として強制的に抜ける
	
	- 【ブレークポイント設定】
		- 【関数指定(break)】b funcname
		- 【アドレス指定(break)】b \*0x08048695
		- 【一時的(tbreak)】tb funcname
		- 【行番号指定(break)】b bubblesort.c:30
		- 【条件付き(break)】b filename if n == 1
		- 【変数書込時】watch i==10 #変数は静的変数のみ指定できる（＝ウォッチポイントともいう）
		- 【変数読出時】rwatch \*0xbffff76c
		- 【変数読書時】awatch \*0xbffff76c
	- 【ブレークポイント情報表示(info breakpoints)】i b
	- 【ブレークポイント削除(ブレークポイント番号指定)(delete)】d 1 #ブレークポイント番号(info breakpointsにて取得)を指定する
	- 【ブレークポイント削除(行番号指定)】clear nn
	- 【ブレークポイント無効化(行番号指定)】disable nn
	- 【ブレークポイント有効化(行番号指定)】enable nn
	- 【ブレーク時の動作設定】command 1 #ブレークポイント番号を指定する
		- 上記コマンドを入力後停止時のコマンドを入力する([こちら](https://www.ois-yokohama.co.jp/oisblog2018/archives/3424))
	- 【ブレークポイント設定(システムコール時)】catch syscall write
	- 【ウォッチポイント停止条件指定】condition 1 if n == 1
	
	- 【コード表示(現在実行行前後)(list)】l
	- 【コード表示(関数指定)(list)】l funcname
	
	- 【停止時表示変数表示】display
	- 【停止時表示変数設定】display varname
	- 【停止時表示無効化】disable display 1 #info displayで取得した番号を指定する
	- 【停止時表示有効化】enable display 1 #info displayで取得した番号を指定する
	- 【停止時表示設定表示】info display
	
	- 【レジスタ表示(info register)】i r
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
	- 【変数表示(print)】p var1
	- 【変数表示(配列)(print)】p array
	- 【変数表示(長さ指定)(print)】p (char[8]) name
	- 【変数表示(アドレス)(print)】p &name
	- 【変数表示(表示形式指定)(print)】p/x name #16進表示
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
	- 【型表示1】whatis array
	- 【型表示2】ptype array
	- 【変数値設定】set array[3] = 199
	
	- 【メモリ配置確認(info proc mappings)】i proc map
	
	- 【バックトレース(backtrace)】bt #現在関数呼出しまでの経路表示
	- 【バックトレース結果さかのぼり】up
	- 【バックトレース結果下り】down
	- 【アベンド場所表示★】where
	
	- 【マクロ定義表示】info macro マクロ名	
	- 【変数表示(全ローカル変数)(info localvariables)】i lo
	- 【ウォッチポイントを設定(watchpoint)】w var1
	- 【シェルコマンド実行1】shell ls
	- 【シェルコマンド実行2】!ls
	
	- 【TUIモード移行(アセンブリモード)】layout asm
	- 【TUIモード移行(ソースモード)】layout src
	- 【TUIモード移行(レジスタ)】layout regs
	- 【TUIモード脱出】tui disable
		- TUIモードとは
			- コードを表示しながらデバッグできる機能
			- Text User Interface の略
			- 「Ctrl+x → Ctrl+a」で移行脱出を切り替えられる
	- 【逆アセンブル表示】disassemble /m
	- 【スクリプト実行】source scriptname

	- マルチスレッド
		- 【スレッド情報表示】info threads
		- 【スレッド切り替え】thread 1 #info threadsで取得できるスレッド番号を指定する

[トップに戻る](../index.md)
