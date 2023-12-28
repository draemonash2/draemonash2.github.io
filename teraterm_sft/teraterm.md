
# TeraTerm

[トップに戻る](../index.md)

## 設定

- [リモートのVimからssh越しにクリップボード書き込み](https://tateren.hateblo.jp/entry/2017/07/21/213020)
    - 端末側の設定
        - [設定]→[その他の設定]→[制御シーケンス]→[リモートからのクリップボードアクセス]を書き込みのみ（又は読込/書込）
    - Vim側の設定
        - [osc52.vimをダウンロードして任意のパスに格納](https://github.com/ghcjs/ghcjs-hterm/blob/master/chromeapps/hterm/etc/osc52.vim)
        - .vimrc内に以下の二行を追記

            ```vimscript
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

- キーバインド設定
    1. `KEYBOARD.CNF` 内の `[User keys]` を編集する。
        - 形式は以下の通り。(ヘルプより引用)

            ```txt
            形式:
                <User key name>=<PC key code>,<Control flag>,<文字列>
            
            <User key name>
                User1, User2, User3,...., User99
                最大99個まで設定可能、例えば10個設定する場合は User1 から
                順番に User10 までを使用し、それ以外の名前を使用してはなら
                ない。
            
            <PC key code>
                PC key code (10進数)
            
            <Control flag>
                キーを押したときに <文字列> をどのように取り扱うかを指定
                するフラグ。
                    0   <文字列>をそのまま送出する。
                    1   <文字列>に含まれる漢字や改行コードを
                        Tera Term の設定にあわせて変換し、変換
                        された文字列を送出する。
                    2   <文字列>のファイル名のマクロファイルを
                        実行する。
                    3   メニュー ID <文字列> で指定される
                        Tera Term のメニューコマンドを実行する。
            
            <文字列>:
                <Control flag> が 0 または 1 の場合、キーを押したときに
                送出される文字列。表示不可能な文字(制御文字等)はその
                ASCII コードを $ と2文字の16進数で表現する
                (例: CR 文字は '$0D')。"$" そのものは "$24" で表現する。
                「付録 A  ASCII コード表」参照。
            
                <Control flag> が 2 の場合、実行されるマクロファイルの
                ファイル名。
            
                <Control flag> が 3 の場合、実行されるメニューコマンドの
                メニュー ID (数字)。「付録 B  メニュー ID 表」参照。
            
            例:
                User1=1083,0,telnet myhost
                User2=1084,0,$0D$0A
                User3=1085,1,こんにちは。
                User4=1086,2,test.ttl
                User5=1087,3,50110
            ```

        - `<PC key code>`は、keycode.exeで確認する。
        - `<文字列>`は、`<Control flag>`が0か1の場合はヘルプの「付録 A  ASCII コード表」を確認する。

## 用語

- VTWindow
    - Tera Term のメインウィンドウのこと
    - 起動したときに現れるウィンドウで、タイトル文字列の一番右に「VT」と表示されています。
    - VT 端末のエミュレーションをします。
- TEK window
    TEK 端末のエミュレーションをするウィンドウで、タイトル文字列の一番右に「TEK」と表示されています。

[トップに戻る](../index.md)
