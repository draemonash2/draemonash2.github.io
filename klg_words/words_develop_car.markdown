- 開発_車  
    - モータ  
        - DC電流  
            - 直流電流  
        - リアクトル  
            リンク: [kotobank.jp/word/%E3%83%AA%E3%82%A2%E3%82%AF%E3%83%88%E3%83%AB-148309][1]  
            - 概要  
                - インダクタを利用した、受動素子  
                - reactor  
            - 種類  
                - 限流リアクトル  
                    - 電力回路の短絡故障電流を抑制  
                - 消弧リアクトル  
                    - 送電線の中性点接地  
                - 分路リアクトル  
                    - 電力系統の無効電力調整  
                - 始動リアクトル  
                    - 籠型誘導電動機の始動電流を制限  
        - インダクタ  
            リンク: [article.murata.com/ja-jp/article/basic-facts-about-inductors-lesson-1][2]  
            - 電気エネルギーを磁気の形で蓄えることができる受動電子部品  
            - 直流は通し、交流は通しにくい部品  
        - リラクタンス  
            リンク: [weblio.jp/content/%E3%83%AA%E3%83%A9%E3%82%AF%E3%82%BF%E3%83%B3%E3%82%B9][3]  
            - 磁気抵抗  
                - 磁気回路における磁束の流れにくさを表す度合い  
                - 起磁力÷磁束  
        - PWM  
            - 三角波比較方式  
                リンク: [energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html][4]  
                - 概要  
                    - デジタル信号(PWM)からアナログ信号を生成するための方法  
                        - ...  
                    - 時間軸方向に量子化されていないPWM信号が得られるため、デジタル方式PWM変調回路よりも解像度が高い  
                    - キャリア周波数を下げると、モータ騒音が大きくなりますが、インバータから発生する高周波 ノイズや、漏れ電流を減らすことができます。  
                        リンク: [dl.mitsubishielectric.co.jp/dl/fa/document/catalog/gear/invertor/inverter.pdf][5]  
                        - キャリア周波数：低⇔高  
                            モータ騒音：大⇔小  
                            漏れ電流：小⇔大  
                            ノイズ：小⇔大  
                - URL  
                    - [https://synapse.kyoto/glossary/pwm/page001.html][6]  
                    - [http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html][7]  
        - 電気と磁気  
            - 右ねじの法則  
                - 意味  
                    - ”電流”を流した時の”磁界”の向き  
                        - ...  
            - フレミングの法則  
                - 左手  
                    - 意味  
                        - ”磁界”の中で”電流”を流した時の”力”の向き  
                              →モーターにおけるトルク方向がわかる  
                            - ...  
                    - 覚え方  
                        - 電→磁→力（中指→人差し指→親指）  
                - 右手  
                    - 意味  
                        - ”磁界”の中で”運動”した時の誘導”起電力”の向き  
                              →発電機の電流方向がわかる  
                            - ...  
                    - 覚え方  
                        - 起→磁→動（中指→人差し指→親指）  
        - 三相同期電動機  
            - ...  
        - ベクトル制御  
            - 数式  
                - クラーク変換  
                    - Iu + Iv + Iw = 0  
                    - Iα= Iu  
                    - Iβ= (Iu + 2Iv) / &radic;3  
                - パーク変換  
                    - Id = ＋Iα・cosθ＋Iβ・sinθ  
                    - Iq = －Iα・sinθ＋Iβ・cosθ  
                - 逆パーク変換  
                    - Vα= Vd・cosθ－Vq・sinθ  
                    - Vβ= Vd・sinθ＋Vq・cosθ  
            - 固定座標から回転座標へ変換  
                リンク: [physics-school.com/rotate-coordinates-equation/][8]  
                - ![固定座標→回転座標](固定座標→回転座標.jpg)  
            - 弱め界磁  
                リンク: [tech.nikkeibp.co.jp/dm/article/WORD/20090916/175328/][9]  
                - 界磁に永久磁石を用いたモータでは永久磁石の磁束が一定なので，回転数が上がるにつれて同磁束によって生じる逆起電力が増加する。  
                    そして，ある回転数に達すると，この逆起電力がモータの印加電圧と等しくなる。それにより，モータには電流を流せなくなり，それよりも回転数を上げることができなくなる。これを防ぐために用いるのが手法。  
            - 参考URL  
                - ベクトルエンジンとベクトル制御  
                    リンク: [toshiba.semicon-storage.com/jp/design-support/e-learning/mcupark/village/vector-1.html][10]  
                - Clarke-Park 変換  
                    リンク: [jp.mathworks.com/solutions/power-electronics-control/clarke-and-park-transforms.html][11]  
                - マイコン：モータ駆動用ベクトル制御技術  
                    リンク: [youtube.com/watch][12]  
            - 他の用語  
                - dq軸  
                    - d：磁界成分  
                        - Direct  
                    - q：トルク成分  
                        - Quadrature(直交)  
        - 相電流と線間電圧  
            リンク: [hegtel.com/three-phase-delta.html][13]  
            - 相電流  
                - 三相交流回路における3つの電源の電流のこと  
            - 線間電圧  
                - 負荷側へ延びている3本の電線のうち2本間の電圧差  
            - ...  
        - 電気角/機械角  
            - 電気角  
                - ステッピング・モータのコイルに流す交流電流の角度  
            - 機械角  
                - 実際にステッピング・モータが回転する角度  
            - ex)8極2相で、36枚の小歯を持つステッピング・モータの場合  
                - ある極に交流電流を一周期分（電気角を360度）流した時、実際にモータは360 度÷36枚＝10度（機械角）回転する。  
            - ![][14]  
                リンク: [mohno-dispenser.jp/compass/compass08.html][15]  
        - sin/cos  
            - 正弦/余弦  
                - ![][16]  
                    - ![][17]  
                - 正弦  
                    - 弦の長さを求めるためのもの  
                - 余弦  
                    - 引いた弦の長さ  
            - ...  
                - 正弦波  
                    - sin  
                - 余弦波  
                    - cos  
        - モーター  
            - ゲートドライバー  
                - リンク: [ameblo.jp/odamaki3/entry-12373760947.html][18]  
            - 界磁電流を変える理由  
                - ★  
        - 他  
            - サーボモーター  
                - 目標物に忠実にかつ素早く応答することを目的としたモータ  
                - Servus@ラテン語  
                    - Slave@英語  
                        - 奴隷  
        - 短絡電流  
            リンク: [indexpro.co.jp/article/detail/13/7][19]  
            - 各相コイル端子をGNDに短絡（ショート）し、モータには電気ブレーキ制動  
        - 電機子  
            - 磁界を発生させる固定子または回転子のこと  
        - 負荷角  
        - 参考URL  
            - 同期機  
                リンク: [energychord.com/children/energy/motor/sync/contents/sync_principle.html][20]  
            - パーク変換法の導入  
                リンク: [denki-no-shinzui.com/3872/][21]  
            - クラーク変換法の導入  
                リンク: [denki-no-shinzui.com/502/][22]  
            - レゾルバオフセット調整の目的と方法  
                リンク: [ekouhou.net/%E3%83%A2%E3%83%BC%E3%82%BF%E5%88%B6%E5%BE%A1%E8%A3%85%E7%BD%AE/disp-A,2007-228700.html][23]  
            - モータの基礎と永久磁石  
                リンク: [neomag.jp/mailmagazines/topics/letter201003.html][24]  
            - 三菱電機製ベルト駆動式モータジェネレーター  
                リンク: [giho.mitsubishielectric.co.jp/giho/pdf/2016/1603113.pdf][25]  
    - 機能安全  
        - 故障の分類  
            リンク: [e-devices.ricoh.co.jp/ja/technology/automotive/fault.html][26]  
            - SPF  
                - Single-point Fault  
                    - 安全機構なし かつ 単独故障  
            - RF  
                - Residual Fault  
                    - 安全機構ありだがカバーできない かつ 単独故障  
                        - residual  
                            リンク: [ejje.weblio.jp/content/residual][27]  
                            - 残りの,残余の  
            - MPF  
                - Multiple-point Fault  
                    - 独立した複数故障の重なり  
            - LF  
                - Latent Fault  
                    - デュアルポイント故障で、安全機構での検知もドライバの認識もできない隠れている故障  
                        - latent  
                            リンク: [ejje.weblio.jp/content/latent][28]  
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
                リンク: [keyence.co.jp/ss/products/recorder/lab/candata/][29]  
            - CAN中級  
                リンク: [eetimes.jp/ee/spv/0912/15/news104.html][30]  
            - CAN詳細  
                リンク: [japan.renesasrulz.com/cfs-file/__key/communityserver-discussions-components-files/83/RJJ05B0937_2D00_0100.pdf]][31]  
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
    - レゾルバセンサ  
        - 概要  
            - モーターの角度と回転速度を検出するセンサー。取得した情報をもとに、モーターを細かく制御する。  
        - 構造  
            - ステータに2次側巻線として2つのピックアップ巻線を90°に配置。  
                リファレンス信号を加える1次側巻線もステータ上に配置し、ローターには中継用の巻線のみを搭載。  
                （ブラシ構造は持ちません）  
        - 検出までの流れ  
            - 1. リファレンス信号を1次側巻線へ加える。  
  
                1. ローターの巻線上に誘導される。  
                1. ステータ上の2つの2次側巻線には、ローターの角度に応じて、起電力が発生  
        - 参考URL  
            - 自動車の電動化（HEV&EV）コア技術 レゾルバ編  
                リンク: [ameblo.jp/odamaki3/entry-12373259657.html][32]  
            - シンクロ・モータとレゾルバの構造  
                リンク: [analog.com/jp/landing-pages/003/sensor_pv_jp/sensor_home_jp/sd_rd/sdrd_structure.html][33]  
            - レゾルバセンサについて  
                リンク: [minebeamitsumi.com/strengths/column/resolver/index.html][34]  
  
