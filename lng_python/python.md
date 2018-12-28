[トップに戻る](../index.md)

# ToDo
- iTunes プレイリスト エクスポート

# 実行方法
- 以下コマンド実行
    ``` python 
    python test01.py
    ```

# Tips
- 基本構文例
    ``` python 
    def add(x, y):
        ans = x + y
        return ans
    n = add(3, 5)
    print n #=> 8
    ```
- ブロック構造に中カッコを用いず、インデントでのブロック構造となっている。
- 何もしない処理
    - 何もしない処理は、以下のように記述する。（これがないとインデントによるブロック構造の為、エラーが発生してしまう）
    ``` python 
    if value == 0:
        pass
    else
        test = "test!"
    ```
- 複数行にわたるコメントアウト
    - 基本的にはできない。
    - ただし、ダブルクオーテーション×３で代用可能。
    ``` python 
    #    複数行のコメントアウト例
    '''
    print "test 3"
    print "test 4"
    '''
    ```
- 文字列中のエスケープ
    - 文字列中のエスケープは"\"でできる
        - 例１）print "1234\"567890" ⇒ 1234"567890
        - 例２）print "1234'567890" ⇒ 1234'567890
        - 例３）print '1234"567890' ⇒ 1234"567890
        - 例４）print "1234\\567890" ⇒ 1234\567890
        - 例５）print "1234\n567890" ⇒ 1234（改行）567890
        - 例６）print "1234\t567890" ⇒ 1234（タブ）567890
- 変数配列＝リスト
- 定数配列＝タプル
- インクルード＝インポート
    - インポートはどの行に書いても問題なし
- ★ディクショナリについて
- 「if \_\_name\_\_ == "\_\_main\_\_":」について
    - \_\_name\_\_ はメインプログラムとして実行中は" \_\_main\_\_" をセットする。ファイルが他のモジュールからインポートされている場合は、\_\_name\_\_には、そのモジュール名が入る。
    - すなわち「if \_\_name\_\_ == "\_\_main\_\_":」は、他のモジュールからインポート時は実行せず、メインプログラムとしての実行時は処理を行う。ということ。
- 関数の戻り値、複数可
    ``` python 
    def func():
        return 3, "ABC"
    n, s = func()
    ```
- 「# -\*- coding: utf8 -\*-」とした場合、全角文字は使用できない。
- 文字列の表現 '...'(シングルクォーテーション)と"..."(ダブルクォーテーション)の違い
    - Python は言語仕様上、'...'と"..."に違いはない。
    - ちなみに Perl / Ruby / PHP は二つの文字列を区別しており、ダブルクォーテーションの場合文字列内の特殊文字や変数などを置換、シングルクォーテーションの場合は置換をせずそのまま出力する。
- lambda について
    - defステートメントのように関数を作成する際に使用するもの。defステートメントとは違い「式」。よってdefステートメントでは記述できない場所に記述することが可能。
    ``` python 
    func = lambda x,y=10,z=30: x + y + z  
    func(x=1) '⇒ 41
    ```

# 構文
- 【変数/配列定義】なし
- 【定数定義】なし
- 【構造体定義】なし（クラスで代用可能っぽい）
- 【関数定義】def func( num\_1, num\_2, operation=1): ～ return value # operation は省略可能。（初期値は1）
- 【関数呼出】value = func(1, 2)
- 【マクロ定義】なし
- 【列挙型定義】なし（Python3.4 から追加されたっぽい）
- 【ブロック脱出（Sub/Function/For/Do）】break

- 【エンコード宣言（Shift-JIS）】# -\*- coding: cp932 -\*-
- 【エンコード宣言（UTF-8）】# -\*- coding: utf8 -\*-
- 【インタプリタパス指定】#! /usr/bin/python
- 【import】import testmod

