<hr>
<h3> Meridim : Meridim配列の概要 </h3>  
<hr>
<br>
Meridim配列は16bit(2byte)を１要素とした可変長の配列で、  
ロボットの状態データやコマンドをコンパクトに格納することができます。  
使い勝手のために**基本形の長さを[90]と定めており、これをMeridim90**と呼びます。  
Meridim配列の長さはユーザーが自由に設定できますが、Ethernetの１パケット(1フレーム)に収まるデータ量が1472バイトであることから、目安として
**Meridim[700] 程度を上限**と想定しています。  
このシステムの目的はマイコンでのリアルタイム処理であるため、要素数はできるだけコンパクトな方がよいでしょう。  
<br>

以下にMeridim90を例として、配列の概要を説明します。  


|Meridim90 配列番号|配列番号キー|説明|
|:--|:---|---------------|
|index [0]|MRD_MASTER|マスターコマンド|  
|index [1]|MRD_SEQENTIAL|シーケンス番号|  
|index [2]-[4]|MRD_ACC_X,Y,Z|加速度センサ値|  
|index [5]-[7]|MRD_GYRO_X,Y,Z|ジャイロセンサ値|  
|index [8]-[10]|MRD_MAG_X,Y,Z|磁気コンパス値|  
|index [11]|MRD_TEMP|温度センサ値|  
|index [12]-[14]|MRD_DIR_ROLL,PITCH,YAW|DMP推定方向値|  
|index [15]|MRD_CONTROL_BUTTONS|リモコンボタン|  
|index [16]|MRD_CONTROL_STICK_R|リモコン右スティックxy|
|index [17]|MRD_CONTROL_STICK_L|リモコン左スティックxy|
|index [18]|MRD_CONTROL_L2R2ANALOG|リモコンL2R2アナログ|
|index [19]|MRD_MOTION_FRAMES|モーション設定のフレーム数|
|index [20]-[49]||左系統サーボのコマンドと値|
|index [50]-[79]||左系統サーボのコマンドと値|
|index [80]-[87]|MRD_USERDATA_xx|ユーザー定義用|
|index [88]|MRD_ERROR_CODE|エラーコード (index[MSG_SIZE-2])|
|index [89]|MRD_CHECKSUM|チェックサム (index[MSG_SIZE-1])|




