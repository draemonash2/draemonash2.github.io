
# python

[トップに戻る](../index.md)

## ToDo

- iTunes プレイリスト エクスポート

## 実行方法

- 以下コマンド実行

    ``` python
    python test01.py
    ```

## Tips

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
        - 例１） `print "1234\"567890" ⇒ 1234"567890`
            - 例２） `print "1234'567890" ⇒ 1234'567890`
            - 例３） `print '1234"567890' ⇒ 1234"567890`
            - 例４） `print "1234\\567890" ⇒ 1234\567890`
            - 例５） `print "1234\n567890" ⇒ 1234（改行）567890`
            - 例６） `print "1234\t567890" ⇒ 1234（タブ）567890`
- 変数配列＝リスト
- 定数配列＝タプル
- インクルード＝インポート
    - インポートはどの行に書いても問題なし
- ★ディクショナリについて
- メインプログラム実行時にのみ処理を行う方法
    - 方法
        - `if __name__ == "__main__":`
    - 解説
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
    - ちなみに Perl / Ruby / PHP は二つを区別。
        - ダブルクォーテーション：文字列内の特殊文字や変数などを置換
        - シングルクォーテーション：置換をせずそのまま出力する。
- lambda について
    - defステートメントのように関数を作成する際に使用するもの。defステートメントとは違い「式」。よってdefステートメントでは記述できない場所に記述することが可能。

        ``` python
        func = lambda x,y=10,z=30: x + y + z
        func(x=1) '⇒ 41
        ```

- [正規表現モジュールreの関数/メソッドの違い](https://note.nkmk.me/python-re-match-search-findall-etc/)
    - 関数/メソッド一覧
        - `compile()` ：正規表現パターンをコンパイル
        - `match()` ：文字列の先頭がマッチするかチェック、抽出
        - `search()` ：先頭に限らずマッチするかチェック、抽出
        - `fullmatch()` ：文字列全体がマッチするかチェック
        - `findall()` ：マッチする部分すべてをリストで取得
        - `finditer()` ：マッチする部分すべてをイテレータで取得
        - `sub()`, `subn()` ：マッチする部分を置換
        - `split()` ：正規表現パターンで文字列を分割
    - まとめ
        - 基本は `findall()` 。マッチ位置を取得する場合は `finditer()` を使う。
    - 実行例
        - `findall()`

            ```python
            pattern = r'(\[\d+\])'
            line = "aaa [1] bbb [2] ccc"
            matchlist = re.findall(pattern, line)
            if matchlist:
                print(matchlist[0][0] + matchlist[0][1])
            ```

        - `finditer()`

             ```python
             pattern = r'(\[\d+\])'
             line = "aaa [1] bbb [2] ccc"
             matchlist = list(re.finditer(pattern, line))
             for matchobj in matchlist:
                match_start_pos = matchobj.span()[0]
                match_end_pos = matchobj.span()[1]
             ```

- [yield文](http://ailaby.com/yield/)
	- 関数の処理を一旦停止して、戻り値を返す
- [相対パスのimport方法](https://qiita.com/u943425f/items/bd94a30b52c9296e942d)

## Python2 と 3の主な違い

- 相違点

| 相違点 | Python2 | Python3 |
|:---|:---|:---|
| print記述方式  | print "出力対象"(\*1) | print("出力対象") |
| ライブラリ数  | 多い | 少ない |
| 数値出力結果(\*2)  | 整数部のみ出力( ex. 3 ) | 小数部も出力( ex. 3.0 )(\*3) |
| long型有無  | ある | ない(int型として扱う) |
| 例外構文記述方法  | except Exception, e: | except Exception as e: |

- 相違点注記
    - (\*1) Python2で丸括弧のなかに複数のオブジェクトがあった時は、タプルを作ってprintすることになる。

        ``` python
        print 'Python', python_version() # -> Python 2.7.6
        print('a', 'b')                  # -> ('a', 'b')
        print 'a', 'b'                   # -> a b
        ```

    - (\*2) Python2で「`from __future__ import division`」を追加することでPython3と同等の振る舞いとなる
    - (\*3) 切り捨ては `6 // 2` のように演算する
- 参考URL
    - [Python2と3の違いとは？Pythonをこれから学習するならどっち？](https://www.acrovision.jp/career/?p=3146)
    - [Python 2.7.x と 3.x の決定的な違いを例とともに](https://postd.cc/the-key-differences-between-python-2-7-x-and-python-3-x-with-examples/)

## 構文

[言語チートシート](https://github.com/draemonash2/other/blob/master/%E8%A8%80%E8%AA%9E%E3%83%81%E3%83%BC%E3%83%88%E3%82%B7%E3%83%BC%E3%83%88.xlsx)参照

## 演算子

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
| a[n:m：s]         | 文字列 | 文字列 a の n 番目から m 番目までの文字列を s個とばしで取り出す     |

[トップに戻る](../index.md)