- 【if】if value == 1: ～ elif value == 2: ～ else: ～
- 【switch】なし
- 【for（要素取出）】for value in for\_sample: ～ # vba の for each と同じ
- 【for（要素数取出）】for i in range( len( list ) ): ～ # list 要素数分繰り返し
- 【while】while 条件式 : ～ (真の場合) ～
- 【break】break
- 【continue】continue
- 【コメント】#
- 【出力①】print "python"
- 【出力②】print u"サイト開設 %d 日目！ %s" % (test\_int,test\_str) # 出力結果「サイト開設 200 日目！ python-izm.com」
- 【入力①】answer = input( "please input >>" ) '数値入力のみ対応。戻り値は数値型。
- 【入力②】answer = raw\_input( "please input >>" ) '数値、文字列の入力に対応。戻り値は文字列型。
- 【アサート】assert a == 4

- 【条件式 and】if value\_1 == "python" and value\_2 == "izm":
- 【条件式 or】if value\_1 == "python" or value\_2 == "izm":
- 【条件式 not】if not value\_1 == "python":

- 【四則演算（加算）】10 + 10
- 【四則演算（減算）】10 - 10
- 【四則演算（乗算）】10 \* 10
- 【四則演算（除算）】10 / 10
- 【インクリメント】test\_num += 1
- 【デクリメント】test\_num -= 1

- 【文字列記載】print "python-izm" # シングルクオーテーションでも可
- 【エスケープ無視】print r"C:\targetdir\sample.txt" # 「r」によりパス区切りの \ のエスケープが不要となる
- 【複数行に渡る文字列】test\_str =  """ ～ test\_1 ～ test\_2 ～ """ # test\_1 と test\_2 の間に改行が入る
- 【文字列 検索１】test\_str.find("a", 1) # "abcd" ⇒ 1（見つからない場合は「-1」が返される）
- 【文字列 検索２】"bc" in test\_str # "abcd" ⇒ True
- 【文字列 置換】test\_str.replace("izm","ism")
- 【文字列 分割】test\_str.split("-")
- 【文字列 結合】test\_str = test\_str + "python"
- 【文字列 大文字化】test\_str.upper()
- 【文字列 小文字化】test\_str.lower()
- 【文字列 文字埋込】test\_str.rjust(10,"!") # "1234" ⇒ "!!!!!!1234"
- 【文字列 ０埋込】test\_str.zfill(10) # "1234" ⇒ "0000001234"
- 【文字列 長】len(test\_str) # "ABCDE" ⇒ 5
- 【文字列 抽出①】print test\_str[0] # "ABCDE" ⇒ "A"
- 【文字列 抽出②】print test\_str[2] # "ABCDE" ⇒ "C"
- 【文字列 抽出（左）】print test\_str[:3]  # "ABCDE" ⇒ "ABC"
- 【文字列 抽出（中）】print test\_str[1:3] # "ABCDE" ⇒ "BC"
- 【文字列 抽出（右）】print test\_str[2:]  # "ABCDE" ⇒ "CDE"

- 【文字列⇒Ascii 変換】hex(ord(u"あ")) # 0x3042
- 【Ascii⇒文字列変換】chr(97) # 'a'
- 【10⇒16進数変換】hex(29) # '0x1d'
- 【16⇒10進数変換】int('0x1d', 16) # 29
- 【文字列⇒数値 変換】int("1234") # 1234
- 【数値⇒文字列 変換】str(1234) # "1234"
- 【改行】'\n' | '\r'
- 【正規表現】★

- list = ['1','2','3','2','1'] とすると…
    - 【リスト 参照】list[0] # '1' （0 オリジン）
    - 【リスト 削除】list.remove('2') # list = ['1', '3', '2', '1']（先頭の '2' のみ削除）
    - 【リスト 末尾取り出し】list.pop(1) # list = ['1', '3', '2', '1']
    - 【リスト 要素番号取得】list.index('2') # 1（先頭の要素のみ）
    - 【リスト 要素数取得】 list.count('2') # 2
    - 【リスト 要素数取得】 len( list ) # 5
    - 【リスト 追加（末尾）】list.append('-') # list = ['1','2','3','2','1','-']
    - 【リスト 追加（中間）】list.insert(1,'-') # list = ['1','-','2','3','2','1']
