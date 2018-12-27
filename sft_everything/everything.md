# 簡単な検索

| 構文 | 説明 |
|:---|:---|
| 半角スペース | AND検索 |
| ｜ | OR検索 |
| ! | NOT |
| < > | グループ化 |
| " " | 囲まれた文字列そのものを直接検索 |
| * | 0文字以上の任意の文字列にマッチ |
| ? | 任意の1文字にマッチ |
| \*.\* | 上の\*に同じ |

# 正規表現検索

| 構文 | 説明 |
|:---|:---|
| a｜b |  a 又は b にマッチ |
| . | 全ての文字1字にマッチ |
| [abc] | a、b、cの3つの内どれか1文字にマッチ |
| [^abc] | a、b、cを除く全ての文字1つにマッチ |
| [a-z] | a ～ z の範囲の内どれか1文字にマッチ |
| [a-zA-Z] | a ～ z と A ～ Z の範囲の内どれか1文字にマッチ |
| ^ | ファイル名の先頭にマッチ |
| $ | ファイル名の末尾にマッチ |
| * | 直前の文字の0回以上の繰り返しにマッチ |
| ? | 直前の文字が0回もしくは1回ある場合にマッチ |
| + | 直前の文字の1回以上の繰り返しにマッチ |
| {x} | 直前の文字のx回繰り返しにマッチ |
| {x,} | 直前の文字のx回以上の繰り返しにマッチ |
| {x,y} | 直前の文字のx回以上、y回以下の繰り返しにマッチ |