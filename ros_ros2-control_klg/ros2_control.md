
# ros2_control

[トップに戻る](../index.md)

## TODO＆疑問

- [effort_controllers](https://control.ros.org/master/doc/ros2_controllers/effort_controllers/doc/userdoc.html)とは？
    - →目標位置や目標速度ではなく、トルクのような「力」を支持するコントローラー
- Hardware ComponentsのSensor、Actuator、Systemの利用用途の違いは？  
SystemがState InterfaceとCommand Interfaceどちらもエクスポートできるなら、SensorとActuatorはいらないのでは？
    → Systemは複雑な操作ができるらしい([こちら](https://github.com/ros-controls/roadmap/blob/master/design_drafts/ros2_control_documentation.rst#hardware-components))
- ジョイントとリンクの違いは？
    - 人間の体で言えば、肘や肩など自由に曲がる部分が「ジョイント」、その間を繋ぐ骨の部分が「リンク」[[1]](https://robotics.kawasaki.com/ja1/xyz/jp/1804-03/)
        - [joint](https://www.ei-navi.jp/dictionary/content/joint/)：[名] 関節
        - [link](https://www.ei-navi.jp/dictionary/content/link/)：[名] 連結するもの，つながり；（鎖の）輪
- YAMLファイルとXACROファイルの設定項目の違いは？
    - →XACROはHardware（HardwareInterface）側の設定、YAMLはController（ControllerManager）側の設定…？
- ★「command interfaceやstate interfaceでやり取りする」とは具体的にどういったことなのかがわからない
- ★update()（controller）とかread()/write()（HardwareInterface）とかのシーケンス図を作る
- ★StateInterfaceとCommandInterfaceはCMとRM間のやり取りと認識している。[demoのexample_1](https://github.com/ros-controls/ros2_control_demos/tree/master/example_1)上で、HWとの実際のやり取りしている個所はどこ？

## 用語

- [DoF（degrees of freedom）](https://github.com/ros-controls/roadmap/blob/master/design_drafts/ros2_control_documentation.rst#hardware-components)
    - 自由度[[1]](https://ja.wikipedia.org/wiki/6DoF)
- [6DoF（Six Degrees of Freedom）](https://github.com/ros-controls/roadmap/blob/master/design_drafts/ros2_control_documentation.rst#hardware-components)
    - 3次元において剛体が取り得る動きの自由度のことである。  
    具体的には、前または後・上または下・左または右に（別の言い方では3次元の直交座標系の軸に沿って）動くことができ、また直交座標系の3軸おのおのの周囲を回転できることを指す。[[1]](https://ja.wikipedia.org/wiki/6DoF)
- [パラレルグリッパ](https://github.com/ros-controls/roadmap/blob/master/design_drafts/ros2_control_documentation.rst#hardware-description-in-urdf)
    - 二つの板でつかむ装置
        - [★](https://www.techshare-store.jp/product/85)
- [effort]()
    - 《物理》〔てこなどに〕加える力、〔てこの原理の〕力点 [[1]](https://eow.alc.co.jp/search?q=effort)
    - 引用元）effort controller

## 参考URL

- [ros2_controlを使ってみた | アールティ ヒューマノイドロボットブログ (rt-net.jp)](https://rt-net.jp/humanoid/archives/3571)
- [roadmap/design_drafts/ros2_control_documentation.rst](https://github.com/ros-controls/roadmap/blob/master/design_drafts/ros2_control_documentation.rst)

[トップに戻る](../index.md)
