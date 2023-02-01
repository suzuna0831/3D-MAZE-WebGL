# 3D-MAZE-WebGL
以前作った3D迷路生成器をWeb上で試せるようにしました。  
WebGLのラッパであるThree.jsを使ってリアルタイムレンダリングによる3DCGを行ってます。
  
https://naohcodes.github.io/3D-MAZE-WebGL/  
↓生成過程を見たい人  
https://naohcodes.github.io/3D-MAZE-WebGL/time.html
  
   
迷路生成器  
https://github.com/naohCodeS/MazeGenerator

# 注意・Tips
- 時間経過で壁を伸ばすほう（time.html）で大きいサイズの迷路を作ろうとすると処理落ちすることがあります（10000セルを超えないようにしたほうが良いです）
- スマホ用のレイアウトは未作成なのでPC推奨です。（入力がかなりやりづらいはずです）
- 3辺のうち1辺を3にすることで平面の迷路が生成できます

# 実行時間

実行時間は迷路のセル数に理論的に比例するはずです。  
（立方体の迷路とし計測しましたが、セル数が同じであれば実行時間もさほど変わりません。）  

## 環境

- Windows 11
- IntelliJ IDEA 2023.3.1  


デバッグモードで実行

## 結果

計測した実行時間は以下の通りです。  

- SIZE_X : 一辺の長さ
- SIZE : 総セル数（SIZE_X^3）
- Generating time : 迷路生成にかかった時間
- Rendering time : 描画にかかった時間

![image](https://user-images.githubusercontent.com/75174022/215410313-8c70607e-b668-4d01-ba18-3aa492185880.png)

101x101x101の迷路で約3分かかりました。

## Generating time
迷路生成にかかった時間をもう少し詳しく見ます。  
グラフにすると以下の通りです。  
![image](https://user-images.githubusercontent.com/75174022/215411871-872f6246-f4a5-4f6e-b8a2-5569ff5dee51.png)
  
理論的には迷路生成の計算量はNを総セル数とすれば $O(N)$ 、すなわち、計算量は総セル数に比例はずですが、実際には総セル数にしたがって大きくなる倍数がかかるようです。
（総セル数を増やせば線形に近づく可能性もあるかな？時間があるときに考えます。）  

## Rendering time
描画にかかった時間は以下の通り総セル数に比例します。  
迷路生成にかかった時間と比べて小さいため、実行時間としては無視できます。
![image](https://user-images.githubusercontent.com/75174022/215414561-bd3ed0db-0e53-4be0-959e-c9f213ced54b.png)
