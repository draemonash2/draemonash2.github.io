[トップに戻る](../index.md)

- string から regexp へは Regexp.new() にて変換可能
- match	は String でも使用可能。( String で正規表現も使用可能)
- include?	は Regexp を使用不可。
⇒ include? は使用すべきでないかも…
⇒ ただし、 match を使用する際は、 MatchData 型であることに注意！
- 「Regexp =~ String」(または 「String =~ Regexp」) は、パターンにマッチした場合の先頭の文字の位置を返却する。
-  Regexp には、修飾子を付加できる。(ex. /^abc/i ) 詳細は下記。

| 修飾子 | 意味 |
|:---|:---|
| /i |大文字と小文字を区別せずにマッチを行う|
| /o |式展開を一度だけ行う|
| /x |パターンの中の空白やコメントを無視する|
| /m |複数行モード。メタ文字(.)が改行にもマッチする|
| /n |文字コードをNONE(ASCII)|
| /e |文字コードをEUC-JP|
| /s |文字コードをShift\_JIS|
| /u |文字コードをUTF-8|

[トップに戻る](../index.md)
