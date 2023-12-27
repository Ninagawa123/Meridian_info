<hr>
<h3> ローカル変数名のリスト #1 </h3>  
<hr>
<br>
<h4><b>バージョン表示</b></h4>
|型|変数名|バージョン書式|説明|
|--|------|-------------------|------------------|
|#define|VERSION|"Meridian_xxx_for_xxx_20xx.xx.xx"|バージョン表示|

<br>
<h4><b>インスタンス</b></h4>
|型|クラス名（引数）|使用ライブラリ|
|--|------|-------------------|
|MERIDIANFLOW::Meridian|mrd|Meridian.h|
|WiFiUDP|udp|WiFiUdp.h|
|ESP32DMASPI::Slave|slave|ESP32DMASPISlave.h|
|ESP32Wiimote|wiimote|ESP32Wiimote.h|
|MPU6050|mpu6050|ESP32Wiimote.h|
|IcsHardSerialClass|krs_L(&Serial2, PIN_EN_L, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|
|IcsHardSerialClass|krs_R(&Serial3, PIN_EN_R, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|
|IcsHardSerialClass|krs_3(&Serial1, PIN_EN_3, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|

<br>
<h4><b>Meridim配列用の共用体</b></h4>
※ DMA使用時に配列末尾のデータが欠損する仕様を回避するため、配列要素を多くすることで対策。

|共用体設定|説明|
|------|-------------------|
|typedef union{<br>short sval[MSG_SIZE + 4];<br>unsigned short usval[MSG_SIZE + 2];<br>uint8_t bval[MSG_BUFF + 4];<br>} UnionData;|<br>.sval short型<br>.usval unsigned short型<br>.bval bite型 <br>UnionData この共用体の型名|

|共用体型名|変数名|説明|
|--|------|-------------------|
|UnionData|s_spi_meridim|Meridim配列データ(short型,センサや角度は100倍値)|
|UnionData|r_spi_meridim|Meridim配列データ(short型,センサや角度は100倍値)|
|UnionData|s_spi_meridim_dma|SPI送信用|
|UnionData|r_spi_meridim_dma|SPI受信用|
|UnionData|s_udp_meridim|UDP送信用|
|UnionData|r_udp_meridim|UDP受信用|

<br>
<h4><b>システム用</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|uint8_t|*s_spi_meridim_dma|DMA送信用|
|uint8_t|*r_spi_meridim_dma|DMA受信用|
|TaskHandle_t|thp[4]|マルチスレッドのタスクハンドル格納用|
|File|myFile|SDカード用|
|int|servo_num_max<br>= max(max(MOUNT_SERVO_NUM_L, MOUNT_SERVO_NUM_R), MOUNT_SERVO_NUM_3)|サーボ送受信のループ処理数（L系R系で多い方）|

★廃止 int servo_num = max(MOUNT_SERVO_NUM_L, MOUNT_SERVO_NUM_R); // サーボ送受信のループ処理数（L系R系で多い方）

<br>
<h4><b>フラグ用</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|bool|flag_spi_ready|SPI送信の順番制御用|
|bool|flag_udp_busy|UDPスレッドでの受信中フラグ（送信抑制）|
|bool|flag_udp_rsvd|UDPスレッドでの受信完了フラグ|
|bool|flag_imuahrs_available|IMU/AHRSセンサ値へのアクセスセマフォ|

★廃止 int frame_sync_r_expect = 0; // フレーム毎に前回受信値に+１として受信値と比較（-30000~29999)<br>
★廃止 spi_ready_flag<br>
★廃止 udp_rsvd_flag<br>
★廃止 udp_busy_flag<br>
★廃止 flag_sensor_IMUAHRS_writable<br>

<br>
<h4><b>タイマー関連</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|long|frame_ms = FRAME_DURATION|1フレームあたりの単位時間(ms)|
|long|mrd_t_mil = (long)millis()|Meridianフレーム管理時計の時刻|
|long|now_t_mil = (long)millis()|現在時刻をミリ秒で取得|
|long|now_t_mic = (long)micros()|現在時刻をマイクロ秒で取得|
|int|frame_count|サイン計算用の変数|
|int|frame_count_diff|サインカーブ動作などのフレームカウントをいくつずつ進めるか|
|int|frame_count_max = 360000|フレームカウントの最大値|
|int|joypad_polling_count|JOYPADのデータを読みに行くためのフレームカウント|
|int|mrd_seq_s_increment|フレーム毎にシーケンス番号0-59999をカウントし、送信|
|int|mrd_seq_r_expect|フレーム毎に0-59999をカウントし、受信シーケンス番号と比較|
|int|mrd_seq_r|今フレームに受信したframe_syncを格納|

★廃止 long merc = (long)millis();      // フレーム管理時計の時刻 Meridian Clock.<br>
★廃止 long curr = (long)millis();      // 現在時刻を取得<br>
★廃止 long curr_micro = (long)micros();// 現在時刻を取得<br>
★廃止 int meridim_seq_s_increment = 0; // フレーム毎に0-59999をカウントし、送信<br>
★廃止 int meridim_seq_r_expect = 0;    // フレーム毎に0-59999をカウントし、受信値と比較<br>
★廃止 int meridim_seq_r = 0;           // 今フレームを格納<br>
★廃止 joypad_frame_count               //JOYPADのデータを読みに行くためのフレームカウント<br>
<br>
<h4><b>エラー監視用</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|int|err_esp_pc|PCの受信エラー回数（ESP32からのUDP）|
|int|err_pc_esp|ESP32の受信エラー回数（PCからのUDP）|
|int|err_esp_tsy|Teensyの受信エラー回数（ESP32からのSPI）|
|int|err_tsy_esp|ESP32の受信エラー回数（TeensyからのSPI）|
|int|err_esp_skip|ESPの受信シーケンス番号スキップ回数（UDP）|
|int|err_tsy_skip|Teensyの受信シーケンス番号スキップ回数（ESP経由UDP）|
|int|err_pc_skip|PCの受信シーケンス番号スキップ回数（UDP）|

★廃止 int spi_ok = 0;<br>
★廃止 int spi_trial = 0;<br>

<br>
<h4><b>モード切り替え関連</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|bool|trim_adjust = TRIM_ADJUST_MODE|トリムモードのオンオフ|
|bool|monitor_all_error = MONITOR_ALL_ERROR|全経路の受信エラー率シリアル表示|

<br>
<h4><b>wifi用</b></h4>
|型|変数名|説明|
|--|------|-------------------|

<br>
<h4><b>bluetooth用</b></h4>
|型|変数名|説明|
|--|------|-------------------|


<br>
<h4><b>リモコン関連</b></h4>
|リモコン用共用体設定|説明|
|------|-------------------|
|typedef union{<br>short sval[4];<br>uint16_t usval[4];<br>int8_t bval[8];<br>uint8_t ubval[8];<br>uint64_t ui64val[1];<br>} UnionPad;|<br>short型で4個の配列データを持つ<br>上記のunsigned short型<br>上記のbyte型<br>上記のunsigned byte型<br>上記のunsigned int16型<br>UnionPad この共用体の型名|

|[0]16bit|[1]上位8bit|[1]下位8bit|[2]上位8bit|[2]下位8bit|[3]上位8bit|[3]下位8bit|
|---|---|---|---|---|---|---|
|button|pad_stick_L_x|pad_stick_L_y|pad_stick_R_x|pad_stick_R_y|pad_L2_val|pad_R2_val|

|共用体型名|変数名|説明|
|--|------|-------------------|
|UnionPad|pad_array|リモコン値格納用の配列|

|型|変数名|説明|
|--|------|-------------------|
|unsigned short|pad_stick_R|受信ジョイスティックデータy|
|int|pad_stick_R_x|受信ジョイスティックデータRx|
|int|pad_stick_R_y|受信ジョイスティックデータRy|
|unsigned short|pad_stick_L|受信ジョイスティックデータL|
|int|pad_stick_L_x|受信ジョイスティックデータLx|
|int|pad_stick_L_y|受信ジョイスティックデータLy|
|unsigned short|pad_stick_L2R2V|受信ジョイスティックデータL2R2アナログ|
|int|pad_R2_val|受信ジョイスティックデータL2アナログ|
|int|pad_L2_val|受信ジョイスティックデータR2アナログ|

★廃止 unsigned short pad_array[] ={0, 0, 0, 0};//button, pad_stick_L_x:pad_stick_L_y, pad_stick_R_x:pad_stick_R_y, pad_L2_val:pad_R2_val<br>
★廃止 unsigned short button_1 = 0; // 受信ボタンデータ1群<br>
★廃止 unsigned short button_2 = 0; // 受信ボタンデータ2群<br>
★廃止 short stick_Rx = 0;          // <br>
★廃止 short stick_Ry = 0;          // 受信ジョイスティックデータRy<br>
★廃止 short stick_Lx = 0;          // 受信ジョイスティックデータLx<br>
★廃止 short stick_Ly = 0;          // 受信ジョイスティックデータLy<br>
★廃止? int joypad_search = 3;<br>

<br>
<h4><b>センサー関連</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|float|imuahrs_yaw_origin|IMU/AHRSのヨー軸方向の原点補正値|
|<b>MPU6050用</b>|||
|MPU6050|mpu|MPU6050取り扱い用のインスタンス|
|uint8_t|mpuIntStatus|holds actual interrupt status byte from MPU|
|uint8_t|devStatus|return status after each device operation (0 = success, !0 = error)|
|uint16_t|packetSize|expected DMP packet size (default is 42 bytes)|
|uint8_t|fifoBuffer[64]|FIFO storage buffer|
|Quaternion|q|[w, x, y, z] quaternion container|
|VectorFloat|gravity|[x, y, z] gravity vector|
|float|ypr[3]|[roll, pitch, yaw] value container|
|float|mpu_read[16]|mpuから読み込んだ一次データ<br>acc_x,y,z,gyro_x,y,z,mag_x,y,z,gr_x,y,z,rpy_r,p,y,temp|
|float|mpu_zeros[16] = {0}|リセット用|
|float|mpu_ave_data[16]|移動平均値計算用（データ格納）|
|float|mpu_result[16]|加工後の最新のmpuデータ（二次データ）|
|float|mpu_stock_data[IMUAHRS_STOCK][16]|移動平均値計算用のデータストック|
|int|mpu_stock_count = 0|移動平均値計算用|
|VectorInt16|aa|[x, y, z] 加速度センサの測定値|
|VectorInt16|gyro|[x, y, z] 角速度センサの測定値|
|VectorInt16|mag|[x, y, z] 磁力センサの測定値|
|long|temperature|センサの温度測定値|
|<b>BNO055用</b>|||
|Adafruit_BNO055|bno = Adafruit_BNO055(55, 0x28, &Wire)|BNO055取り扱い用のインスタンス|

★廃止 float yaw_center //ヨー軸方向の原点リセット用<br>
<br>
<h4><b>サーボボジション関連</b></h4>
|型|変数名|単位|説明|
|--|------||-------------------|
|int|idl_mount[15]|0,1|サーボのマウント有無 IDL_MT[0] ~[14]に対応 (L系統)|
|int|idr_mount[15]|0,1|サーボのマウント有無 IDR_MT[0] ~[14]に対応 (R系統)|
|int|id3_mount[15]|0,1|サーボのマウント有無 ID3_MT[0] ~[14]に対応 (3系統)|
|int|idl_cw[15]|-1,1|サーボの回転方向補正 IDL_CW[0] ~[14]に対応 (L系統)|
|int|idr_cw[15]|-1,1|サーボの回転方向補正 IDR_CW[0] ~[14]に対応 (R系統)|
|int|id3_cw[15]|-1,1|サーボの回転方向補正 ID3_CW[0] ~[14]に対応 (3系統)|
|float|idl_trim[15]|degree|サーボの直立ポーズトリム値 IDL_TRIM[0] ~[14]に対応 (L系統)|
|float|idr_trim[15]|degree|サーボの直立ポーズトリム値 IDR_TRIM[0] ~[14]に対応 (R系統)|
|float|id3_trim[15]|degree|サーボの直立ポーズトリム値 ID3_TRIM[0] ~[14]に対応 (3系統)|
|float|idl_tgt[15]|degree|サーボの目標値格納 (L系統)|
|float|idr_tgt[15]|degree|サーボの目標値格納 (R系統)|
|float|id3_tgt[15]|degree|サーボの目標値格納 (3系統)|
|float|idl_tgt_past[15]|degree|前回の目標位置 (L系統)|
|float|idr_tgt_past[15]|degree|前回の目標位置 (R系統)|
|float|id3_tgt_past[15]|degree|前回の目標位置 (3系統)|
|int|idl_err[15]||サーボのエラーカウンタ格納 (L系統)|
|int|idr_err[15]||サーボのエラーカウンタ格納 (R系統)|
|int|id3_err[15]||サーボのエラーカウンタ格納 (3系統)|
|int|k||計算用変数|

★廃止 float r_servo_pos_L[15] = {0}; // 15要素 degree値<br>
★廃止 float r_servo_pos_R[15] = {0}; // 15要素<br>
★廃止 float idl_diff[15]; // L系統<br>
★廃止 float idr_diff[15]; // R系統<br>
★廃止 float idl_diff_past[15]//前回のサーボ値のキープ用<br>
★廃止 float idr_diff_past[15]//前回のサーボ値のキープ用<br>
★廃止 float id3_diff_past[15]//前回のサーボ値のキープ用<br>
★廃止 int s_servo_pos_L[15]//サーボのポジション格納<br>
★廃止 int s_servo_pos_R[15]//サーボのポジション格納<br>
★廃止 int s_servo_pos_3[15]//サーボポジション格納<br>
★廃止 int s_servo_err_L[15]//サーボのエラーカウンタ格納<br>
★廃止 int s_servo_err_R[15]//サーボのエラーカウンタ格納<br>
★廃止 int s_servo_err_3[15]//サーボのエラーカウンタ格納<br>
