# Swift

[トップに戻る](../index.md)


## Tips

- DropboxAPI使用方法
    1. Dropbox API設定する
        1. TODO:

    1. [cocoapods インストール](https://ios-docs.dev/cocoapods/)

        ```shell
        brew update
        brew upgrade
        sudo gem install -n /usr/local/bin cocoapods -v 1.8.4
        pod setup
        ```

    1. Pods初期化

       ```shell
       cd ~/Documents/codes/swift/app/hab-chain # move project directory
       pod init
       ```

    1. [Podfile 編集](https://qiita.com/D4ik1/items/b4284a35925a526adb27)

        ```diff
         target 'app_name' do
           # Comment the next line if you don't want to use dynamic frameworks
           use_frameworks!
         
           # Pods for hab-chain
        +  pod 'SwiftyDropbox'
         
         end
        ```

    1. XCode のプロジェクトを閉じる
    1. Pod インストール

        ```shell
        pod install
        pod update
        ```

    1. Info.plistを作成する
        1. Info.plistファイル作成
            - Project -> TARGETSでInfoタブを選択する。[[1]](https://qiita.com/john-rocky/items/0d7bf4428f013feba64c)
        1. Info.plistファイル編集（<apps_key>にはDropBoxAPIにて設定したAppsKeyを設定する）

            ```diff
             <dict>
            +    <key>LSApplicationQueriesSchemes</key>
            +    <array>
            +        <string>dbapi-8-emm</string>
            +        <string>dbapi-2</string>
            +    </array>
                 <key>CFBundleURLTypes</key>
                 <array>
                     <dict>
            +            <key>CFBundleURLSchemes</key>
            +            <array>
            +                <string>db-<apps_key></string>
            +            </array>
            +            <key>CFBundleURLName</key>
            +            <string></string>
                     </dict>
                 </array>
             </dict>
             </plist>
            ```

- [ライフサイクルとメソッド( init(),onApper(),onDisappear())が呼ばれるタイミング](https://nonateck.com/?p=649)

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
    - チェックして使う場合は、`if let ～`や`guard iet ～`を使用する
        - `if let ～` ： アンラップできたとき
        - `guard iet ～` ： アンラップできなかったとき
- `var body: somo View` のsomeは推論のための就職子。（viewプロトコルに関連したデータ型という意味）
- プロパティラッパー
    - 概要
        - プロパティをラップして機能を追加する文法
    - 種類
        - @State
            - View内のプロパティ更新時にViewを自動的に再描画する
        - @Binding
            - @Stateを定義したViewと他のViewとの間で双方向にデータ連動できるようにする
        - @Published
            - ObservableObjectプロパティに準拠したクラス内部のプロパティを監視して、複数のViewへ自動通知できる
            - @StateObjectと組み合わせて利用する
        - @StateObject
            - ObservableObjectプロパティに準拠した外部クラスのプロパティの状態を受信する。
            - @Publishedと組み合わせて利用する
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
- メソッド引数先頭の `_` について
    - 呼び出し側でラベル名を省略するための命令
    - 例えば、以下例１のようにメソッド呼び出し処理では`quantity`や `price`等のラベルを指定して呼び出す。  
    しかし引数が自明の場合は、例２のように引数ラベルを省略させるようにすることも可能。
        - 例１）ラベル名あり

            ```swift
            //メソッド定義
            func calcSum(quantity qt: Int, price pc: Int) -> Int {
                return qt * pc
            }
            //メソッド呼び出し処理
            calcSum(quantity: 2, price: 300)
            ```

        - 例２）ラベル名なし

            ```swift
            //メソッド定義
            func debugMessage(_ message: String) {
                print("\(message)")
            }
            //メソッド呼び出し処理
            debugMessage("エラー")
            ```

- Viewを繰り返す方法
    - [ForEachを使う](https://q3task.com/swiftui_foreach/)
- 循環参照について
    - class内のクロージャは、参照型のため循環参照が発生する可能性がある。  
    対策のため、自分自身を指すselfを付与する必要がある。  
    (Swift5.3からselfが省略できるようになった)  
    structは値型のため循環参照の可能性がない。
- [asyncとawait](https://ticklecode.com/asyncawait/)
    - 非同期処理(async)を同期的に待つ(await)
    - 例）

        ```swift
        // リクエストURLからダウンロード
        let (_ , response) = try await URLSession.shared.data(from: req_url)
        // データ取得が完了したら、次のコードを実行
        if (response as? HTTPURLResponse)?.statusCode == 200 {
            print("2.データの取得できた")         
        }
        ```

- Combineフレームワーク
    - View間またはView⇔ファイル間でデータを配信・受信できる仕組み
    - SwiftUIで作成したViewとデータの状態を、非同期かつ双方向にデータ連動（バインド）できる
- Single Source of Truth
    - 変化する全データを１つの場所で保持し、状態の変化を階層化されたViewでまたがって配信・受信できるようにするという考え方。
    - Combineフレームワークで採用

## 参考書メモ

### [SwiftUI 対応 たった2 日でマスターできる iPhone アプリ開発集中講座 Xcode 13/iOS 15/Swift 5.5 対応](https://www.amazon.co.jp/gp/product/B09JSKHB8L/ref=ppx_yo_dt_b_d_asin_title_o01?ie=UTF8&psc=1)

- 誤記、不明点
    - MyMap
        - p.208 なぜプレビュー機能の時はMapView_previewが先に実行されるのか？
            - MapView.swiftを表示しているため
        - P.209 緯度軽度が返却されない
            - 処置内容：[検索ワードをtokyo towerに変えると返却される！](https://teratail.com/questions/ds25q5i80p0i10)
    - MyCamera
        - p.366 フォトライブラリが開けない
            - 処置内容：p.364におけるソースコード上の `isPhotolibrary = true` の後ろに `isShowSheet = true` を追加する
        - p.366 フォトライブラリーで写真を選択してから戻れない
            - 処置内容：p.356におけるソースコード上の `self.parent.captureImage = unwrapImage` の後ろに `self.parent.isShowSheet = false` を追加する
        - p.391 `isShowAction = true`の追加は不要では？
            - 前文と同じなので不要。なくても正常に動作する。
    - MyOkashi
        - p.450 追加したソースコードでは結果を取得できない
            - 処置内容：サンプルプログラムのプログラムの通りに修正する
                - 格納先： `XcodeSwift20211106/2_4/MyOkashi/src/MyOkashi/OkashiData.swift`

## サンプルプログラム

- 日付処理＋連想配列

    ```swift
    func Test2() -> String
    {
        var dicStatus:Dictionary<Date, Int> = [:]
        
        let today = Date()
        let yesterday = Calendar.current.date(byAdding: .day,value: -1, to: Date())!
        let yesterday_1 = Calendar.current.date(byAdding: .day,value: -2, to: Date())!
        
        let dateFormatter = DateFormatter()
        dateFormatter.dateFormat = DateFormatter.dateFormat(fromTemplate: "yyyyMMdd", options: 0, locale: Locale(identifier: "ja_JP"))
        
        dicStatus.updateValue(1, forKey: today)
        dicStatus.updateValue(2, forKey: yesterday)
        for (key,value) in dicStatus {
            print("\(dateFormatter.string(from: key)) : \(value)")
        }
        print("\(dicStatus[today]!)")
        print("\(dicStatus[yesterday]!)")
        //print("\(dicStatus[yesterday_1]!)")
        print("\(dicStatus.keys.contains(today))")
        print("\(dicStatus.keys.contains(yesterday))")
        print("\(dicStatus.keys.contains(yesterday_1))")
        return "1"
    }
    ```

[トップに戻る](../index.md)