- 【リスト 連結】list1 + list2

- 【コマンドライン引数】import sys ～ param = sys.argv
    - コマンド "python test.py python izm com" 実行時、param = ['test.py', 'python', 'izm', 'com']

- 【コマンド実行】import os ～ os.system( "attrib +h " + r"c:\test\a.txt" )

- 【プログラム終了】import sys ～ sys.exit()
- 【スリープ処理】import sleep ～ time.sleep( 0.001 ) ' 1[ms] スリープ

- 【現在時刻取得】from datetime import datetime ～ datetime.now().strftime("%Y/%m/%d %H:%M:%S")

- 【ファイルオープン】fileobj = open( "hoge.txt", 'r' ) # 'r':読込、'w':書込、'a':追記
- 【ファイルクローズ】fileobj.close()
- 【ファイル読込（一行毎１）】for line in fileobj: ～
- 【ファイル読込（一行毎２）】line = fileobj.readline()
- 【ファイル読込（全行１）】allLines = fileobj.readLines() # リストとして取得（改行文字は削除されない！）
- 【ファイル読込（全行２）】allLines = fileobj.read() # 改行区切りの文字列として取得
- 【ファイル書込】fileobj.write( "test string" )

- 以下、trgtpath = r"C:\targetdir\test\sample.txt" とする
- 【os インポート】import os
    - 【ディレクトリ作成（単一）】os.mkdir( trgtpath )
    - 【ディレクトリ作成（複層）】os.makedirs( trgtpath )
- 【os.path インポート】import os.path
    - 【ファイル名抽出】os.path.basename( trgtpath ) # "sample.txt"
    - 【ディレクトリパス抽出】os.path.dirname( trgtpath ) # "C:\targetdir\test"
    - 【拡張子抽出】path, ext = os.path.splitext( trgtpath ) # ext = ".txt"
    - 【ファイル存在確認】os.path.exists( trgtpath )
    - 【ディレクトリ存在確認】os.path.isdir( trgtpath )

- 【shutil インポート】import shutil
    - 【ファイルコピー１】shutil.copyfile(r"C:\src\src.txt", r"C:\dst\dst.txt")
    - 【ファイルコピー２】shutil.copy(r"C:\src\src.txt", r"C:\dst")
    - 【ディレクトリコピー】shutil.copytree(r"C:\src", r"C:\dst")
    - 【ディレクトリ配下削除】shutil.rmtree(r"C:\targetdir") # 配下のファイルも削除

- 以下、実行スクリプトのファイルパスは "C:\dir\sample.py" とする
    - 【実行スクリプト ファイル相対パス１】\_\_file\_\_ # "dir\sample.py"
    - 【実行スクリプト ファイル相対パス２）】import sys ～ sys.argv[0] # "dir\sample.py"
    - 【実行スクリプト ファイル絶対パス】import os ～ os.path.abspath( \_\_file\_\_ ) # "C:\dir\sample.py"
    - 【実行スクリプト ファイル名】import os ～ os.path.basename( os.path.abspath( \_\_file\_\_ ) ) # "sample.py"

- 【フォルダ内ファイルリスト取得】import glob ～ files = glob.glob(r"C:\Python25\\*.\*")
（フォルダ以外。サブフォルダ配下は無視）
- 【ファイル/フォルダリスト取得（サブフォルダ含む）】
    ``` python 
    # create file list. filetype selectable
    #   0:both, 1:files, 2:directorys, other:none
    def create_file_list(dirpath, filetype):
        for root, dirs, files in os.walk(dirpath):
            if filetype == 0 or filetype == 2:
                yield root.replace("\\", "/")
            if filetype == 0 or filetype == 1:
                for file in files:
                    yield os.path.join(root, file).replace("\\", "/")
    ```
