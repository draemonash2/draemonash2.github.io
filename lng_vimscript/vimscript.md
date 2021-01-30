[トップに戻る](../index.md)

# 構文
- 【変数 定義】let s:lVal = ""
- 【定数 定義】let asList = ['a', 'b', 'c'] ～ lockvar asList " unlockvar asList で解除可能。
- 【関数 定義】function! Func() ～ return lRetVal ～ endfunction
- 【関数 呼出】Func()
- 【関数 終了】return
- 【構造体 定義】★
- 【列挙型 定義】★
- 【ブロック脱出】break

- 【if】if s:vimCurMode == "v" ～ elseif s:vimCurMode == "n" ～ else ～ endif
- 【switch】なし
- 【for】for iLoopCnt in range( 5, 1, -1 ) ～ endfor " range( start, end, step) ０オリジン
- 【while】while iLoopCnt < 5 ～ endwhile
- 【コメント】" コメント
- 【出力】echo "Hello World!"
- 【出力（履歴保存）】echom "Hello World!" ":messege にて履歴参照可能。デバッグにもってこい！
- 【出力（改行のみ）】echo "\n"
- 【チェック処理】なし
- 【入力】let l:sText = input("what your name ?", "yamada")

- 【コマンド実行】execute "cd " . sCtagsPath
- 【外部コマンド実行】execute "!start C:/prg/ctags58j2bin/ctags.exe -R"
- 【ファイル存在確認】if filereadable( "c:/codes/c/tags" ) ～ endif
- 【カーソル位置取得（Ｘ軸）】col('.')
- 【カーソル位置取得（Ｙ軸）】line('.')

- 【文字列 長さ】len( l:asDirNames )
- 【文字列 置換】substitute( expand('%:p'), "/", "\\", "g" )
- 【文字列 抽出】let substr = 'abcd'[1]      " b
- 【文字列 抽出】let substr = 'abcd'[0 : 1]  " ab
- 【文字列 抽出】let substr = 'abcd'[ : 1]   " ab
- 【文字列 抽出】let substr = 'abcd'[2 : ]   " cd
- 【文字列 抽出】let substr = 'abcd'[1 : -1] " bcd

- 【vim script からキー送信】call feedkeys("\<c-w\>w", t)

# データ型
- 変数

| 型 | 説明                                   |
|:---|:---|
| b  | 現在のバッファにローカル               |
| w  | 現在のウィンドウにローカル             |
| t  | 現在のタブページにローカル             |
| g  | グローバル                             |
| l  | 関数にローカル                         |
| s  | :source されたVimスクリプトにローカル  |
| a  | 関数の引数(関数内のみ)                 |
| v  | グローバル、Vimがあらかじめ定義        |

# Tips
- 列番号取得には苦労したよ。。。
	- 詳細は本ページ添付の「VimScript\_列番号取得に関する考察.xlsx」参照

[トップに戻る](../index.md)
