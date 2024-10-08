# Boards
  
<br>  
### 概念としての動作環境  
Meridianのコアは中間プロトコルであるため, 理屈上, なんらかの形で通信を行うことができ, かつプログラム可能なデバイス上であればなんでも動きます.   
実質的には, 小型サーボで多く採用されている半二重のUART通信や多くのセンサで使われているI2C, SPIなどが使えることが必要になると思います.   
また100Hzの速度を実現するために, ある程度の処理速度が求められます. (ESP32は20個程度のサーボをギリギリ処理できます. )
回路図をgithubで公開しているので, Meridian対応のボードをユーザーが作成することもできます.   
  
<br>  
### 現実的な最小限の動作環境  
最小限の動作であれば, 100Hzのwifi通信を含んだ動作検証を, ESP32 DevkitC単体で行うことができます.   
ESP32 DevkitCは秋月電子で1,600円で購入することができます(2024.7月現在).   
ブレッドボードにMAX485などの半二重回路などをレイアウトすることで, サーボ動作についても検証できると思います. 
  
<br>  
### より具体的な動作環境  
半二重回路やI2C, SPIののピン出力を持った完成済みの評価ボードを, 以下のサイトで頒布しています.   
[https://1985b.booth.pm/](https://1985b.booth.pm/)  
