<hr>
<h3> #define で定義される変数名のリスト #4 </h3>  
<hr>
<br>

<h3><b>Meridim マスターコマンド定義</b></h3>


|#define|コマンド値|説明|
|--|:------:|-------------------|
|MCMD_TORQUE_ALL_OFF|0|すべてのサーボトルクをオフにする（脱力）|
||1-999|Meridimの配列長|
|MCMD_UPDATE_YAW_CENTER|10002|センサの推定ヨー軸を現在値でゼロに|
|MCMD_ENTER_TRIM_MODE|10003|トリムモードに入る<br>全サーボオンで起立姿勢|
|MCMD_CLEAR_SERVO_ERROR_ID|10004|通信エラーのサーボのIDをクリア|
|MCMD_BOARD_TRANSMIT_ACTIVE|10005|ボードが定刻で送信を行うモード<br>（デフォルト設定.PC側が受信待ち）|
|MCMD_BOARD_TRANSMIT_PASSIVE|10006|ボードが受信を待ち返信するモード<br>（PC側が定刻送信）|