[1]: https://kotobank.jp/word/%E3%83%AA%E3%82%A2%E3%82%AF%E3%83%88%E3%83%AB-148309  
[2]: https://article.murata.com/ja-jp/article/basic-facts-about-inductors-lesson-1  
[3]: https://www.weblio.jp/content/%E3%83%AA%E3%83%A9%E3%82%AF%E3%82%BF%E3%83%B3%E3%82%B9  
[4]: http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html  
[5]: https://dl.mitsubishielectric.co.jp/dl/fa/document/catalog/gear/invertor/inverter.pdf  
[6]: https://synapse.kyoto/glossary/pwm/page001.html  
[7]: http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html  
[8]: https://physics-school.com/rotate-coordinates-equation/  
[9]: https://tech.nikkeibp.co.jp/dm/article/WORD/20090916/175328/  
[10]: https://toshiba.semicon-storage.com/jp/design-support/e-learning/mcupark/village/vector-1.html  
[11]: https://jp.mathworks.com/solutions/power-electronics-control/clarke-and-park-transforms.html  
[12]: https://www.youtube.com/watch?v=0Yd8qOfiWzQ  
[13]: https://hegtel.com/three-phase-delta.html  
[14]: http://www.mohno-dispenser.jp/img/compass/compass08/img_08_06.gif  
[15]: http://www.mohno-dispenser.jp/compass/compass08.html  
[16]: https://sites.google.com/site/cinderellajapan/_/rsrc/1363258953597/gao-xiao-shu-xue/san-jiao-bi/zheng-xian/sannkaku2.png  
[17]: https://sites.google.com/site/cinderellajapan/_/rsrc/1363258953597/gao-xiao-shu-xue/san-jiao-bi/zheng-xian/sannkaku4.png  
[18]: https://ameblo.jp/odamaki3/entry-12373760947.html  
[19]: https://www.indexpro.co.jp/article/detail/13/7  
[20]: http://energychord.com/children/energy/motor/sync/contents/sync_principle.html  
[21]: https://denki-no-shinzui.com/3872/  
[22]: https://denki-no-shinzui.com/502/  
[23]: http://www.ekouhou.net/%E3%83%A2%E3%83%BC%E3%82%BF%E5%88%B6%E5%BE%A1%E8%A3%85%E7%BD%AE/disp-A,2007-228700.html  
[24]: https://www.neomag.jp/mailmagazines/topics/letter201003.html  
[25]: https://www.giho.mitsubishielectric.co.jp/giho/pdf/2016/1603113.pdf  
[26]: https://www.e-devices.ricoh.co.jp/ja/technology/automotive/fault.html  
[27]: https://ejje.weblio.jp/content/residual  
[28]: https://ejje.weblio.jp/content/latent  
[29]: https://www.keyence.co.jp/ss/products/recorder/lab/candata/  
[30]: https://eetimes.jp/ee/spv/0912/15/news104.html  
[31]: https://japan.renesasrulz.com/cfs-file/__key/communityserver-discussions-components-files/83/RJJ05B0937_2D00_0100.pdf]  
[32]: https://ameblo.jp/odamaki3/entry-12373259657.html  
[33]: https://www.analog.com/jp/landing-pages/003/sensor_pv_jp/sensor_home_jp/sd_rd/sdrd_structure.html  
[34]: https://www.minebeamitsumi.com/strengths/column/resolver/index.html  