- 【ファイル/ディレクトリ判別】import os ～ os.path.isdir(r"c:\dir\sample.py") # false

# 演算子

| 演算子            | 種別   | 説明                                                                |
|:---|:---|:---|
| +a                | 代数   | 正数                                                                |
| -a                | 代数   | 負数                                                                |
| a + b             | 代数   | 加算                                                                |
| a - b             | 代数   | 減算                                                                |
| a \* b            | 代数   | 乗算                                                                |
| a / b             | 代数   | 除算                                                                |
| a % b             | 代数   | a を b で割った余り                                                 |
| a \*\* b          | 代数   | a の b 乗                                                           |
| a // b            | 代数   | 切り捨て除算                                                        |
| ~a                | ビット | ビット反転                                                          |
| a & b             | ビット | AND:論理積                                                          |
| a &#124; b        | ビット | OR:論理和                                                           |
| a ^ b             | ビット | XOR:排他的論理和                                                    |
| a << b            | ビット | b ビット左シフト                                                    |
| a >> b            | ビット | b ビット右シフト                                                    |
| a = b             | 代入   | a に b を代入する                                                   |
| a += b            | 代入   | a = a + b に同じ                                                    |
| a -= b            | 代入   | a = a - b に同じ                                                    |
| a \*= b           | 代入   | a = a \* b に同じ                                                   |
| a /= b            | 代入   | a = a / b に同じ                                                    |
| a %= b            | 代入   | a = a % b に同じ                                                    |
| a \*\*= b         | 代入   | a = a \*\* b に同じ                                                 |
| a //= b           | 代入   | a = a // b に同じ                                                   |
| a &= b            | 代入   | a = a & b に同じ                                                    |
| a &#124;= b       | 代入   | a = a &#124; b に同じ                                               |
| a ^= b            | 代入   | a = a ^ b に同じ                                                    |
| a <<= b           | 代入   | a = a << b に同じ                                                   |
| a >>= b           | 代入   | a = a >> b に同じ                                                   |
| a == b            | 比較   | a が b と等しい                                                     |
| a != b            | 比較   | a が b と異なる                                                     |
| a < b             | 比較   | a が b よりも小さい                                                 |
| a > b             | 比較   | a が b よりも大きい                                                 |
| a <= b            | 比較   | a が b 以下である                                                   |
| a >= b            | 比較   | a が b 以上である                                                   |
| a <> b            | 比較   | a が b と異なる                                                     |
| a is b            | 比較   | a が b と等しい                                                     |
| a is not b        | 比較   | a が b と異なる                                                     |
| a in b            | 比較   | a が b に含まれる                                                   |
| a not in b        | 比較   | a が b に含まれない                                                 |
| a and b           | ブール | a も b も真であれば真                                               |
| a or b            | ブール | a または b が真であれば真                                           |
| not a             | ブール | a が偽であれば真                                                    |
| x if c else y     | 条件   | c が真であれば x を、さもなくば y を返します。                      |
| a + b             | 文字列 | 文字列 a と 文字列 b を連結                                         |
| a \* n            | 文字列 | 文字列 a を n 回繰り返す                                            |
| a[n]              | 文字列 | 文字列 a の n 番目の文字を取り出す                                  |
| a[n:m]            | 文字列 | 文字列 a の n 番目から m 番目まで（m は含まない）の文字列を取り出す |
| a[n:]             | 文字列 | 文字列 a の n 番目から最後までの文字列を取り出す                    |
| a[:m]             | 文字列 | 文字列 a の 0 番目から m 番目まで（m は含まない）の文字列を取り出す |
| a[n:m：s]          | 文字列 | 文字列 a の n 番目から m 番目までの文字列を s個とばしで取り出す     |

[トップに戻る](../index.md)
