# Swift

[トップに戻る](../index.md)

## 構文メモ

- 変数種別
    - let：定数
    - var：変数
- 例外処理

    ```swift
    do {
        try メソッド呼び出し
    } catch {
        // エラー処理
    }
    ```

- オプショナル型 `?`
    - 値がない状態を許す型
- アンラップ
    - オプショナル型の変数やメソッドを安全に取り扱うための手法
    - チェックせずに使う場合、強制アンラップ(`!`)する
    - チェックして使う場合は、`if let ～`や`guard if ～`を使用する
- `var body: somo View` のsomeは推論のための就職子。（viewプロトコルに関連したデータ型という意味）
- @Binding
    - @Stateを定義したViewと他のViewとの間で双方向にデータ連動できるようにする構造体
- delegate
    - 処理が完了したときに通知されるための仕組み
    - [delegate](https://eow.alc.co.jp/search?q=delegate)：〔他者の代わりに行動する権限を与えられた〕代理人
- Any型
    - 構造体、クラス、関数、その他オプショナル型含め、任意の値を表現できるデータ型
    - どんな型でもセットできる型
- `as`
    - キャスト演算子
    - e.g. `image as UIImage`
- `as?`
    - 条件付きキャスト演算子で返却値はオプショナル型。
    - 型変換を試みて、失敗時は「nil」が返却される
    - e.g. `image as? UIImage`
- ★コンストラクタの先頭の `_` は何だっけ？

## 参考書メモ

### [SwiftUI 対応 たった2 日でマスターできる iPhone アプリ開発集中講座 Xcode 13/iOS 15/Swift 5.5 対応](https://www.amazon.co.jp/gp/product/B09JSKHB8L/ref=ppx_yo_dt_b_d_asin_title_o01?ie=UTF8&psc=1)

- MyMap
    - p.208 なぜプレビュー機能の時はMapView_previewが先に実行されるのか？
        - MapView.swiftを表示しているため
    - P.209 緯度軽度が返却されない
        - 処置内容：[検索ワードをtokyo towerに変えると返却される！](https://teratail.com/questions/ds25q5i80p0i10)
    - p.208 updateUIViewが実行されるタイミングは？
        - ★
- MyCamera
    - p.366 フォトライブラリが開けない
        - 処置内容：p.364におけるソースコード上の `isPhotolibrary = true` の後ろに `isShowSheet = true` を追加する
    - p.366 フォトライブラリーで写真を選択してから戻れない
        - 処置内容：p.356におけるソースコード上の `self.parent.captureImage = unwrapImage` の後ろに `self.parent.isShowSheet = false` を追加する

[トップに戻る](../index.md)
