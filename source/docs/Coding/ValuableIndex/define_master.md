<hr>
<h3> #define で定義される変数名のリスト その4 </h3>  
<hr>
<br>

<h3><b>Meridim マスターコマンド定義</b></h3>
<br>
<h4><b>書式: meridim[MRD_MASTER] == コマンド値</b></h4>

|#define|コマンド値|説明|
|--|:------:|-------------------|
| MCMD_TORQUE_ALL_OFF | 0 | すべてのサーボトルクをオフにする（脱力） |
| MCMD_DUMMY_DATA | -32768 | SPI送受信用のダミーデータ判定用 |
| MCMD_SENSOR_YAW_CALIB | 10002 | センサの推定ヨー軸を現在値センターとしてリセット |
| MCMD_SENSOR_ALL_CALIB | 10003 | センサの3軸について現在値を原点としてリセット |
| MCMD_ERR_CLEAR_SERVO_ID | 10004 | 通信エラーのサーボのIDをクリア<br>(MRD_ERR_l = 0)|
| MCMD_BOARD_TRANSMIT_ACTIVE | 10005 | ボードが定刻で送信を行うモード<br>(PC側が受信待ち)|
| MCMD_BOARD_TRANSMIT_PASSIVE | 10006 | ボードが受信を待ち返信するモード<br>(PC側が定刻送信) |
| MCMD_FRAMETIMER_RESET | 10007 | フレームタイマーを現在時刻にリセット |
| MCMD_BOARD_STOP_DURING | 10008 | ボードの末端処理を<br>[MRD_STOP_FRAMES]ミリ秒止める |
| MCMD_EEPROM_ENTER_WRITE | 10009 | EEPROM書き込みモードのスタート |
| MCMD_EEPROM_EXIT_WRITE | 10010 | EEPROM書き込みモードの終了 |
| MCMD_EEPROM_ENTER_READ | 10011 | EEPROM読み出しモードのスタート |
| MCMD_EEPROM_EXIT_READ | 10012 | EEPROM読み出しモードの終了 |
| MCMD_SDCARD_ENTER_WRITE | 10013 | SDCARD書き込みモードのスタート |
| MCMD_SDCARD_EXIT_WRITE | 10014 | SDCARD書き込みモードの終了 |
| MCMD_SDCARD_ENTER_READ | 10015 | SDCARD読み出しモードのスタート |
| MCMD_SDCARD_EXIT_READ | 10016 | SDCARD読み出しモードの終了 |