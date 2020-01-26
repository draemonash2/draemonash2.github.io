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
        - 三角波比較方式  
            リンク: [energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html][3]  
            - 概要  
                - デジタル信号(PWM)からアナログ信号を生成するための方法  
                    - ...  
                - 時間軸方向に量子化されていないPWM信号が得られるため、デジタル方式PWM変調回路よりも解像度が高い  
                - キャリア周波数を下げると、モータ騒音が大きくなりますが、インバータから発生する高周波 ノイズや、漏れ電流を減らすことができます。  
                    リンク: [dl.mitsubishielectric.co.jp/dl/fa/document/catalog/gear/invertor/inverter.pdf][4]  
                    - キャリア周波数：低⇔高  
                        モータ騒音：大⇔小  
                        漏れ電流：小⇔大  
                        ノイズ：小⇔大  
            - URL  
                - [https://synapse.kyoto/glossary/pwm/page001.html][5]  
                - [http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html][6]  
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
        - 右ねじの法則  
            - 意味  
                - ”電流”を流した時の”磁界”の向き  
                    - ...  
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
                リンク: [physics-school.com/rotate-coordinates-equation/][7]  
                - ![固定座標→回転座標](固定座標→回転座標.jpg)  
            - 弱め界磁  
                リンク: [tech.nikkeibp.co.jp/dm/article/WORD/20090916/175328/][8]  
                - 界磁に永久磁石を用いたモータでは永久磁石の磁束が一定なので，回転数が上がるにつれて同磁束によって生じる逆起電力が増加する。  
                    そして，ある回転数に達すると，この逆起電力がモータの印加電圧と等しくなる。それにより，モータには電流を流せなくなり，それよりも回転数を上げることができなくなる。これを防ぐために用いるのが手法。  
            - 参考URL  
                - ベクトルエンジンとベクトル制御  
                    リンク: [toshiba.semicon-storage.com/jp/design-support/e-learning/mcupark/village/vector-1.html][9]  
                - Clarke-Park 変換  
                    リンク: [jp.mathworks.com/solutions/power-electronics-control/clarke-and-park-transforms.html][10]  
                - マイコン：モータ駆動用ベクトル制御技術  
                    リンク: [youtube.com/watch][11]  
            - 他の用語  
                - dq軸  
                    - d：磁界成分  
                    - q：トルク成分  
        - 相電流と線間電圧  
            リンク: [hegtel.com/three-phase-delta.html][12]  
        - 参考URL  
            - 同期機  
                リンク: [energychord.com/children/energy/motor/sync/contents/sync_principle.html][13]  
            - パーク変換法の導入  
                リンク: [denki-no-shinzui.com/3872/][14]  
            - クラーク変換法の導入  
                リンク: [denki-no-shinzui.com/502/][15]  
            - レゾルバオフセット調整の目的と方法  
                リンク: [ekouhou.net/%E3%83%A2%E3%83%BC%E3%82%BF%E5%88%B6%E5%BE%A1%E8%A3%85%E7%BD%AE/disp-A,2007-228700.html][16]  
            - モータの基礎と永久磁石  
                リンク: [neomag.jp/mailmagazines/topics/letter201003.html][17]  
            - 三菱電機製ベルト駆動式モータジェネレーター  
                リンク: [giho.mitsubishielectric.co.jp/giho/pdf/2016/1603113.pdf][18]  
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
                リンク: [ameblo.jp/odamaki3/entry-12373259657.html][19]  
            - シンクロ・モータとレゾルバの構造  
                リンク: [analog.com/jp/landing-pages/003/sensor_pv_jp/sensor_home_jp/sd_rd/sdrd_structure.html][20]  
            - レゾルバセンサについて  
                リンク: [minebeamitsumi.com/strengths/column/resolver/index.html][21]  
  
[1]: https://kotobank.jp/word/%E3%83%AA%E3%82%A2%E3%82%AF%E3%83%88%E3%83%AB-148309  
[2]: https://article.murata.com/ja-jp/article/basic-facts-about-inductors-lesson-1  
[3]: http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html  
[4]: https://dl.mitsubishielectric.co.jp/dl/fa/document/catalog/gear/invertor/inverter.pdf  
[5]: https://synapse.kyoto/glossary/pwm/page001.html  
[6]: http://energychord.com/children/energy/pe/inv/contents/inv_pwm_tri.html  
[7]: https://physics-school.com/rotate-coordinates-equation/  
[8]: https://tech.nikkeibp.co.jp/dm/article/WORD/20090916/175328/  
[9]: https://toshiba.semicon-storage.com/jp/design-support/e-learning/mcupark/village/vector-1.html  
[10]: https://jp.mathworks.com/solutions/power-electronics-control/clarke-and-park-transforms.html  
[11]: https://www.youtube.com/watch?v=0Yd8qOfiWzQ  
[12]: https://hegtel.com/three-phase-delta.html  
[13]: http://energychord.com/children/energy/motor/sync/contents/sync_principle.html  
[14]: https://denki-no-shinzui.com/3872/  
[15]: https://denki-no-shinzui.com/502/  
[16]: http://www.ekouhou.net/%E3%83%A2%E3%83%BC%E3%82%BF%E5%88%B6%E5%BE%A1%E8%A3%85%E7%BD%AE/disp-A,2007-228700.html  
[17]: https://www.neomag.jp/mailmagazines/topics/letter201003.html  
[18]: https://www.giho.mitsubishielectric.co.jp/giho/pdf/2016/1603113.pdf  
[19]: https://ameblo.jp/odamaki3/entry-12373259657.html  
[20]: https://www.analog.com/jp/landing-pages/003/sensor_pv_jp/sensor_home_jp/sd_rd/sdrd_structure.html  
[21]: https://www.minebeamitsumi.com/strengths/column/resolver/index.html  
