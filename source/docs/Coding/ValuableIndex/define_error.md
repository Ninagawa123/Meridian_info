<hr>
<h3> #define で定義される変数名のリスト その5 </h3>  
<hr>
<br>

<h3><b>エラーコード</b></h3>
<br>
<h4><b>Meridim[MRD_ERR]のエラーコード</b></h4>

|ビット|値|内容|
|--|:------||
|**上位8ビット**|||
|ERRBIT_15_ESP_PC|bit15|ESP32 → PC のUDP受信エラー (0:エラーなし, 1:エラー検出)|
|ERRBIT_14_PC_ESP |bit14|PC → ESP32 のUDP受信エラー|
|ERRBIT_13_ESP_TSY|bit13|ESP32 → TeensyのSPI受信エラー|
|ERRBIT_12_TSY_ESP|bit12|Teensy → ESP32 のSPI受信エラー|
|ERRBIT_11_BOARD_DELAY|bit11|Teensy or ESP32のシステムディレイ (末端で捕捉)|
|ERRBIT_10_UDP_ESP_SKIP|bit10|PC → ESP32 のUDPフレームスキップエラー|
|ERRBIT_9_BOARD_SKIP|bit9|PC → ESP32 → Teensy のフレームスキップエラー(末端で捕捉)|
|ERRBIT_8_PC_SKIP|bit8|Teensy → ESP32 → PC のフレームスキップエラー(末端で捕捉)|
|**下位8ビット**|||
||0-249|0:エラーなし<br>1-99:メッセージ未定義<br>100〜149:エラーサーボIndex (IXL[0~49])<br>150〜199:エラーサーボIndex (IXC[0~49])<br>200~249:エラーサーボIndex (IXR[0~49])|
