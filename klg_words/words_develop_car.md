- 開発_車  
    - CAN  
        - 概要  
            - CAN2.0A  
            - CAN2.0B  
        - 特徴  
            - 高速アクセス  
                - 伝送長により異なりますが、CANの転送レートは、MAX1Mbpsであり、制御系LANとしては、適度なアクセススピードを実現できます。  
            - エラー検出  
                - エラー検出として送信2つ受信Textが3つのエラー検出機能があり、充実しています。  
            - 短いメッセージ構成  
                - メッセージとしては、0byte～8byteと短いメッセージ構成がとなっていますので再送信などの場合、再送までの時間がかなり短くなります。  
            - マルチマスター方式  
                - データとしては、マルチマスタ方式での通信となります。  
            - バスアクセスの優先順位  
                - バスの優先順位は、IDの低いものが優先となります。  
                - アービトレーションを実行することによって、リアルタイムに衝突を検出し、優先ノードの送信をしている！  
                    - アービトレーションはID: 0 が最も優先度高！  
                        - ⇒優先度を変更するのが困難？  
                        - Ethernet はフレームに アドレスを含む  
                        - CAN はフレームにアドレスを含まない  
                            - 送信者/送信先はID毎にあらかじめ決められているため、不要！  
            - メディアアクセス方式  
                - CSMA/CD (Carrier Sense Multiple Access with Collition Detection)  
                    - ⇒Ethernet と同様  
                    - ⇒リアルタイム性が問われる車載システムで、どう実現されているのか？  
        - 利用業界  
            - 車載が一番に考えられますが、その他にも、CANの特徴を生かした多くのシステムに使用され始めている  
        - 速度  
            - 情報系  
                - 10000-100000kbps  
            - パワートレイン系  
                - 500kbps  
            - ボディー系  
                - 10-125kbps  
        - 種類  
            - BasicCAN  
                - 一般的に送信バッファと受信バッファの数が少なく，マスクレジスタにも制限があり，CPUに負荷がかかります  
            - FullCAN  
                - 送信バッファと受信バッファの数が多く，マスクレジスタにおいても許容範囲が大きいため，CPUへの負荷が少なくて済みます。富士通が対応してい  
        - 参考URL  
            - CAN基礎@keyence  
                リンク: [keyence.co.jp/ss/products/recorder/lab/candata/][1]  
            - CAN中級  
                リンク: [eetimes.jp/ee/spv/0912/15/news104.html][2]  
            - CAN詳細  
                リンク: [japan.renesasrulz.com/cfs-file/__key/communityserver-discussions-components-files/83/RJJ05B0937_2D00_0100.pdf]][3]  
    - AUTOSAR  
        - 階層  
            - アプリケーション層  
            - AUTOSARランタイム環境（Run time Environment：RTE）  
            - 基盤ソフトウエア（Basic Software：BSW）  
                - サービス層  
                    - -システムサービス，メモリサービス，通信サービスからなり， 大部分がハードウェアから独立している。  
                - ECU抽象化層  
                    - ハードウェアには依存していないがECUには依存している階層であり，主に搭載機器抽象化，メモリハードウェア抽象化，通信ハードウェア抽象化，I/Oハードウェア抽象化からなる。ECU抽象化層の目的は，ECUのすべてのコンポーネントを抽象化することである。  
                - マイクロコントローラ抽象化層（MCAL）  
                - 複合ドライバ層  
                    - 主に処理が間に合わない時などに使用します  
    - 機能安全  
        - 故障の分類  
            リンク: [e-devices.ricoh.co.jp/ja/technology/automotive/fault.html][4]  
            - SPF  
                - Single-point Fault  
                    - 安全機構なし かつ 単独故障  
            - RF  
                - Residual Fault  
                    - 安全機構ありだがカバーできない かつ 単独故障  
                        - residual  
                            リンク: [ejje.weblio.jp/content/residual][5]  
                            - 残りの,残余の  
            - MPF  
                - Multiple-point Fault  
                    - 独立した複数故障の重なり  
            - LF  
                - Latent Fault  
                    - デュアルポイント故障で、安全機構での検知もドライバの認識もできない隠れている故障  
                        - latent  
                            リンク: [ejje.weblio.jp/content/latent][6]  
                            - 隠れている,見えない,潜在的  
            - 概要  
                - 安全目標を侵害する要因  
        - FTA vs FMEA  
            - FTA  
                - 不具合原因を特定するため、可能性のある要因を「木の枝」、さらにその要因を「枝の先の葉」のように分解していきます。  
            - 故障モード  
                - システムの部品の特性劣化,物理的な構造破壊のこと  
                - ex) 断線、短絡、折損、摩耗  
                - 製品が機能しない原因となる不具合が必ずあります。この故障(機能障害)を引き起こした原因  
                - 種類  
                    - 故障  
                        - 故障モードが引金となって発生する機能障害  
                    - 不良  
                        - 機能を満足しない設計ミス  
                        - 指示どおり製造されなかったことによる欠陥品  
            - FMEA/FTA違い  
                リンク: [monodukuri.com/gihou/article/869][7]  
                - イメージ  
                    - ...  
                    - ...  
                - FTA  
                    - Failure Tree Analysis  
                        故障木解析  
                    - 周知の故障の発生確率を解析する。  
                    - トップダウン解析  
                - FMEA  
                    - Failure Mode and Effect Analysis  
                        故障モード影響度解析  
                    - ボトムアップ解析  
                    - 「故障モード」から想定階の故障・事故を洗い出す。  
                    - 一つの部品単体の機能から重大な故障の抽出を行う方法  
                - DRBFM  
                    - Design Review Based on Failure Mode  
                    - ボトムアップ解析  
                    - 設計の変更点のみに着眼して、変更した部品群の故障の可能性を洗い出す方法  
                    - トヨタ自動車によって確立された体系的なFMEAの運用方法。  
  
[1]: https://www.keyence.co.jp/ss/products/recorder/lab/candata/  
[2]: https://eetimes.jp/ee/spv/0912/15/news104.html  
[3]: https://japan.renesasrulz.com/cfs-file/__key/communityserver-discussions-components-files/83/RJJ05B0937_2D00_0100.pdf]  
[4]: https://www.e-devices.ricoh.co.jp/ja/technology/automotive/fault.html  
[5]: https://ejje.weblio.jp/content/residual  
[6]: https://ejje.weblio.jp/content/latent  
[7]: https://www.monodukuri.com/gihou/article/869  
