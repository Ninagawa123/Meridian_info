<hr>
<h3> ローカル変数名のリスト </h3>  
<hr>
<br>
<h4><b>バージョン表示</b></h4>
|型|変数名|バージョン書式|説明|
|--|------|-------------------|------------------|
|#define|VERSION|"Meridian_xxx_for_xxx_20yy.mm.dd"|バージョン表示|

<br>
<h4><b>ライブラリのインスタンス</b></h4>
|型|インスタンス名|使用ライブラリ|
|--|------|-------------------|
|MERIDIANFLOW::Meridian|mrd|Meridian.h|
|WiFiUDP|udp|WiFiUdp.h|
|ESP32DMASPI::Slave|slave|ESP32DMASPISlave.h|
|ESP32Wiimote|wiimote|ESP32Wiimote.h|
|File|sd_file|SD.h|
|MPU6050|mpu6050|ESP32Wiimote.h|
|IcsHardSerialClass|ics_L(&Serial2, PIN_EN_L, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|
|IcsHardSerialClass|ics_R(&Serial3, PIN_EN_R, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|
|IcsHardSerialClass|ics_C(&Serial1, PIN_EN_3, ICS_BAUDRATE, ICS_TIMEOUT)|IcsHardSerialClass.h|

<br>
<h4><b>Meridim配列用の共用体</b></h4>
※ DMA使用時に配列末尾のデータが欠損する仕様を回避するため、配列要素を多くすることで対策。

|Meridim90Union共用体設定|説明|
|------|-------------------|
|typedef Union {<br>short sval[MRDM_LEN + 4];<br>unsigned short usval[MRDM_LEN + 2];<br>uint8_t bval[  + 4];<br>uint8_t ubval[MRDM_BYTE + 4];<br>} <b>Meridim90Union</b>;|<br>short型で90個の配列データを持つ<br>上記のunsigned short型<br>byte型で180個の配列データを持つ<br>上記のunsigned byte型<br>共用体型名|
|**インスタンス名**||
|s_spi_meridim|Meridim配列データ(short型,センサや角度は100倍値)|
|r_spi_meridim|Meridim配列データ(short型,センサや角度は100倍値)|
|s_spi_meridim_dma|SPI送信用|
|r_spi_meridim_dma|SPI受信用|
|s_spi_meridim_dummy|送信ダミー用|
|s_udp_meridim|UDP送信用|
|r_udp_meridim|UDP受信用|
|s_udp_meridim_dummy|送信ダミー用|

<br>
<h4><b>リモコン値格納用の共用体</b></h4>

|共用体設定|説明|
|------|-------------------|
|typedef union {<br>short sval[PAD_LEN];<br>uint16_t usval[PAD_LEN];<br>int8_t bval[PAD_LEN * 2];<br>uint8_t ubval[PAD_LEN * 2];<br>uint64_t ui64val[1];<br>} <b>PadUnion</b>;|<br>short型で4個の配列データを持つ<br>unsigned short型<br>byte型で8個の配列データを持つ<br>unsigned byte型<br>unsigned int16型の配列データを持つ<br>共用体型名|
|**インスタンス名**||
|pad_array||
|pad_array[0]|ボタンデータのビットフラグ|
|pad_array[1]|上位8ビット(int_8):pad.stick_L_x,<br>下位8ビット(int_8):pad.stick_L_y|
|pad_array[2]|上位8ビット(int_8):pad.stick_R_x,<br>下位8ビット(int_8):pad.stick_R_y|
|pad_array[3]|上位8ビット(uint_8):pad.L2_val,<br>下位8ビット(uint_8):pad.R2_val|

<br>
<h4><b>リモコン値格納用の共用体(I2C,MERIMOTE用)</b></h4>

|共用体設定|説明|
|------|-------------------|
|typedef union {<br>short sval[PAD_I2C_LEN];<br>uint16_t usval[PAD_I2C_LEN];<br>int8_t bval[PAD_I2C_LEN * 2];<br>uint8_t ubval[PAD_I2C_LEN * 2];<br>} <b>PadUnionWire</b>;|<br>short型で5個の配列データを持つ<br>unsigned short型<br>byte型で10個の配列データを持つ<br>unsigned byte型<br>共用体型名|
|**インスタンス名**||
|pad_i2c||
|pad_i2c[0]|ボタンデータのビットフラグ|
|pad_i2c[1]|上位8ビット(int_8):pad.stick_L_x,<br>下位8ビット(int_8):pad.stick_L_y|
|pad_i2c[2]|上位8ビット(int_8):pad.stick_R_x,<br>下位8ビット(int_8):pad.stick_R_y|
|pad_i2c[3]|上位8ビット(uint_8):pad.L2_val,<br>下位8ビット(uint_8):pad.R2_val|
|pad_i2c[4]|チェックサム|

<br>
<h4><b>リモコン値格納用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>PadValue</b> {<br>unsigned short stick_R = 0;<br>int stick_R_x = 0;<br>int stick_R_y = 0;<br>unsigned short stick_L = 0;<br>int stick_L_x = 0;<br>int stick_L_y = 0;<br>unsigned short stick_L2R2V = 0;<br>int R2_val = 0;<br>int L2_val = 0;<br>};|<br>stick_R: 右スティックの値<br>stick_R_x: 右スティックのX軸値<br>stick_R_y: 右スティックのY軸値<br>stick_L: 左スティックの値<br>stick_L_x: 左スティックのX軸値<br>stick_L_y: 左スティックのY軸値<br>stick_L2R2V: L2とR2の値<br>R2_val: R2ボタンの値<br>L2_val: L2ボタンの値|
|**インスタンス名**||
|pad||

<br>
<h4><b>フラグ用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>MrdFlags</b> {<br>bool imuahrs_available = true;<br>bool udp_board_passive = false;<br>bool frame_timer_reset = false;<br>bool stop_board_during = false;<br>bool eeprom_write_mode = false;<br>bool eeprom_read_mode = false;<br>bool eeprom_protect = EEPROM_PROTECT;<br>bool eeprom_load = EEPROM_LOAD;<br>bool eeprom_set = EEPROM_SET;<br>bool sdcard_write_mode = false;<br>bool sdcard_read_mode = false;<br>bool wire0_init = false;<br>bool wire1_init = false;<br>bool udp_rcvd = false;<br>bool meridim_rcvd = false;<br>};|<br>センサ値を読み取る間, スレッドによる書き込みを待機<br>UDP通信の周期制御がボード主導(false) か, PC主導(true)か<br>フレーム管理時計をリセットする<br>ボードの末端処理をmeridim[19]秒ミリ秒だけ止める<br>EEPROMへの書き込みモード<br>EEPROMからの読み込みモード<br>EEPROMの書き込みプロテクト<br>起動時にEEPROMの内容を読み込む<br>起動時にEEPROMに規定値をセット<br>SDCARDへの書き込みモード<br>SDCARDからの読み込みモード<br>I2C 0系統の初期化合否<br>I2C 1系統の初期化合否<br>UDPが受信できたか<br>Meridimが正しく受信できたか(シーケンス番号判断)|
|**インスタンス名**||
|flg||

<br>
<h4><b>シーケンス番号用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>MrdSq</b> {<br>int s_increment = 0;<br>int r_expect = 0;<br>};|<br>送信用にフレーム毎に0-59999をカウント<br>受信値との比較用にフレーム毎に0-59999をカウント|
|**インスタンス名**||
|mrdsq||

<br>
<h4><b>タイマー用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>MrdTimer</b> {<br>long frame_ms = FRAME_DURATION;<br>long mrd_mil = 0;<br>long now_mil = 0;<br>long now_mic = 0;<br>int loop_count = 0;<br>int loop_count_dlt = 2;<br>int loop_count_max = 359999;<br>};|タイマー管理用の構造体設定。各変数の説明:<br>1フレームあたりの単位時間(ms)<br>フレーム管理時計の時刻 Meridian Clock<br>現在時刻を取得<br>現在時刻を取得<br>サイン計算用の循環カウンタ<br>サイン計算用の循環カウンタを1フレームにいくつ進めるか<br>循環カウンタの最大値|
|**インスタンス名**||
|tmr||

<br>
<h4><b>エラーカウント用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>MrdErr</b> {<br>int esp_pc = 0;<br>int pc_esp = 0;<br>int esp_tsy = 0;<br>int tsy_esp = 0;<br>int board_dly = 0;<br>int esp_skip = 0;<br>int tsy_skip = 0;<br>int pc_skip = 0;<br>};|<br>ESP32 → PC のUDP受信エラー<br>PC → ESP32 のUDP受信エラー<br>ESP32 → TeensyのSPI受信エラー<br>Teensy → ESP32 のSPI受信エラー<br>Teensy or ESP32のシステムディレイ (末端で捕捉)<br>PC → ESP32 のUDPフレームスキップエラー<br>PC → ESP32 → Teensy のフレームスキップエラー(末端で捕捉)<br>Teensy → ESP32 → PC のフレームスキップエラー(末端で捕捉)|
|**インスタンス名**||
|err||


<br>
<h4><b> EEPROM読み書き用共用体</b></h4>

|共用体設定|説明|
|------|-------------------|
|typedef union {<br>uint8_t bval[EEPROM_SIZE];<br>short saval[3][int(EEPROM_SIZE / 4)];<br>short sval[int(EEPROM_SIZE / 2)];<br>} UnionEEPROM;|<br>1バイト単位で540個のデータを持つ<br>short型で3*90個の配列データを持つ<br>short型で270個のデータを持つ<br><br>|
|**インスタンス名**||
|eeprom_write_data|EEPROM書き込み用|
|eeprom_read_data|EEPROM読み込み用|

<br>
<h4><b>6軸,9軸センサー用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct <b>AhrsValue</b> {<br>Adafruit_BNO055 bno<br> = Adafruit_BNO055(55, 0x28, &Wire);<br>MPU6050 mpu6050;<br>uint8_t mpuIntStatus;<br>uint8_t devStatus;<br>uint16_t packetSize;<br>uint8_t fifoBuffer[64];<br>Quaternion q;<br>VectorFloat gravity;<br>float ypr[3];<br>float yaw_origin = 0;<br>float yaw_source = 0;<br>float read[16];<br>float zeros[16] = {0};<br>float ave_data[16];<br>float result[16];<br>float stock_data[IMUAHRS_STOCK][16];<br>int stock_count = 0;<br>VectorInt16 aa;<br>VectorInt16 gyro;<br>VectorInt16 mag;<br>long temperature;<br>};|<br>bno: BNO055のインスタンス<br><br>MPU6050のインスタンス<br>MPUからの実際の割り込みステータスバイト<br>各デバイス操作後のステータス (0 = 成功, !0 = エラー)<br>DMPパケットサイズ (デフォルトは42バイト)<br>FIFOストレージバッファ<br>クォータニオン [w, x, y, z]<br>重力ベクトル [x, y, z]<br>DMPロール、ピッチ、ヨー [x, y, z]<br>ヨー軸のセンター補正値<br>ヨー軸の元データ<br>センサ値の読み込み配列<br>センサ値のゼロリセット用配列<br>移動平均値計算用(データ格納)<br>加工後の最新のmpuデータ(二次データ)<br>移動平均値計算用のデータストック<br>移動平均値計算用<br>加速度センサの測定値[x, y, z]<br>角速度センサの測定値[x, y, z]<br>磁力センサの測定値[x, y, z]<br>温度測定値|
|**インスタンス名**||
|ahrs||


<br>
<h4><b>シリアルモニタリング設定用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct MrdMonitor {<br>bool flow = MONITOR_FLOW;<br>bool all_err = MONITOR_ALL_ERROR;<br>bool servo_err = MONITOR_SERVO_ERR;<br>bool seq_num = MONITOR_SEQ_NUMBER;<br>bool pad = MONITOR_PAD;<br>};|<br>フローを表示<br>全経路の受信エラー率を表示<br>サーボエラーを表示<br>シーケンス番号チェックを表示<br>リモコンのデータを表示|
|**インスタンス名**||
|monitor||

<br>
<h4><b>システム用</b></h4>
|型|変数名|説明|
|--|------|-------------------|
|uint8_t|*s_spi_meridim_dma|DMA送信用|
|uint8_t|*r_spi_meridim_dma|DMA受信用|
|TaskHandle_t|thp[4]|マルチスレッドのタスクハンドル格納用|


<br>
<h4><b>サーボパラメータ用の構造体</b></h4>

|構造体設定|説明|
|------|-------------------|
|struct ServoParam {<br>int num_max;<br>int idl_mount[IDL_MAX];<br>int idr_mount[IDR_MAX];<br>int idc_mount[IDC_MAX];<br>int idl_cw[IDL_MAX];<br>int idr_cw[IDR_MAX];<br>int idc_cw[IDC_MAX];<br>float idl_trim[IDL_MAX];<br>float idr_trim[IDR_MAX];<br>float idc_trim[IDC_MAX];<br>float idl_tgt[IDL_MAX] = {0};<br>float idr_tgt[IDR_MAX] = {0};<br>float idc_tgt[IDC_MAX] = {0};<br>float idl_tgt_past[IDL_MAX] = {0};<br>float idr_tgt_past[IDR_MAX] = {0};<br>float idc_tgt_past[IDC_MAX] = {0};<br>int idl_err[IDL_MAX] = {0};<br>int idr_err[IDR_MAX] = {0};<br>int idc_err[IDC_MAX] = {0};<br>};<br>ServoParam sv;|<br>サーボの最大接続 (サーボ送受信のループ処理数)<br>L系統のマウントありなし<br>R系統のマウントありなし<br>C系統のマウントありなし<br>L系統の正逆方向補正<br>R系統の正逆方向補正<br>C系統の正逆方向補正<br>L系統の直立ポーズトリム値<br>R系統の直立ポーズトリム値<br>C系統の直立ポーズトリム値<br>L系統のポジション目標値(degree)<br>R系統のポジション目標値(degree)<br>C系統のポジション目標値(degree)<br>L系統のポジション前回値(degree)<br>R系統のポジション前回値(degree)<br>C系統のポジション前回値(degree)<br>L系統のサーボエラーカウンタ<br>R系統のサーボエラーカウンタ<br>C系統のサーボエラーカウンタ<br>|
|**インスタンス名**||
|sv||