[トップに戻る](../index.md)

# 設定

- [リモートのVimからssh越しにクリップボード書き込み](https://tateren.hateblo.jp/entry/2017/07/21/213020)
	- 端末側の設定
		- [設定]→[その他の設定]→[制御シーケンス]→[リモートからのクリップボードアクセス]を書き込みのみ（又は読込/書込）
	- Vim側の設定
		- [osc52.vimをダウンロードして任意のパスに格納](https://github.com/ghcjs/ghcjs-hterm/blob/master/chromeapps/hterm/etc/osc52.vim)
		- .vimrc内に以下の二行を追記
			```
			source ~/path/to/osc52.vim
			vmap <C-c> y:call SendViaOSC52(getreg('"'))<cr>
			```
		- 日本語化に対応するためにosc52.vimを編集
			``` diff
			diff --git a/osc52.vim b/osc52_for_teraterm.vim
			index 1cb6931..376347b 100644
			--- a/osc52.vim
			+++ b/osc52_for_teraterm.vim
			@@ -42,7 +42,8 @@ endfunction
			 "
			 " It's appropriate when running in a raw terminal that supports OSC 52.
			 function! s:get_OSC52 (str)
			-  let b64 = s:b64encode(a:str)
			+  let str = iconv(a:str, &encoding, "cp932")
			+  let b64 = s:b64encode(str)
			   let rv = "\e]52;c;" . b64 . "\x07"
			   return rv
			 endfunction
			@@ -56,7 +57,8 @@ endfunction
			 function! s:get_OSC52_DCS (str)
			   " The base64 commands with no params will return a string with newlines
			   " every 72 characters.
			-  let b64 = s:b64encode(a:str)
			+  let str = iconv(a:str, &encoding, "cp932")
			+  let b64 = s:b64encode(str)
			 
			   " Remove the trailing newline.
			   let b64 = substitute(b64, '\n*$', '', '')
			```

# 用語

- VTWindow
	- Tera Term のメインウィンドウのこと
	- 起動したときに現れるウィンドウで、タイトル文字列の一番右に「VT」と表示されています。
	- VT 端末のエミュレーションをします。
- TEK window
	TEK 端末のエミュレーションをするウィンドウで、タイトル文字列の一番右に「TEK」と表示されています。

[トップに戻る](../index.md)
