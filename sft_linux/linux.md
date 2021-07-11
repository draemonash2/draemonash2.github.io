[トップに戻る](../index.md)

# 関連リンク

- [WSL2](../sft_wsl2/wsl2.md)
- [Raspberry Pi](../sft_raspberrypi/raspberrypi.md)

# コマンド構文
- 【コマンドプロンプト記号】
	- 【rootユーザー】#
	- 【一般ユーザー(Bシェル系)】$
	- 【一般ユーザー(Cシェル系)】%
	- 【一般ユーザー(Tシェル系)】>
- 【コマンド実行】cmd
- 【コマンド実行(非エイリアス)】\cmd # エイリアスを介さない元のコマンドを実行する
- 【[コマンド実行(直近実行コマンド)](https://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q13147860248)】!cmd
	- ex. 最後に実行したlsが `ls -R | grep "babababa" #①` だった場合、そののちに `!ls` と入力すると、①のコマンドが再度実行される
- 【[コマンド実行(直前コマンド)](https://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q13147860248)】!!
	- ex. 最後に実行したlsが `ls -R | grep "babababa" #①` だった場合、その直後に `!!` と入力すると、①のコマンドが再度実行される
	
- [コマンド連続実行方法](https://qiita.com/egawa_kun/items/714394609eef6be8e0bf)
	- 【；】コマンド1終了後、コマンド2実行（実行結果に関わらず）
	- 【＆】コマンド1実行(バックグラウンド)中に、コマンド2実行
	- 【｜】コマンド1実行結果をコマンド2へ渡して実行
	- 【＆＆】コマンド1正常終了後、コマンド2実行
	- 【｜｜】コマンド1異常終了時、コマンド2実行
- [シェルスクリプトを実行する時の書いておくとよいこと](https://qiita.com/youcune/items/fcfb4ad3d7c1edf9dc96)
	- 【set -e】エラーがあったらシェルスクリプトをそこで打ち止めにしてくれる
	- 【set -u】未定義の変数を使おうとしたときに打ち止めにしてくれる
- ワイルドカード
	- `?` ：任意の一文字
	- `*` ：0個以上の任意の文字列
- 【まとめてコマンド実行】(cmd1;cmd2)
- 【現在のシェルでコマンド実行】{cmd1;cmd2}
- 引用符の違い
	- 【'】全て文字列としてみなす
	- 【"】文字列とみなすが、変数の場合は変数の中身を展開
	- 【`】コマンドの場合はコマンド実行結果を展開、変数の場合は変数に格納されたコマンドの実行結果が展開
		```sh
		$ DATE=date
		$ echo '$DATE'
		$DATE
		$ echo "$DATE"
		date
		$ echo `$DATE`
		Fri May 17 04:26:03 PDT 2013
		```
		
- リダイレクト
	- 種別
	
		 | コマンド(*1)						   | 画面(*2)		  | ファイル(*2) | 出力形式 | 
		 | :---								   | :---			  | :---		 | :---		| 
		 | command > out.log				   | E				  | O			 | 新規		| 
		 | command 2> out.log				   | O				  | E			 | 新規		| 
		 | command > out.log 2>&1			   | -				  | O/E			 | 新規		| 
		 | command &> out.log				   | -				  | O/E			 | 新規		| 
		 | command &>> out.log				   | -				  | O/E			 | 追記		| 
		 | command >> out.log 2>&1			   | -				  | O/E			 | 追記		| 
		 | command 1> stdout.log 2> stderr.log | -				  | O/E(*3)		 | 新規		| 
		 | command \| tee -a out.log		   | O/？			  | O			 | 新規		| 
		 | command \| & tee -a out.log		   | O/E			  | O/E			 | 新規		| 
		 | command &> /dev/null				   | -				  | -			 | -(*4)	| 
		
			- (*1) command を exec とすると、以降の出力先を変更するコマンドになる
			- (*2) O:標準出力、E:標準エラー出力
			- (*3) 標準出力をstdout.logへ、標準エラー出力をstderr.logへ出力
			- (*4) 画面とファイル出力を抑制したい場合に使用する
- フォアグラウンドとバックグラウンドの制御
	![フォアグラウンドとバックグラウンドの制御](フォアグラウンドとバックグラウンドの制御.jpg)
- [ブレース展開](https://qiita.com/ine1127/items/6e5fe80f4a9c64509558)
	- 【ブレース展開例01】{a,b,c} #→a b c
	- 【ブレース展開例02】{6..10} #→6 7 8 9 10
	- 【ブレース展開例03】{1..10..2} #→1 3 5 7 9
	- 【ブレース展開例04】a{m,n} #→am an
	- 【ブレース展開例05】{m,n}a #→ma na
	- 【ブレース展開例06】a{m,n}b #→amb anb
	- 【ブレース展開例07】{a,b}{m,n} #→am an bm bn
	- 【ブレース展開例08】a{,m,n} #→a am an
	- 【ブレース展開例09】a{m,n,} #→am an a
	- 【ブレース展開例10】a{,,,} #→a a a a
	- 【ブレース展開例11】a{,b{,c}} #→a ab abc

- ★要整理★
	- !^	直前コマンドの最初の引数
	- !$	直前コマンドの最終の引数
	- !\*	直前コマンドの全引数
	- !:-	直前コマンドの全引数(最終引数を除く)
	- $\_	直前コマンドの最終引数
	- $$	シェルのPID
	- !-n	直近n番目に実行したコマンド
	- !n	直近n番目に実行したコマンド(ヒストリ)
	- !!	直前コマンド再実行
	- !<command>	直近実行コマンド再実行(直近の<command>)
	- !!:s/<FROM>/<TO>/	直前コマンドの最初の★を置換
	- !!:gs/<FROM>/<TO>/	直前コマンドの全ての★を置換
	- !$:t	直前コマンド最終引数のファイルベース名
	- !$:h	直前コマンド最終引数のディレクトリパス
	- !!:n	直前コマンドのn番目のトークン(0:コマンド名、1以降:引数)
	- !!:n-m	直前コマンドのn～m番目のトークン
	- !!:n-$	直前コマンドのn～最終トークン

- [変数展開](https://qiita.com/t_nakayama0714/items/80b4c94de43643f4be51#parameterword-%E3%83%87%E3%83%95%E3%82%A9%E3%83%AB%E3%83%88%E5%80%A4%E4%BB%A3%E5%85%A5%E3%81%82%E3%82%8A)
	- 【参照】${hoge}
	- 【空変数時デフォルト値参照】${hoge:-"default"} #hogeにdefaultが代入されない
	- 【空変数時デフォルト値代入】${hoge:+"default"} #hogeにdefaultが代入される
	- 【変数未定義時デフォルト値参照】${hoge-"default"} #hogeにdefaultが代入されない
	- 【変数未定義時デフォルト値代入】${hoge+"default"} #hogeにdefaultが代入される
	- 【変数未定義時エラー出力】${hoge:?"error-message"}
	- 【非空変数時代用代入】${hoge:+"other-value"}
	- 【非空変数時代用参照】${hoge+"other-value"}
	- 【文字列抽出】${hoge:5} #0オリジンで5文字目以降を参照
	- 【文字列抽出】${hoge:5:3} #0オリジンで5～7文字目を参照
	- 【文字列抽出】${hoge:5:-1} #0オリジンで5文字目以降で、末尾から1文字取り除いたものを参照
	- 【文字数出力】${#hoge} #hogeが"other-value"なら、11が返却される
	- 【配列要素数出力】${list[*]}
	- 【前方一致除去(最短一致)】${hoge#hoge-} #hogeが"hoge-value"なら、"value"が返却される
	- 【前方一致除去(最長一致)】${hoge##*hoge-}
	- 【後方一致除去(最短一致)】${hoge%-value}
	- 【後方一致除去(最長一致)】${hoge%%-value*}
	- 【文字列置換(先頭単語のみ)】${hoge/value/fuga} #hoge内の文字列valueをfugaに置換する
	- 【文字列置換(全単語)】${hoge//hoge/fuga}
	- 【大文字化(先頭文字)】${hoge^}
	- 【大文字化(全文字)】${hoge^^}
	- 【小文字化(先頭文字)】${hoge,}
	- 【小文字化(全文字)】${hoge,,}
	- 【大文字小文字反転(先頭文字)】${hoge~}
	- 【大文字小文字反転(全文字)】${hoge~~}
	- 【数式展開】$((1+2\*3))

# シェルスクリプト構文

- 【シェバン(シバン)】#!/bin/bash
	- 「#!」…スクリプトを実行するシェルプログラムを指定する記号
- 【メタキャラクタ】data{1,2} #data1 と data2に展開される

- [setコマンド](https://www.atmarkit.co.jp/ait/articles/1805/10/news023.html)
	- 【シェルオプション設定】set [-o] [+o] オプション
		- 操作種別
			- -o：オプション有効化
			- +o：オプション無効化
		- オプション一覧
			- 【作成/変更変数の自動的エクスポート】allexport
			- 【キーバインドemacs化】emacs
			- 【キーバインドvi化】vi
			- 【Ctrl＋Dによるログアウト禁止】ignoreeof
			- 【既存ファイルへの上書き出力禁止】noclobber
			- 【メタキャラクタを使用したファイル名展開無効化】noglob
	- 【変数一覧表示】set
	- 【シェルオプション表示】set -o
	- 【エラー発生時強制終了】set -e #＝「set -o errexit」
	- 【未定義変数使用時強制終了】set -u
	- 【パス名展開無効化】set -f #＝「set -o noglob」。アスタリスクなどでのワイルドカードでの展開を無効化する
	- 【実行コマンド出力】set -x
	- 【実行コマンド出力】set -v
	- 【構文チェックのみ実施(実行しない)】set -n #＝「set -o noexec」
	- 【ブレース展開無効化】set +B #＝「set +o braceexpand」。デフォルトは有効(ブレース展開する)
	- 【リダイレクト時ファイル上書き無効化】set -C #＝「set -o noclobber」。リダイレクト時の追記はできる。
	- 【作成/変更変数の自動的エクスポート】set -a #＝「set -o allexport」。シェル変数の定義と同時にexportし、環境変数としても使用可能にする。

- 【コメント】#

- 【シェルスクリプト実行方法1】source sample.sh
- 【シェルスクリプト実行方法2】. sample.sh
- 【シェルスクリプト実行方法3】bash sample.sh
- 【シェルスクリプト実行権限付与(change mode)】chmod +x sample.sh
	- シェルスクリプトをコマンドのように実行したい場合は、実行権限を付与する必要がある。

- 【変数定義】name='John'
- 【変数参照】echo ${name} #→John
- 【変数参照】echo "Hi $name" #=> Hi John
- 【変数参照】echo 'Hi $name' #=> Hi $name
- 【変数参照(非空文字列時word返却＆var非保存)】${name:+word}
- 【変数参照(　空文字列時word返却＆var非保存)】${name:-word}
- 【変数参照(　空文字列時word返却＆var　保存)】${name:=word}
- 【変数参照(　空文字列時標準エラー出力表示)】${name:?word}

- 【変数定義(配列)】ARRAY=(item1 item2 item3 item4)
- 【変数参照(配列)】ARRAY[0]

- 【関数定義】function lsmo() { ～ ls -la \| more; ～ }
- 【関数定義削除】unset lsmo

- 【特殊変数 引数の数】$#
- 【特殊変数 引数の値】$n（n=1～9？）
- 【特殊変数 シェルスクリプトファイル名】$0
- 【特殊変数 全ての引数(区切りはスペース)】$@ #→"$1" "$2" "$3" ...
- 【特殊変数 全ての引数(区切りは環境変数IFSで指定したもの)】$\* #→"$1 $2 $3 ..."
- 【特殊変数 現在実行シェルプロセスID】$$
- 【特殊変数 最終実行バックグラウンドプロセスID】$!
- 【特殊変数 直前実行したコマンド終了値(0=正常終了、1=異常終了、それ以外はエラー）】$?

- 【標準入力取得】echo -n "あなたのお名前は?";read yourname

- 【比較演算子(＝)】test 5 -eq 10; echo $? #→1(偽) EQual
- 【比較演算子(≠)】test 5 -ne 10; echo $? #→0(真) Not Equal
- 【比較演算子(≧)】test 5 -ge 10; echo $? #→1(偽) Greater Equal
- 【比較演算子(＞)】test 5 -gt 10; echo $? #→1(偽) Greater Than
- 【比較演算子(≦)】test 5 -le 10; echo $? #→0(真) Less Equal
- 【比較演算子(＜)】test 5 -lt 10; echo $? #→0(真) Less Than
- 【比較演算子(＝)】"$a" == "$b"; echo $? # $aと$bが同じ場合TRUEを返します。
- 【比較演算子(≠)】"$a" != "$b"; echo $? # $aと$bが同じではない場合TRUEを返します。
- 【比較演算子(空文字列)】test -z "$a"; echo $? # $aが何も指定してない場合TRUEを返します
- 【比較演算子(非空文字列)】test -n "$a"; echo $? # $aに何かを指定しした場合TRUEを返します

- 【存在確認(ディレクトリ)】test -d ディレクトリ名 #→ファイルorディレクトリ判定にも使える
- 【存在確認(ファイル)1】test -f ファイル名 #→ファイルorディレクトリ判定にも使える
- 【存在確認(ファイル)2】test -e ファイル名
- 【文字列空文字列確認】test -n 文字列
- 【文字列一致確認1】test 文字列1 = 文字列2
- 【文字列一致確認2】test 文字列1 != 文字列2

- 【ファイル種別判定(0バイト以上】test -s ファイル名
- 【ファイル種別判定(レギュラーファイル)】test -f ファイル名
- 【ファイル種別判定(読込み可)】test -r ファイル名
- 【ファイル種別判定(書込み可)】test -w ファイル名
- 【ファイル種別判定(実行可能)(ディレクトリの場合は移動可能)】test -x ファイル名
- 【ファイル種別判定(シンボリックリンクファイル)】test -h ファイル名
- 【ファイル種別判定(シンボリックリンクファイル)】test -L ファイル名
- 【ファイル種別判定(ブロックデバイスファイル)】test -b ファイル名
- 【ファイル種別判定(キャラクタデバイスファイル)】test -c ファイル名
- 【ファイル種別判定(名前付きパイプ)】test -p ファイル名
- 【ファイル種別判定(ソケットファイル)】test -S ファイル名
- 【ファイル種別判定(スティッキービット設定)】test -k ファイル名 #chown o+t
- 【ファイル種別判定(セットユーザIDビット設定)】test -u ファイル名 #chown u+s
- 【ファイル種別判定(セットグループIDビット設定)】test -g ファイル名 #chown g+s
- 【ファイル種別判定(実効ユーザID所有)】test -O ファイル名
- 【ファイル種別判定(実効グループID所有)】test -G ファイル名

- 【★(change owner)】chown

- 【論理結合(否定)】!条件
- 【論理結合(AND)】条件1 -a 条件2
- 【論理結合(OR)】条件1 -o 条件2

- 【算術演算(加)】echo `expr 10 + 20`
- 【算術演算(減)】echo `expr 20 - 10`
- 【算術演算(乗)】echo `expr 11 \* 11`
- 【算術演算(割)】echo `expr 10 / 2`
- 【算術演算(剰余)】echo `expr 10 % 4`
- 【算術演算(指定)】a=$b # bの値はaに保存されます

- 【if】if [ $NUM1 -eq $NUM2 ]; then ～コマンド(条件式1が真)～ elif [ $NUM1 -eq $NUM3 ]; then ～コマンド(条件式2が真)～ else ～コマンド(条件式2が偽)～ fi
	- `test 1 -eq 1` と `[ 1 -eq 1]` は同等([詳細はこちら](https://ascii.jp/elem/000/001/278/1278792/))
- 【switch】case 変数 in 条件式) コマンド ;; esac
- 【for(リスト指定)】for VAR in Level1 Level2 Level3 ～ do ～ echo LinuC $VAR ～ done
- 【for(数値指定1)】for NUM in `seq 1 3` ～ do ～ echo LinuC Level $NUM ～ done
- 【for(数値指定2)】for ((i = 0; i <= 10; i++)) { ～ echo "$i" ～ }
- 【while】while [ read LINE ] ～ do ～ echo LinuC Level $LINE ～ done < test.txt
- 【until】until [ ! $a -lt 5 ] ～ do ～ echo $a ～ done

- 【ファイル名取得】SRCPATH="/path/to/foo.cpp"; echo ${SRCPATH##\*/} #=> "foo.cpp" (basepath)
- 【ディレクトリパス取得】SRCPATH="/path/to/foo.cpp"; echo ${SRCPATH%$BASE}  #=> "/path/to/" (dirpath)

# コマンド一覧

- コマンド関連
	- 【コマンド履歴表示】history
	- 【コマンド格納先表示】which command
	- 【コマンド格納先表示】whereis command
		- マニュアル、ソース、オブジェクトも指定可能
	- 【コマンド簡易説明表示】whatis command
	- 【コマンドエイリアス確認】type command
	- 【コマンドキーワード検索】apropos
	
	- 【標準出力書き出し(改行付与)】echo hello!
	- 【標準出力書き出し(改行なし)】echo -n hello!
	- 【C言語のprintfと同等】printf
	- 【永遠文字列表示】yes
	
	- 【何もしない(戻り値1)】false
	- 【何もしない(戻り値0)】true
	- 【コマンド戻り値判定】test
	- 【式評価】expr
	
	- 【変数中身出力】echo ${var1}
	- 【コマンド実行結果出力】echo $(cmd1)
	- 【直前コマンドの終了ステータス表示】echo $?
	
	- 【出力を複数ファイルやプロセスに渡す】tee
		- コマンド結果をファイルに書きつつ、標準出力にも出力したいときに使う。(リダイレクションでは標準出力されない)
	
	- 【エイリアス設定】alias ll='ls -al'
	- 【エイリアス解除】unalias ll
	
	- 【パッケージインストール(Debian系)】apt install package\_name
		- aptをapt-getの設計改良版の位置づけらしい([詳細はこちら](https://www.atmarkit.co.jp/ait/articles/1708/31/news017.html))
	- 【パッケージ削除(Debian系)】apt remove package\_name
	- 【パッケージ更新(Debian系)】apt upgrade package\_name
	- 【パッケージインストール(RedHat系)】yum install package\_name
	
	- 【コンパイル実行】gcc -o objfile srcfile
	- 【コンパイル実行(コンパイル＆アセンブルのみ)】gcc -c -o objfile srcfile
	
	- 【コマンド結果をクリップボードにコピー】xclip
		- 以下の通りコマンドのインストールが必要。（[詳細はこちら](https://linuxfan.info/xclip)）
			- sudo apt install -y xclip
		- →WSL2では使えないかも…
	
	- 【ユーザ切り替え】su user1
	- 【管理者権限実行】sudo
	
	- 【タイムリミット設定後コマンド実行】timeout 5 cmd
	- 【実行遅延】sleep 1d 1h 1m 1s
	
	- 【コマンドライン引数受取後実行】cmd1 \| xargs cmd2
		- xargsとは
			- [「標準入力を引数に変換」してくれるもの](https://teratail.com/questions/63845)
				- パイプでつないだ場合、前コマンドを標準出力を次コマンドの標準入力として受け取る。
				- 標準入力を入力にできないコマンド(ex. echo,rm 等)は、xargsで標準入力→引数に変換する必要がある。
				- 標準入力を入力にできるコマンド(ex. cat,sort,uniq等)は、xargsなしでそのままパイプで渡せる。
					- 標準入力を入力にできるコマンドかどうかは、引数なしでコマンドを実行すればわかる。(ex. sort)
	- 【プロセス実行優先度変更後コマンド実行】nice -n -15 updatedb #実行優先度を「15」低くして、updatedbコマンドを実行
		- niceness…プロセスの優先度を示す値(＝アプリケーション実行順序)(≠スケジュール優先度)
	- 【ログアウト後継続コマンド実行】nohup cmd
	- 【スクリプト自動実行】at -c 0400pm script.sh #=> 午後4時にスクリプトを自動実行
	
	- 【簡易電卓】bc

- ファイル操作
	- 【ディレクトリ移動】cd
	- 【ディレクトリ移動(直前)】cd -
	- 【ディレクトリ移動([mv後のディレクトリへ](https://qiita.com/arene-calix/items/41d8d4ba572f1d652727))】cd !$
	- 【ディレクトリ移動(保存)】pushd
	
	- 【ファイル作成】touch file
	- 【ディレクトリ作成(再帰的)】mkdir -p aaa/bbb/ccc
	
	- 【ファイル削除】rm a.txt
	- 【ディレクトリ削除(再帰的1)】rm -r aaa
	- 【ディレクトリ削除(再帰的2)】rmdir -p aaa/bbb/ccc
		- 備考1：「rmdir -p aaa」では削除不可
		- 備考2：ディレクトリaaaとbbbとcccのみ削除するため、厳密には配下のファイルをすべて削除するわけではない。
			- →上記より「rm -r aaa」の方がいいかも
	- 【ファイル完全削除】shred -u file.txt
	
	- 【ファイル移動】mv file.txt bbb/
	- 【ディレクトリ移動】mv ccc ../
		- 再帰的に移動する場合は「mv」コマンドではできない。「cp」と「rm」を使って移動する必要あり。
	- 【リネーム1】rename \_o .o fort.33\*
	- 【リネーム2】rename s/\_o/.o/g fort.33\*
	- 【★】size
	
	- 【ファイルコピー1】cp file.txt aaa/file2.txt
	- 【ファイルコピー2】cp file.txt aaa/
	- 【ディレクトリコピー(再帰的)】 cp -r orgdir/ trgtdir/
		- cd オプション
			- 【ディレクトリ以下を再帰的にコピー(由来: recursive)】-r
			- 【確認無しで強制コピー(由来: force)】-f
			- 【コピー前後でパーミッションを保持(由来: permission)】-p
	- 【[ファイルコピー(ブロック単位)](https://news.mynavi.jp/article/20180706-659745/)】dd if=/dev/コピー元デバイスファイル of=/dev/コピー先デバイスファイル
	- 【ファイルコピー＆アクセス権設定】install sourcefile destfile
	
	- 【ファイル分割(行番号指定)】split
	- 【ファイル分割(文脈指定)】csplit
	
	- 【文字コード変換(sjis→utf8)(iconv)】iconv -f sjis -t utf8 shiftjis.txt | less
	- 【文字コード変換(sjis→utf8)([nkf](https://www.atmarkit.co.jp/ait/articles/1609/29/news016.html))】nkf -Sw shiftjis.txt > utf8.txt
	
	- 【改行コード変換(Mac→Unix)】tr \\\\r \\\\n <mac.txt >unix.txt
	- 【改行コード変換(Windows→Unix)】tr -d \\\\r <windows.txt >unix.txt
	- 【改行コード変換(Unix→Windows)】perl -p -e 's/\\n/\\r\\n/' <unix.txt >windows.txt
	- 【改行コード変換(xxx→Windows)】nkf -c xxx.txt > windows.txt
	- 【改行コード変換(xxx→Unix)】nkf -d xxx.txt > unix.txt
	- 【改行コード変換(xxx→Mac)】nkf -Lmm xxx.txt > mac.txt
	
	- 【ハードリンク作成】ln aaa/trgtfile.txt ./lnkfile
	- 【シンボリックリンク作成】ln -s mydir/trgtfile.txt ./lnkfile
	- 【リンク指示先表示】readlink ./lnkfile
	- 【リンク指示先表示(シンボリックリンク解決済み絶対パス)】readlink -f \_lib
	- 【リンクファイル削除】unlink ./lnkfile
	
	- 【データを印刷できる形式に変換】base64
	- 【データを印刷できる形式に変換】base32
	- 【データを印刷できる形式に変換】basenc
		- [BASE64とは](https://qiita.com/PlanetMeron/items/2905e2d0aa7fe46a36d4)
			- すべてのデータをアルファベット(a~z, A~z)と数字(0~9)、一部の記号(+,/)の64文字で表すエンコード方式
	
	- 【テキストファイル 折り返し】fmt
	- 【テキストファイル 折り返し(強制)】fold
	- 【テキストファイル ヘッダフッタ付与】pr
	
	- 【タイムスタンプ更新(現在時刻)】touch file
	- 【タイムスタンプ更新(指定時刻)】touch -d "2016-9-20 20:30" file
	
	- 【タブ→空白変換(8文字)】expand -t 8 file
	- 【空白→タブ変換(8文字)】unexpand -t 8 file
	
	- 【ファイルパーミッション変更】chmod 755 \*.sh
		- 755のように数字を3つ並べるのは次の3つを指定している
			- [所有者に対する権限][所有グループに対する権限][その他に対する権限]
		- 数字の意味は次の通り
			- 0: 権限なし
			- 1: 実行権限
			- 2: 書き込み権限
			- 4: 読み込み権限
				- (7=1+2+4で全部OK, 6=2+4で読み書きのみ、といった具合)
		- 755は、"所有者はなんでもできる、他の人は読み書きだけできる"という設定
		- 644は、"所有者は読み書きできる、他の人は読むことだけできる"という設定
	- 【ファイルパーミッション変更】chmod go+w testdata.txt
		- 上記コマンドは、'グループ'と'その他ユーザ'に'書き込み'権限を与えるコマンド
	- 【ファイルパーミッション変更(再帰的)】chmod -R 777 .
	
	- 【一時的空ファイル/ディレクトリ作成】mktemp
	
	- 【圧縮】tar -czvf xxx.tgz file1 file2 dir1
	- 【展開】tar -xzvf xxx.tgz
		- c(create):新規作成 x(extract):展開 z:gzip形式圧縮 v:ファイル一覧表示 f:ファイル名指定
	
	- 【ファイルサイズ増減】truncate
		- 10MBの空ファイル作成するとかが可能
	
	- 【差分ファイル作成】diff -u file\_old file\_new > hoge.patch
	- 【差分適用(単一ファイル指定)】patch -u file\_path < hoge.patch
	- 【差分適用(フォルダ配下全て)】patch -p0 < hoge.patch
	- 【差分巻き戻し】patch -R file\_path < hoge.patch
		- -u：差分をunified形式のコンテキストdiffとして解釈
		- -R：新旧のファイルが反転していると見なす
	
	- 【インデント調整】indent a.c

- ファイル情報表示
	- 【現在ディレクトリパス表示】pwd
	- 【現在ディレクトリパス表示(実パス表示(デフォルト挙動))】pwd -P
	- 【現在ディレクトリパス表示(シンボリックリンクパス経由)】pwd -L
	
	- 【ファイル/ディレクトリ一覧表示】ls
	- 【ファイル/ディレクトリ一覧表示(隠しファイル/詳細情報含む)】ls -al
	- 【ディレクトリ一覧出力1★】dir
	- 【ディレクトリ一覧出力2★】ls -C -b
	- 【ディレクトリ一覧出力1★】vdir
	- 【ディレクトリ一覧出力2★】ls -l -b
		- lsオプション
			- 【タイムスタンプ順表示(由来:time)】-t
			- 【隠しファイル表示(由来:all)】-a
			- 【隠しファイル表示(.と..を除く)(由来:all)】-A
			- 【詳細情報表示(由来:list?)】-l
			- 【サイズ単位(M(メガ),G(ギガ)等)付与(由来:human readable)】-h
			- 【常時リスト複数列表示】-C
			- 【ファイル識別子付与】-F
			- 【非ソート表示(表示速度軽減)】-f
			- 【ディレクトリ自体の情報表示】-d dir
			- 【再帰的ディレクトリ内表示】-R
			- 【ソート＠逆順(由来:reverse)】-r
			- 【ソート＠拡張子毎】-X
			- 【ソート＠ファイルサイズ順】-S
			- 【ソート＠更新時間順】-t
			- 【★】-b
		- [ls --color 時の色意味](https://www.mm2d.net/main/prog/linux/ls-08.html)
	
	- 【ファイル中身表示】cat ~/.bash\_history
	- 【ファイル中身表示(反転)】tac ~/.bash\_history
	- 【ファイル中身表示(行番号付)(number line)】nl ~/.bash\_history
	- 【ファイル中身表示(バイナリ表示)】od ~/.bash\_history
	- 【ファイル中身表示(1画面ずつ)】more filename
	- 【ファイル中身表示(1画面ずつ)】less filename
		- Vimキーバインドが使えるlessがオススメ！
	- 【ファイル中身表示(一部先頭)】head -n 5 ~/.bash\_history
	- 【ファイル中身表示(一部末尾)】tail -n 5 ~/.bash\_history
	- 【ファイル中身表示(更新)】tail -f ~/.bash\_history
		- tail応用例：
			- tail -n1 \*/{comp,run}\*.log
				- フォルダ配下にあるファイル名「comp*.log」もしくは「run*.log」の末尾1行を順に表示する。
	
	- 【ファイル中身表示(ソート)】sort
	- 【ファイル中身表示(シャッフル)】shuf
	- 【ファイル中身表示(重複削除)】uniq
	- 【ファイル中身表示(前後関係指定ソート)】tsort
	
	- 【ファイル中身表示(垂直抽出)】cut -c 1-5 test.txt #1～5文字目を取出す
	- 【ファイル中身表示(垂直抽出)】cut -d: -f 5 test.txt #区切り文字を「:」として、第5フィールドのみ切り出す
	- 【ファイル中身表示(列結合)】paste -d"," date1.txt date2.txt #「data1.txt」と「data2.txt」を、区切り文字「,」として列結合
	- 【ファイル中身表示(差異比較列結合)】join -j 1 data1.txt data2.txt #「data1.txt」と「data2.txt」の第1フィールドに基づいて列結合
	
	- 【テキストファイル 行数 表示(word count)】wc -l file
	- 【テキストファイル 単語数 表示】wc -w file
	- 【テキストファイル バイト数(文字数) 表示】wc -c data
	
	- 【[ファイル比較](https://qiita.com/mumian1014/items/bb71b0520e457f3b2466)】comm file1 file2
	- 【ファイル比較(バイナリ比較)】cmp file1 file2
	- 【ファイル比較(テキスト比較)】diff --color file1 file2
	- 【ファイル比較(左右並列表示)】sdiff file1 file2
	- 【[ファイル比較(3ファイル)](https://linuxcommand.net/diff3/)】diff3 TRGTFILE OLDFILE NEWFILE
	
	- 【ディレクトリ比較(再帰的)】diff -r --color=always dir1 dir2
	
	- 【ファイル一覧表示(再帰的)】find dirpath -type f
	- 【ファイル一覧表示(再帰的)(ファイル指定)】find dirpath -type f \| grep .md
	- 【ファイル一覧表示(再帰的)(ファイル指定)】find dirpath -name '\*.md' -type f
	- 【ディレクトリ一覧表示(再帰的)】find dirpath -type d
	- 【ファイル/ディレクトリ一覧表示(再帰的)】find dirpath
	- 【ファイル/ディレクトリ検索】上記のfindコマンドを用いる
	- 【ファイルツリー出力】tree -C -N dirpath
		- -C:常に色付きで表示、-N:表示不可文字8進数表示
	- 【ファイル種別表示】file filename
	- 【リンク切れシンボリックリンク一覧表示(再帰的)】find dirpath -xtype l
	
	- 【ファイル数出力(フォルダ配下すべて)】find . -type f | wc -l
	- 【ファイル数出力(フォルダ内のみ)】find . -maxdepth 1 -type f | wc -l
	
	- 【ファイル名抽出(拡張子含む)】basename aaa/bbb/test.txt #→test.txt
	- 【ディレクトリパス抽出】dirname aaa/bbb/test.txt #→aaa/bbb
	- 【ファイルパス移植性確認】pathchk aaa/bbb/test.txt
		- 以下の場合にエラーを吐くコマンド
			- パーミッションの関係でディレクトリの中身が見れない
			- ファイル名長すぎ
	- 【相対パス→絶対パス変換】realpath
	
	- 【高速ファイル/ディレクトリ検索】locate "\*.txt"
		- locateコマンドは、事前に「updatedb」コマンドにてインデックスを作成しておく必要あり。
	
	- 【文章から索引作成】ptx
	
	- 【ls用色設定コマンド出力】dircolors
	
	- 【16bitチェックサム＆ブロック数(1024Byte単位) 表示】sum
	- 【CRCチェックサム 表示】cksum
	- 【BLAKE22ハッシュ値 表示】b2sum
	- 【128bitチェックサム表示】md5sum
		- →バイナリの一致確認時に使用する
	
	- 【[SHA-1](https://ja.wikipedia.org/wiki/SHA-1)ダイジェスト計算】sha1sum
	- 【SHAダイジェスト計算(xxxビット長)】shaXXXsum
	
	- 【Grep】 `grep -nr 'const' /mnt/c/codes\_sample/c/FreeRTOSV7.1.1/Source --include='*.[ch]' >> grep_result.txt`
		- 主な grep オプション（[詳細はこちら](https://www.atmarkit.co.jp/ait/articles/1604/07/news018.html)）
			- 【検索パターン指定(複数条件検索時)】-e 検索パターン
			- 【大/小文字区別なし】-i
			- 【単語単位検索】-w
			- 【不一致行表示】-v
			- 【エラーメッセージ表示】-s
			- 【基本正規表現】-G
			- 【拡張正規表現】-E
			- 【行番号表示】-n
			- 【ファイル名表示】-H
			- 【ファイル名非表示（複数ファイル指定時）】-h
			- 【一致カラム表示】-b
			- 【一致文字列ハイライト】\-\-color=WHEN # WHEN=\(always|never|auto\)
			- 【一致行 前行表示】-B 行数
			- 【一致行 後行表示】-A 行数
			- 【一致行 前後行表示】-C 行数,-行数
			- 【検索対象にディレクトリを指定した場合の動作】-d ACTION # ACTION=(read|recurse|skip)
			- 【サブディレクトリ配下ファイル対象】-r
			- 【サブディレクトリ配下ファイル対象(シンボリックリンク含む)】-R
			- 【パターンマッチファイル対象追加】--include='\*.c'
			- 【パターンマッチファイル対象除外】--exclude='\*.o'
			- 【結果非表示（主にシェルスクリプトなどで判定用に使う）】-q
	
	- 【Grep置換】grep -l "Dim" \*.vbs | xargs sed -i "s/Dim/Dims/g"
	
	- 【数値単位変換1】numfmt --from=auto 1Mi #→1048576
	- 【数値単位変換2】numfmt --to=si 500000 #→500K

- 文字操作
	- 【文字列置換(文字単位)(translate)】tr
		- 例1）cat data.txt \| tr [:lower:] [:uppder:] #data.txtファイルにある小文字全てを大文字に変更
		- 例2）cat data.txt \| tr 'a-z' 'A-Z' #data.txtファイルにある小文字全てを大文字に変更 
		- 例3）tr -d : < file1 #data.txtファイルにある「：」を削除して表示
	- 【テキスト置換】echo "Hello World" | sed 's/Hello/Welcome/g'
	- 【テキスト置換(ファイル対象)】sed -i -e 's/Wolrd/World/' targetfile.txt
	- 【テキスト追加(5行目)】sed 5a addstring
	- 【テキスト削除(10行目)】sed 15d
	- 【ファイル書換＆元ファイル.bak化】sed -i.bak
	- 【ソート＆重複削除】cat file1 \| sort \| uniq
	- 【数字列出力】seq

- システム
	- 【フォルダ使用容量表示(disk usage)】du -h -d 1
	- 【ディスク空き容量表示(disk free)】df -h
	- 【ディレクトリサイズ表示(disk usage)】du -h
	- 【メモリ使用状況表示】free
	- 【CPU/メモリ使用状況確認】top
	- 【ファイル作成/更新日時表示】stat file
	- 【ファイル作成/更新日時表示(リンク先情報)】stat -L lnkfile
	- 【ファイル作成/更新日時表示(ファイルシステム情報)】stat -f file
	- 【実行中ジョブ確認】jobs
	
	- 【プロセス情報表示(全プロセス)】ps -ef
	- 【プロセス情報表示(現在プロセス)】ps $$
	- 【プロセス情報表示(ツリー表示)】pstree
	- 【プロセス停止】kill jobno
	- 【[キャッシュ内未処理データディスク書込み](https://linuc.org/study/knowledge/413/)】sync
	- 【端末行設定表示】stty
	- 【標準入力ターミナルファイルパス表示】tty
	
	- 【ユーザID表示】id
	- 【現在ログイン名表示】logname
	- 【現在ユーザIDに関連付けされているユーザ名表示】whoami
		- id -un と同等
	- 【所属グループ名表示】groups
	- 【ログインユーザ一覧表示】users
	- 【ログオン中ユーザ情報表示】who
	
	- 【ユーザアカウント作成】useradd -d /home/mike -s /bin/bash mike
		- 「mike」という新規ユーザを作成し、ホームディレクトリ、ログインシェルを指定する設定
	- 【ユーザアカウント変更(グループ変更)】usermod -g sales mike
	- 【ユーザアカウント削除】userdel -r mike
	- 【グループアカウント作成】groupadd sales
	- 【グループアカウント変更】groupmod -n salesmarketing sales
	- 【グループアカウント削除】groupdel sales
	- 【所属グループ表示】id sales
	- 【ログインパスワード変更】passwd mike
	- 【ログインシェル変更】chsh -s /bin/bash mike #mikeのログインシェルをbashに変更する
	
	- 【環境変数表示】printenv
	- 【環境変数設定(csh系用)】setenv envvar value
	- 【環境変数設定(sh系用)】export envvar='value'
	- 【環境変数変更(一時的)】env
	- 【環境変数表示】env
	
	- 【マウント】mount /dev/sda1 /mnt/hdd1
		- マウント…記憶媒体に対して読み書きを可能にすること
	- 【アンマウント】umount /mnt/hdd1
	- 【マウント状況確認】df -k
	- 【デバイス一覧表示】fdisk -l
	
	- 【時刻(システムクロック)表示】date
	- 【時刻(システムクロック)変更】date 11132330 #→11/13 23:30にセット
	- 【時刻(ハードウェアクロック)変更】hwclock -w #システムクロックの時刻をハードウェアクロックに反映
	
	- 【プロセッサ数表示】nproc
	- 【システム情報表示】uname
	- 【ハードウェア名表示】arch
	- 【ホスト名表示】hostmname
	- 【ホスト識別子表示(16進数)】hostid
	- 【システム起動時間等表示】uptime

- 他
	- 【[名前付きパイプ作成](https://linuxcommand.net/mkfifo/)】mkfifo
	- 【[特殊ファイル作成](https://manual.atmark-techno.com/armadillo-guide/armadillo-guide-2_ja-1.0.0/ch03.html)】mknod
	
	- 【ネットワーク切断】sudo ifconfig wlan0 down
	- 【ネットワーク接続】sudo ifconfig wlan0 up
	- 【ネットワーク状況確認】sudo ifconfig wlan0
	
	- 【マニュアル確認】man wpa\_supplicant.conf
	
	- 【[awk](https://www.tohoho-web.com/ex/awk.html)】
		- 【出力】awk '{print $2,$4}' #空白区切りで2番めと4番めの部分を出力
		- 【数値判定】awk '$5>=100{print $2,$4}' #5番めが100以上なら2番めと4番めを出力
		- 【文字列判定】awk '$9=="hello.awk" { print $3, $4, $9 }'
		- 【区切り文字指定】awk -F: '{ print $1, $6 }' #区切り文字を:として1列目、6列目
		- 【スクリプト実行】awk -f #awk用のコマンドが書かれたファイルに従って処理を行う
		- 【パターンマッチ】awk '/World/ { print $1 }' # レコードの中にABCという文字列が含まれていればマッチ
		- 【パターンマッチ】awk $1 ~ /^#/ { ... } # 第1フィールド先頭が#で始まっていたらマッチ
	
	- 【カレンダー表示】cal
	
	- 【URLコンテンツ取得(Client for URL)】curl https://draemonash2.github.io/sft\_linux/linux.html
	- 【URLコンテンツ取得(ファイルダウンロード)】curl -OL https://github.com/draemonash2/codes/raw/master/vim/\_vimrc
	
	- 【TCP/IPアドレス情報表示】ifconfig
	- 【パケット送付】ping 宛先
	- 【★】chcon
	- 【★】runcon
	- 【特定ルートディレクトリでコマンド実行】chroot
	
	- 【バッファリングモード変更＆コマンド実行】stdbuf
	- 【素因数分解】factor 60 #→60: 2 2 3 5
	
	- 【make(デフォルトターゲット指定)】make
	- 【make(ターゲット指定)】make trgt
	- 【make(メイクファイル指定)】make -f file
	- 【make(標準入力指定)】make -f- file
	- 【make(エラー無視)】make -k
	- 【make(コマンド出力のみ)】make -n
	
	- 【[bash動作設定(シェルオプション)](https://www.atmarkit.co.jp/ait/articles/1912/12/news034.html)】shopt
		- shopt -s nullglob    # 不一致globsを除去する ('*.foo' => '')
		- shopt -s failglob    # 不一致globsはエラーにする
		- shopt -s nocaseglob  # globsの大文字小文字を区別しない
		- shopt -s dotglob     # dotfilesもワイルドカードにマッチさせる ("*.sh" => ".foo.sh")
		- shopt -s globstar    # 「**」を再帰マッチにする ('lib/**/*.rb' => 'lib/a/b/c.rb')
	
	- 【現在のシェル表示】echo $SHELL
	
	- 【SCP転送】scp a.txt username@127.0.0.1:/home/user
	- 【SCP転送(パスワード自動入力)】expect -c "spawn scp sendfile.txt username@127.0.0.1:/home/user ; expect password: ; send passwd\r ; expect $ ; exit"
		- 127.0.0.1に対して、ユーザ名：username、パスワード：passwdでsshログインした後、sendfile.txtを「/home/user」にSCP転送する。
	
	- 【[シンボル情報表示](http://doi-t.hatenablog.com/entry/2014/01/31/084213)】nm hello.o
	
	- 【書庫インデックス作成】ranlib libgraphics.a
	- 【アーカイブファイル作成】ar qc libgraphics.a \*.o
		- GNU ranlib プログラムは GNU ar の別名である。ranlib を実行するのと ` ar -s 'とは完全に等価である。
		- 操作オプション
			- r：メンバ追加
			- d：メンバ削除
			- q：メンバ追加(アーカイブ末尾)
		- 修飾子オプション
			- c：アーカイブ作成

- [各種ツール](https://i.loveruby.net/ja/misc/readingcode.html)
	- gonzui
		- 様々な言語に対応しているソースコード検索エンジン。 ファイル内のインクリメンタル検索、ソースブラウズなどが可能。
	- global
		- GNU global。ctagsの強化版？
		- C 言語用。 クロスリファレンス、関数定義元の検索など、高機能。 同梱ツール htags を使うと HTML で出力できる。
		- 不満なところ。グローバル変数と関数ポインタについても定義元を 示してほしい。
		- あと htags で HTML を出力するとき予約語にタグを つけたりできるんだけども、ここでタグを直接出力するのではなく CSS を使って指定できるようにしてほしい。
		- 手元ではそのように 改造して使っている。グローバルに定義されている文字列定数を 書き変えるだけで変更できた。(ただし CSS 名は決め打ち)
		- さらに言えばマクロの中で定義された関数とかローカル変数まで カバーしてくれると完璧なのだが、そこまでやるとほとんど C コンパイラと同じかそれ以上の解析が必要になってしまうので 無理は言わないことにする。
	- cscope
		- 対話形式によるC言語プログラムを検査するツールです。
		- ソースコード全体から、関数や変数の定義場所を検索／移動（タグジャンプ）することや、関数の参照先一覧を表示することができます。
		- 手作業でgrepコマンドを実行するよりも効率的に検索することが可能になります。 
		- cscopeのシンボル系検索機能は以下のことが可能です。
			- シンボルの検索（宣言／定義／参照）
			- 定義位置の検索（定義が検索対象
			- 呼び出し先の検索（指定関数から呼び出されている関数の一覧）
			- 呼び出し元の検索（指定関数を呼び出している関数の一覧）
			- 文字列の検索（シンボル検索での検索対象に加えてコメント記述等を対象に検索）
			- egrep での検索（正規表現）
		- C/C++/Java 用。 Curses ベースのソースコードビューア。独自コマンド体系なのが どうも面倒くさい。
		- そういうわけであんまり真面目に使ってないが、機能はかなり豊富だ。 global より cscope のほうが便利という人も多いようである。
	- lxr
		- Linux のソースコード読みを支援するために開発されたツール。 名前は Linux Cross Referencer から来ている。CGI として使うもの。
		- スタンドアロンツールが欲しかったのであまり真面目に使わなかったが、 これはこれでなかなか便利そうだ。
	- cxref
		- C cross referencing & Documentation tool、の名前のとおり クロスリファレンスとドキュメント生成のためのツール。それ用の コメントを付けとかないとドキュメントは生成されない。
		- 基本的には これはドキュメント生成のツールであって、クロスリファレンスは そのオマケみたいなもの。
		- ソース読みが目的なら上記のどれかを使うほうがいい。
	- cflow
		- 昔から UNIX に付いてるツール。 C 言語の関数の呼び出し関係をテキストで表示してくれる。
		- 今となってはメチャクチャ便利というものではないが、 シンプルだし、パイプへの出力に使えるので持ってて損はない。

# Tips
- [「E: Unable to locate package」エラー解消法＠Ubuntu](https://qiita.com/hatorijobs/items/c503840c13672e12d188)
	- `apt update` を実行する
		- `sudo apt-get update`
- コマンドインストール方法
	- `sudo apt install <command>`
- [ホームディレクトリパス変更](https://qiita.com/funacchi/items/c3bb78a546cf2605205d)
	1. `sudo vim /etc/passwd`を実行
		- [/etc/passwdについてはこちら](https://www.server-memo.net/centos-settings/system/passwd_shadow.html)
	1. ユーザ名の行を探し、"/home/xxx"を"変えたいディレクトリ"に変更
- [「.tar.gz」とは](https://wa3.i-3-i.info/word12942.html)
	- 複数ファイルを1つにまとめたファイル（tarファイル）をgzipコマンドで圧縮したファイル
- 起動時にエイリアスを設定したい
	1. 「~/.bashrc」に起動時に設定したいエイリアスを設定しておく
- 共有PCにおける自分用ホームディレクトリ設定＆運用方法
	1. 起動時に実行される「~/.bashrc」に以下のエイリアスを設定しておく
		- `alias endo='export HOME=/home/dir'`
	1. bash起動時に 'endo' を実行する
- 共有PCにおける自分用ホームディレクトリ設定＆運用方法
	1. 起動時に実行される「~/.bashrc」に以下のエイリアスを設定しておく
		- `alias endo='export HOME=/home/dir'`
	1. bash起動時に 'endo' を実行する
- 共有PCにおける自分用vimrc設定＆運用方法
	1. 「共有PCにおける自分用ホームディレクトリ設定＆運用方法」にて設定するホームディレクトリに「.vimrc」を格納する
	1. 「共有PCにおける自分用ホームディレクトリ設定＆運用方法」の手順を実施する
- [Linux操作がうまくなるために](https://qiita.com/chooyan_eng/items/b154d57a8da8911db612)
- [NFSとは](https://baremetal.jp/blog/2018/04/17/541/)
	- Network File Systemの略。
	- ネットワーク上のコンピュータが持つストレージを共有するための仕組み。
	- LinuxをはじめとするUNIX系OSの多くに標準で組み込まれている。
- [SSH基礎](https://iatlex.com/linux/ssh)
- bashの設定ファイル一覧と実行順序
![bash設定ファイル一覧](bash設定ファイル一覧.jpg)
- [「.bash\_profile」と「.bashrc」の違い](https://honmushi.com/2020/03/30/bash-custom/)
	- 相違点
		- .bash\_profile … ログイン時に1回だけ実行
		- .bashrc … シェルを起動する度に実行
	- 備考
		- 一般的な設定は特に理由がなければ.bashrc の方に書けば問題ない。
- [シェル、ターミナル、コンソール、コマンドラインの違い](https://qiita.com/tadsan/items/441dcd910537d3f408e5)
- 共有アカウントにおけるホームディレクトリ変更
	1. 事前準備
		1. 以下を共有アカウントの設定ファイル「~/.bashrc」に追記
			- `alias he='export HOME=/home/draemon_ash3/;cd ~;source ./.bashrc;pwd;'`
		1. 個人アカウントの設定ファイル「/home/<user_name>/.bashrc」に自分の設定を追加する
			- ※「/etc/passwd」のパスは書き換えないようにする！
	1. ログオン直後
		1. コマンド「he」を実行する
- [ファイル種別](https://qiita.com/angel_p_57/items/1faafa275525469788b4)
	- レギュラーファイル -
	- ディレクトリ d
	- シンボリックリンク l
	- ブロックデバイスファイル b
	- キャラクタデバイスファイル c
	- パイプ p
	- ソケット s
- [CentOSをインストールする](https://www.geekfeed.co.jp/geekblog/install_centos8_on_wsl2_for_free)
- [GDBの使い方はこちら](../sft_gdb/gdb.md)
- alias rm='rm -i'は避けた方がいい
	- エイリアスのrm -iが定義されてない環境で事故を起こす危険があるから。やるなら、rmとは違う名前で定義すべき。それなら、未定義の環境では コマンドが無いエラーで済む。
- ブレース展開を用いたバックアップファイルの作成
	- cp file.txt{,.bk}
- [紛らわしいけど重大な違いを引き起こすリダイレクト](https://zariganitosh.hatenablog.jp/entry/20110623/redirect_command)
- bashのPS1で使える特殊文字
	- プロンプトの色を変更するには \e[太さ;色番号m、元に戻すには \e[m を、\[ ... \] で挟んで指定します。
	- 太さは 0 が通常、1 が太字、色は、黒(30)、赤(31)、緑(32)、黄色(33)、青(34)、マジェンダ(35)、シアン(36)、灰色(37)、白(97) などを指定できます。
	- 特殊文字は以下の通り。
	
		|特殊文字|説明|
		|:---|:---|
		| \a		| ビープ音を鳴らす |
		| \A		| 24時間表記の時分(例:23:59) |
		| \e		| エスケープ文字(ESC) |
		| \d		| 曜日 月 日(例:Sun May 24) |
		| \D{fmt}	| %Y/%m/%d %H:%M:%S などのフォーマットで日時を指定 |
		| \h		| ホスト名(例:msv02) |
		| \H		| ホスト名(例:msv02.example.com) |
		| \j		| バックグランドジョブの個数(例:2) |
		| \l		| ターミナル(例:/dev/pts/2)の最後のファイル名(例:2) |
		| \n		| 改行 |
		| \r		| キャリッジリターン |
		| \s		| シェルの名前(例:bash) |
		| \t		| 24時間表記の時刻(例:23:59:59) |
		| \T		| 12時間表記の時刻(例:11:59:59) |
		| \@		| AM/PM付き12時間表記の時分(例:11:59 PM) |
		| \u		| ユーザー名(例:tanaka) |
		| \v		| bashのバージョン(例:4.2) |
		| \V		| bashのバージョン(例:4.2.46) |
		| \w		| カレントディレクトリ(例:~/bin) |
		| \W		| カレントディレクトリ(例:bin) |
		| \#		| 現在のセッションにおけるヒストリ番号(例:21) |
		| \\!		| ヒストリ番号(例:423) |
		| \\$		| ルート権限の場合は #、一般権限の場合は $ |
		| \nnn		| 8進数での文字コード |
		| \\\\		| バックスラッシュそのもの |
		| \\[		| 非表示文字の開始 |
		| \\]		| 非表示文字の終了 |
	
- export 動作実験
```
$ cat test.sh
#!/bin/sh

echo === called test.sh ===

echo echo ENDOENV1:$ENDOENV1
echo echo ENDOENV2:$ENDOENV2
echo echo ENDOENV3:$ENDOENV3

export ENDOENV1=aaa

./test2.sh

echo echo ENDOENV1:$ENDOENV1
echo echo ENDOENV2:$ENDOENV2
echo echo ENDOENV3:$ENDOENV3

$ cat test2.sh
#!/bin/sh

echo === called test2.sh ===

echo echo ENDOENV1:$ENDOENV1
echo echo ENDOENV2:$ENDOENV2
echo echo ENDOENV3:$ENDOENV3

export ENDOENV1=bbb
export ENDOENV2=11
ENDOENV3=uuuu

echo echo ENDOENV1=$ENDOENV1
echo echo ENDOENV2=$ENDOENV2
echo echo ENDOENV3=$ENDOENV3


$ export ENDOENV1=init1

$ ENDOENV2=init2

$ ./test.sh
=== called test.sh ===
echo ENDOENV1:init1
echo ENDOENV2:
echo ENDOENV3:
=== called test2.sh ===
echo ENDOENV1:aaa
echo ENDOENV2:
echo ENDOENV3:
echo ENDOENV1=bbb
echo ENDOENV2=11
echo ENDOENV3=uuuu
echo ENDOENV1:aaa
echo ENDOENV2:
echo ENDOENV3:

$ echo $ENDOENV1
init1

$ echo $ENDOENV2
init2
```

# ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||Tab|コマンド/ファイル名補完|
|Ctrl|||p/n|コマンド履歴呼出し(1つ前/1つ先)|
|Ctrl|||r|コマンド履歴検索|
|Ctrl|||l|画面クリア|
|Ctrl|Shift||f|検索|
|Ctrl|||c|実行中プログラム強制終了|
|Ctrl|||d|終了|
|Ctrl|||f/b|カーソル移動(1個右/左)|
|||Alt|f/b|カーソル移動(単語単位右/左)|
|Ctrl|||a/e|カーソル移動(行頭/行末)|
|Ctrl|||t|文字入替(現在⇔1つ前)|
|Ctrl|||h/d|文字削除(カーソル左/カーソル位置)|
|Ctrl/||/Alt|w|単語削除(カーソル左/右)|
|Ctrl|||u/k|文字削除(カーソル左側/右側全て)|
|Ctrl|||y|貼付け（上記Ctrl + w,Ctrl + kなどで削除した文字列をペーストできる）|
|Ctrl|||m/j/o|ENTERと同じ|
||Shift|Alt|+/-|タブ内分割追加(垂直/水平)|
|Ctrl|Shift||w|タブ内分割削除|
|||Alt|方向キー|タブ内分割移動|
||Shift|Alt|方向キー|タブ内分割サイズ変更|
|||Alt|Enter|全画面モード|
||||F11|全画面モード|
|Ctrl|||s/q|画面更新 停止/再開|
|Ctrl|Shift||↑/↓|画面スクロール 上/下（WSL2のみ？）|
|Ctrl|Shift||t|新規タブ作成|
|Ctrl|Shift||d|タブ複製|
|Ctrl|/Shift||Tab|タブ切替え 順方向/逆方向|
|Ctrl|Shift||p|コマンドパレット表示|
|Ctrl|Shift||Space|ドロップダウンメニュー表示|
|Ctrl|||+/-|フォントサイズ変更(拡大/縮小)|

[トップに戻る](../index.md)
