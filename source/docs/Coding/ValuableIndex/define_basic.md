<hr>
<h3> #define で定義される変数名のリスト その1 </h3>  
<hr>
<br>

<h3><b>基本設定</b></h3>
<br>
<h4><b>主にconfig.hで設定する項目</b></h4>

|#define|値範囲|初期値|説明|
|--|:------:|:------:|-------------------|
|**Meridim基本設定**||||
|MRDM_LEN|1-700|90|Meridim配列の長さ|
|MRDM_BYTE|MRDM_LEN*2|180|Meridim配列のバイト型の長さ|
|FRAME_DURATION|1以上|10|1フレームあたりの単位時間(単位ms)|
|CHARGE_TIME|0以上|200|起動時のコンデンサ充電待機時間(単位ms)|
|**動作モード**||||
|MODE_ESP32_STDALONE|0,1|0|ESP32をMeridianボードに挿さずに動作確認<br>(1:する, 0:しない)|
|MODE_UDP_RECEIVE|0,1|1|PCからデータを受信(1:する, 0:しない)|
|MODE_UDP_SEND|0,1|1|PCへデータを送信(1:する, 0:しない)|
|**EEPROMの設定**||||
|EEPROM_SIZE||540|使用するEEPROMのサイズ(バイト)|
|EEPROM_SET|0,1|0|起動時にEEPROMにconfig.hの内容をセット<br>(1:する, 0:しない)|
|EEPROM_PROTECT|0,1|0|EEPROMの書き込み保護<br>(1:書き込み禁止, 0:保護しない)|
|EEPROM_LOAD|0,1|0|起動時にEEPROMの内容を諸設定に反映<br>(1:する, 0:しない)|
|EEPROM_DUMP|0,1|0|起動時のEEPROM内容のダンプ表示|
|EEPROM_FORMAT|Bin,Hex,Dec|Dec|EEPROM内容のダンプ表示の書式|
|**起動時のチェック**||||
|CHECK_SD_RW|0,1|0|SDカードリーダーの読み書きチェック|
|CHECK_EEPROM_RW|0,1|0|EEPROMの動作チェック|
|**シリアルモニタリング**||||
|MONITOR_FRAME_DELAY|0,1|0|フレーム遅延時間の表示（0:OFF, 1:ON）|
|MONITOR_FLOW|0,1|0|フロー番号の表示|
|MONITOR_ERR_SERVO|0,1|0|通信エラーのあったサーボIDの表示|
|MONITOR_ERR_ALL|0,1|0|全経路の受信エラー率の表示|
|MONITOR_SEQ|0,1|0|シーケンス番号の表示|
|MONITOR_PAD|0,1|0|リモコンデータの表示|
|MONITOR_SUPPRESS_DURATION||8000|起動直後のタイムアウトメッセージ<br>抑制時間(単位ms)|
|**マウント関連**||||
|MOUNT_SD|0,1|0|SDカードリーダーの搭載(1:あり, 0:なし)|
|MOUNT_IMUAHRS|0-3|NO_IMU|IMU/AHRSの搭載<br>(0:NO_IMU, 1:MPU6050_IMU, 2:MPU9250_IMU, 3:BNO055_AHRS)|
|MOUNT_PAD|0-5|0|ジョイパッドの搭載<br>(0:なし, 1:MERIMOTE, 2:BLUERETRO, 3:SBDBT, 4:KRR5FH, 5:Wiimote)|
|**I2C設定**||||
|I2C0_SPEED||400000|I2Cの速度(400kHz推奨)|
|IMUAHRS_INTERVAL||10|IMU/AHRSの読み取り間隔(ms)|
|IMUAHRS_STOCK||4|移動平均を取る際のフレーム数|
|I2C1_SPEED||100000|I2Cの速度|
|I2C1_MERIMOTE_ADDR||0x58|MerimoteのI2Cアドレス|
|**SPI設定**||||
|SPI_SPEED||6000000|SPI通信の速度(bps)|
|**リモコンの設定**||||
|PAD_INTERVAL||10|ジョイパッドのデータを読むフレーム間隔<br>(KRC-5FHでは4推奨)|
|PAD_BUTTON_MARGE|0,1|1|JOYPADのボタンデータをMeridim受信値に 0:論理積, 1:論理和|
|PAD_GENERALIZE|0,1|1|ジョイパッドの入力値をPS系に一般化する|
|**サーボ関連設定**||||
|MOUNT_SERVO_TYPE_L||43|L系統のサーボプロトコル|
|MOUNT_SERVO_TYPE_R||43|R系統のサーボプロトコル|
|MOUNT_SERVO_TYPE_C||43|C系統のサーボプロトコル|
|SERVO_BAUDRATE_L||1250000|L系統のサーボの通信速度(bps)|
|SERVO_BAUDRATE_R||1250000|R系統のサーボの通信速度(bps)|
|SERVO_BAUDRATE_C||1250000|C系統のサーボの通信速度(bps)|
|SERVO_TIMEOUT_L||2|L系統のサーボ返信タイムアウト時間(ms)|
|SERVO_TIMEOUT_R||2|L系統のサーボ返信タイムアウト時間(ms)|
|SERVO_TIMEOUT_C||2|C系統のサーボ返信タイムアウト時間(ms)|
|SERVO_LOST_ERR_WAIT||6|サーボ通信エラーと判定する連続エラー回数|
|**PC接続関連設定**||||
|SERIAL_PC_BPS||115200|PCとのシリアル通信の速度(bps)|
|SERIAL_PC_TIMEOUT||2000|Cとのシリアル接続確立タイムアウト(ms)|
|**Wifiアクセスポイントの設定**||||
|MODE_FIXED_IP|0,1|0|IPアドレスを固定する|
|UDP_TIMEOUT||4|UDPの待受タイムアウト時間(ms)|

