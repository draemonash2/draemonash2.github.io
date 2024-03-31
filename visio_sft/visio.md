
# Visio

[トップに戻る](../index.md)

## Tips

- ステンシル(.vss、.vssx)を自動で開く
    1. 以下フォルダ配下にステンシルファイルを格納する
        - `%USERPROFILE%\OneDrive\Documents\個人用図形`
- オフセットコピー
    - シェイプをCtrl＋ドラッグ＆ドロップでコピー＋F4キーを押します。
    - 初めにコピーしたのと同じ間隔で、F4キーを押した回数だけどんどんオフセットコピーができます。
- 画面の移動
    - Ctrl＋Shift＋マウス右ボタン＋マウス移動
- 背面にあるシェイプ選択
    - 表にあるシェイプをクリックして選択後、もう一度クリックすると背面にあるシェイプを選択できる。
- excel図形との差
    - 図形内のテキストを検索、置換できる
    - 図形操作のショートカットキーが多い
    - 避けるコネクタを使える
- vbaマクロ周り
    - vbaアドインについて
        - excel vbaとは違い、アドインを適用できない！
    - vbaマクロについて
        - マクロが入っているファイルのみマクロが使える。ほかのファイルは使えない。
            - つまり、マクロを使うためには、vbaソースコードを組み込む必要がある！
        - マクロショートカットキーについて
            - excel vba とは違い、Application.OnKey が使えない。
            - クイックアクセスツールバーにvbaマクロを登録できない
                - つまり、ショートカットキーは「ctrl+★」のみ！
- スナップ/接着/ダイナミックグリッド
    - スナップ
        - 図形の位置をどこに合わせるか？
    - 接着
        - 接続を図形のどこに接着させるか？
    - ダイナミックグリッド
        - 他の図形の中心に合わせるか？とか、等間隔に合わせるか？
- Excelに埋め込んだVisioオブジェクトを編集できない。
    - 事象
        - Excelに埋め込んだVisioオブジェクトは、「オブジェクトを右クリック」->「Visio オブジェクト(O)」->「開く(O)」で編集できる。  
        しかし、右クリック時のコンテキストメニューに「Visio オブジェクト(O)」が表示されないことで、編集できないことがある。
    - 対処方法
        - Visioオブジェクトをダブルクリックして、一度Visioオブジェクトを直接編集する。  
        それにより、右クリック時のコンテキストメニューに「Visio オブジェクト(O)」が表示されるようになる。

## マクロサンプル

```txt
Public Sub 上下に整列()
    Application.ActiveWindow.Selection.Distribute visDistVertSpace, False
End Sub

Public Sub 左右に整列()
    Application.ActiveWindow.Selection.Distribute visDistHorzSpace, False
End Sub

Public Sub 左右中央揃え()
    Application.ActiveWindow.Selection.Align visHorzAlignCenter, visVertAlignNone, False
End Sub

Public Sub 上下中央揃え()
    Application.ActiveWindow.Selection.Align visHorzAlignNone, visVertAlignMiddle, False
End Sub
```

## ショートカットキー

|Ctrl|Shift|Alt|Key|機能|
|:---|:---|:---|:---|:---|
||||Tab|図形間でフォーカスを1つ移動|
||||F8|[図形の整列] ダイアログ|
||Shift||マウスホイール|左右スクロール|
|Ctrl|||1|[オブジェクト選択ツール]|
|Ctrl|||2|[テキスト ツール]|
|Ctrl|||3|[コネクタ]|
|Ctrl|||6|[直線ツール]|
|Ctrl|||7|[円弧ツール]|
|Ctrl|||8|[四角形ツール]|
|Ctrl|||9|[円/楕円ツール]|
|Ctrl|Shift||1|[接続ポイント]|
|Ctrl|Shift||4|[テキスト ボックス ツール]|
|Ctrl|Shift||w|ページサイズ ウィンドウに合わせる|
|Ctrl|Shift||f7|開いている図面ウィンドウを左右に並べて表示|
|Ctrl|||h/j|オブジェクト 左右反転/上下反転|
|Ctrl|||l/r|オブジェクト 回転 反時計回り/時計回り|
|Ctrl|(Shift)||g/u|オブジェクト グループ化/グループ化解除|
|Ctrl|Shift||f/b|オブジェクト 最前面/最背面に移動|
|Ctrl|Shift||\>/<|テキスト フォント 拡大/縮小|
|Ctrl|Shift||p|テキスト 書式のコピー/貼り付け|
|Ctrl|Shift||l/r/c/j|テキスト 横 左揃え/右揃え/中央揃え/両端揃え|
|Ctrl|Shift||t/m/v|テキスト 縦 上揃え/中央揃え/下揃え|
|||Alt|f9|スナップと接着|

[トップに戻る](../index.md)
