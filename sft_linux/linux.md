[トップに戻る](../index.md)

# 構文

- [コマンド連続実行方法](https://qiita.com/egawa_kun/items/714394609eef6be8e0bf)
	- ； (ex. `コマンド1 ; コマンド2`)
		- コマンド1が終了したらコマンド2を実行する（実行結果に関わらず）
	- ＆ (ex. - 例：`コマンド1 & コマンド2`)
		- バックグラウンドでコマンド1を実行しつつ、コマンド2も実行する
	- ＆＆ (ex. `コマンド1 && コマンド2`)
		- コマンド1が正常終了したらコマンド2を実行する
	- ｜ (ex. `コマンド1 | コマンド2`）
		- コマンド1の結果をコマンド2へ渡して実行する
	- ｜｜ (ex. `コマンド1 || コマンド2`)
		^ コマンド1が異常終了したときのみ、コマンド2が実行される

# コマンド一覧

- ファイル操作
	- 【ファイルリスト表示】ls
	- 【現在フォルダパス表示】pwd
	
	- 【ディレクトリ作成】mkdir /media/pi/DvdDrive
	- 【ディレクトリ削除】rmdir /media/DvdDrive
	
	- 【フォルダ配下コピー＆ペースト】 `cp -r <org_dir>/ <trgt_dir>/`
	
	- 【ファイル分割(行番号指定)】split
	- 【ファイル分割(文脈指定)】csplit
	
	- 【データを印刷できる形式に変換】base64
	- 【データを印刷できる形式に変換】base32
	- 【データを印刷できる形式に変換】basenc
		- [BASE64とは](https://qiita.com/PlanetMeron/items/2905e2d0aa7fe46a36d4)
			- すべてのデータをアルファベット(a~z, A~z)と数字(0~9)、一部の記号(+,/)の64文字で表すエンコード方式
	
	- 【テキストファイル 折り返し】fmt
	- 【テキストファイル 折り返し(強制)】fold
	- 【テキストファイル ヘッダフッタ付与】pr
	
	- 【タブ→空白変換(8文字)】expand
	- 【空白→タブ変換(8文字)】unexpand
	
- ファイル情報表示
	- 【ファイル中身表示】cat
	- 【ファイル中身表示(反転)】tac
	- 【ファイル中身表示(行番号付)】nl
	- 【ファイル中身表示(バイナリ表示)】od
	
	- 【ファイル中身表示(一部先頭)】head
	- 【ファイル中身表示(一部末尾)】tail
	
	- 【テキストファイル行数/単語数/バイト数 表示】wc
	- 【16bitチェックサム＆ブロック数(1024Byte単位) 表示】sum★
	- 【CRCチェックサム 表示】cksum
	- 【BLAKE22ハッシュ値 表示】b2sum★
	- 【128bitチェックサム表示】md5sum
		- →バイナリの一致確認時に使用する
	
	- 【[SHA-1](https://ja.wikipedia.org/wiki/SHA-1)ダイジェスト計算】sha1sum
	- 【SHAダイジェスト計算(xxxビット長)】shaXXXsum

	- 【ファイル中身表示(ソート)】sort
	- 【ファイル中身表示(シャッフル)】shuf
	- 【ファイル中身表示(重複削除)】uniq
	- 【ファイル中身表示(前後関係指定ソート)】tsort

	- 【ファイル中身表示(垂直抽出)】cut
	- 【ファイル中身表示(列結合)】paste
	- 【ファイル中身表示(差異比較列結合)】join
	
	- 【ファイル比較】comm★
	- 【ファイル比較】 `diff --color ZipFile.vbs ZipPasswordFile.vbs`
	
	- 【ファイル/ディレクトリ一覧出力】ls
	- 【ディレクトリ一覧出力】dir
		- `ls -C -b` と同じ
	- 【ディレクトリ一覧出力】vdir
		- `ls -l -b` と同じ
	
	- 【フォルダ配下ファイル＆ディレクトリリスト一覧表示】`find <path>`
	- 【フォルダ配下ファイルリスト一覧表示】`find <path> -type f`
	- 【フォルダ配下ディレクトリ一覧表示】`find <path> -type d`
	- 【ファイルツリー出力】tree
	
	- 【文章から索引作成】ptx★
	
	- 【lsのカラー設定】dircolors★

- 基本操作
	- 【ファイル/ディレクトリコピー】cp
	- 【ファイルコピー＆変換】dd★
	- 【ファイルコピー(属性指定)】install★
	- 【ファイル移動】mv
	- 【ファイル削除】rm
	- 【★】shred

	- 【ハードリンク作成】link
	- 【ファイル間リンク作成★】ln
	- 【ディレクトリ作成】mkdir
	- 【名前付きパイプ作成★】mkfifo
	- 【★】mknod
	- 【シンボリックリンクパス表示】readlink
	- 【リンクファイル削除】unlink
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】

- 文字操作
	- 【文字列置換(文字単位)】tr
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】
	- 【】

- 他
	- 【ネットワーク切断】sudo ifconfig wlan0 down
	- 【ネットワーク接続】sudo ifconfig wlan0 up
	- 【ネットワーク状況確認】sudo ifconfig wlan0
	
	- 【マニュアル確認】man wpa\_supplicant.conf
	
	- 【マウント状況確認】df -k
	- 【マウント】mount /dev/sda1 /mnt/hdd1
	- 【アンマウント】umount /mnt/hdd1
	- 【デバイス一覧表示】fdisk -l
	
	- 【エイリアス設定】alias ll='ls -al'
	
	- 【Grep】grep★
	- 【テキスト処理(文字列置換/抽出/削除等)】sed
	- 【★】awk
		- [sedやgrepのようなテキスト処理ツールに演算機能を持たせた拡張ツール](https://ja.wikipedia.org/wiki/AWK)
	- 【数字列出力】seq
	- 【カレンダー表示】cal

	- 【コマンド結果をクリップボードにコピー】xclip
		- 以下の通りコマンドのインストールが必要。（[詳細はこちら](https://linuxfan.info/xclip)）
			- `sudo apt install -y xclip`
		- →使えない…★

	- 【ファイルパス表示】 `readlink -f _lib`
	- 【ファイルの読み取り専用を解除】 `chmod u-r <file>`
	- 【ファイルの隠しファイルを解除】★
	- 【ショートカットファイルを作成】★
	- 【シンボリックリンクを作成】★
	- 【圧縮】★
	- 【解凍】★
	- 【ファイル切り取り＆ペースト】mv
	- 【テキストファイル作成】`touch <file>`
	- 【コンテンツ取得(fromHTTP)】curl

# VIM 設定

★

# Tips
- [「E: Unable to locate package」エラー解消法＠Ubuntu](https://qiita.com/hatorijobs/items/c503840c13672e12d188)
	- `apt update` を実行する
- コマンドインストール方法
	- `sudo apt install <command>`


[トップに戻る](../index.md)