<br>
<h4><b>ピンアサイン</b></h4>

|#define|LITE|TWIN|説明|
|--|:------:|:------:|-------------------|
|PIN_ERR_LED|25|2|LED用|処理が時間内に収まっていない場合に点灯|
|PIN_EN_L|33|6|L系統のサーボのENピン|
|PIN_EN_R|4|5|R系統のサーボのENピン|
|PIN_EN_C| |23|C系統のサーボのENピン|
|PIN_CHIPSELECT_SD|15|9|SDカードSPI通信用のChipSelect|
|PIN_I2C0_SDA|22||I2CのSDAピン|
|PIN_I2C0_SCL|21||I2CのSCLピン|

<br>
<h4><b>列挙型</b></h4>

|列挙型名|値:列挙子|説明|
|--|:------|-------------------|
|UartLine|0:L<br>1:R<br>2:C|サーボ系統の列挙型|
|ImuAhrsType|0:NO_IMU<br>1:MPU6050_IMU<br>2:MPU9250_IMU<br>3:BNO055_AHRS|6軸9軸センサ種の列挙型|
|PadReceiverType|0:PC<br>1:MERIMOTE<br>2:BLUERETRO<br>3:SBDBT<br>4:KRR5FH<br>5:Wiimote<br>5:Wiimote_C|リモコン種の列挙型|
|BinHexDec|0:Bin<br> 1:Hex<br>2:Dec<br>|数値表示タイプの列挙型|

<br>
<h4><b>システム用固定値</b></h4>

|定義|固定値|説明|
|--|:------:|-------------------|
|PAD_LEN|5|ジョイパッド用配列の長さ|
|MRD_ERR_u |MRD_ERR * 2 + 1|エラーフラグの格納場所(上位8ビット,エラーコード)|
|MRD_ERR_l |MRD_ERR * 2|エラーフラグの格納場所(下位8ビット,サーボエラー)|

