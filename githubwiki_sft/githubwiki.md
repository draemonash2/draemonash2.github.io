[トップに戻る](../index.md)

# 構文

## 見出し

```
#
##
###
```

## 箇条書き（番号なし）

```
- aaa
<TAB>- bbb
<TAB><TAB>- ccc
<TAB>- ddd
```

- aaa
	- bbb
		- ccc
	- ddd

## 箇条書き（番号あり）

```
1. aaa
<TAB>1. bbb
<TAB><TAB>1. ccc
<TAB>1. ddd
```

1. aaa
	1. bbb
		1. ccc
	1. ddd

## 引用

```
> お世話になります。xxxです。
> ご連絡いただいた、バグの件ですが、仕様です。
>> お世話になります。 yyyです。
>> あの新機能バグがあります。
```

> お世話になります。xxxです。
> ご連絡いただいた、バグの件ですが、仕様です。
>> お世話になります。 yyyです。
>> あの新機能バグがあります。

## 強調

```
normal *italic* normal
normal _italic_ normal
normal **bold** normal
normal __bold__ normal
normal ***bold+italic*** normal
normal ___bold+italic___ normal
normal ~~strikethrough~~ normal
```

- normal *italic* normal
- normal _italic_ normal
- normal **bold** normal
- normal __bold__ normal
- normal ***bold+italic*** normal
- normal ___bold+italic___ normal
- normal ~~strikethrough~~ normal

## 水平線

```
***
---
```

---

## pre記法

- 上下の行は空行である必要なし。
- pre記法はインデントしないほうがいい。(インデントした分、行頭に空白文字が挿入される)

```
``` ruby
class Hoge
  def hoge
    print 'hoge'
  end
end
\```
```

``` ruby
class Hoge
  def hoge
    print 'hoge'
  end
end
```

## 表組み

- 表の左にタブを付与すると、表をインデントできる
- 表の上下の行が空行(もしくはスペース/タブのみの行)である必要あり！
- 表内で「｜」を使うときは、エスケープもしくはasciiコード`&#124;`で表現する

```
|header1|header2|header3|
|:--|--:|:--:|
|align left|align right|align center|
|a|b|c\||
```

|header1|header2|header3|
|:--|--:|:--:|
|align left|align right|align center|
|a|b|c\||


## リンク

```
[Google先生](https://www.google.co.jp/)
```

[Google先生](https://www.google.co.jp/)

## ページ内リンク

```
[to header1](#header1)
```

[リンク](#リンク)

## 画像

```
![画像１](image.jpg)
![画像２](http://test/image2.jpg)
```

![画像１](image.jpg)
![画像２](http://test/image2.jpg)

## 取り消し線

```
~~取り消し線~~
```

## チェックボックス

```
- [x] チェック済み
- [ ] 未チェック
```

- [x] チェック済み
- [ ] 未チェック

## 折り畳み（デフォルトopen）

```
<details open>
<summary>展開</summary>

1. aaa
1. bbb
    - ccc
</details>
```

<details open>
<summary>展開</summary>

1. aaa
1. bbb
    - ccc
</details>

## 折り畳み（デフォルトclose）

```
<details>
<summary>展開</summary>

1. aaa
1. bbb
    - ccc
</details>
```

<details>
<summary>展開</summary>

1. aaa
1. bbb
    - ccc
</details>

[トップに戻る](../index.md)
