# 構文

- 【見出し】
```
#
##
###
```
- 【箇条書き（番号なし）】
```
-
	-
		-
```
- 【箇条書き（番号あり）】
```
1.
	1.
		1.
```
- 【引用】
```
> お世話になります。xxxです。
> ご連絡いただいた、バグの件ですが、仕様です。
>> お世話になります。 yyyです。
>> あの新機能バグがあります。
```
- 【強調】
```
normal *italic* normal
normal _italic_ normal
normal **bold** normal
normal __bold__ normal
normal ***bold+italic*** normal
normal ___bold+italic___ normal
```
- 【取り消し線】
```
~~取り消し線~~
```
- 【水平線】
```
***
---
```
- 【pre記法】
```
	``` ruby
	class Hoge
	  def hoge
	    print 'hoge'
	  end
	end
	```
```
- 【表組み】
```
|header1|header2|header3|
|:--|--:|:--:|
|align left|align right|align center|
|a|b|c|
```
- 【リンク】
```
[Google先生](https://www.google.co.jp/)
```
- 【ページ内リンク】
```
[to header1](#header1)
```
- 【画像】
```
![画像１](image.jpg)
![画像２](http://test/image2.jpg)
```
- 表内の「|」エスケープ
	- 参考：asciiコードを変えれば他の文字を表現可能。
```
&#124;
```

# 他
```
###########################################
# 検索
###########################################
■wiki内ページ参照
\[\[(.{-1,})\]\]

###########################################
# 置換
###########################################
■見出し
%s/\v^\*\*\*/###/ge|%s/\v^\*\*/##/ge|%s/\v^\*/#/ge

■箇条書き
%s/\v^\-\-\-\-\-/\t\t\t\t\-/ge|%s/\v^\-\-\-\-/\t\t\t\-/ge|%s/\v^\-\-\-/\t\t\-/ge|%s/\v^\-\-/\t\-/ge
%s/\v^\+\+\+\+\+/\t\t\t\t\-/ge|%s/\v^\+\+\+\+/\t\t\t\-/ge|%s/\v^\+\+\+/\t\t\-/ge|%s/\v^\+\+/\t\-/ge|%s/\v^\+/\-/ge

■URL
s/\v\[\[(.{-1,})\>\>(.{-1,})\]\]/\[\1\]\(\2\)/ge

■表タイトル
s/\v\|(.{-1,})(\|)@=/\|:\-\-\-/ge

■Highlightタイトル
%s/\v#highlight\((.{-,})\)\{\{/```\1/ge|%s/^\}\}/```/ge
%s/\v#highlight\((.{-,})\)\{/```\1/ge|%s/^\}/```/ge

■image
%s/\v#image\((.{-,})\.(.{-,})\)/!\[\1\]\(\1\.\2\)/ge

###########################################
# TODO
###########################################
■Highlight複数行
#highlight( vb ){{ ～ }}

■フォント色
&color(red){★}
<font color="Red">★</font>
s/\v\&color\((.{-1,})\)\{(.{-1,})\}/\<font\scolor\="\1"\>\2\<\/font\>/g
⇒★出来ない…要検討★
```