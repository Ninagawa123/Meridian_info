<hr>
<h3> #define で定義される変数名のリスト その2 </h3>  
<hr>
<br>

<h3><b>サーボ関連</b></h3>
<br>

<h4><b>マウントするサーボのプロトコルタイプ</b> </h4>
|プロトコル|列挙子|値|備考|
|--|:------|||
|マウントなし|NOSERVO|0||
|Single PWM|PWM_S|1|(未)|
|I2C_PCA9685 to PWM|PCA9685|11|(未)|
|FUTABA_RSxTTL|FRSXTTL|21|(未)|
|DYNAMIXEL 1.0|DXL1|31|(未)|
|DYNAMIXEL 2.0|DXL2|32|(未)|
|KONDO_ICS 3.5/3.6|KOICS3|43||
|KONDO_PMX|KOPMX|44|(未)|
|JRPROPO_XBUS|JRXBUS|51|(未)|
|FEETECH_STS|FTCSTS|61|(未)|
|FEETECH_SCS|FTCSCS|62|(未)|

<br>
<h4><b>サーボの初期パラメータ</b> </h4>
|int|値範囲|初期値|説明|
|--|:------:|:------:|-------------------|
|**各サーボのマウント有無**||||
|IDL_MT[0]||43|頭ヨー|
|IDL_MT[1]||43|左肩ピッチ|
|IDL_MT[2]||43|左肩ロール|
|IDL_MT[3]||43|左肘ヨー|
|IDL_MT[4]||43|左肘ピッチ|
|IDL_MT[5]||43|左股ヨー|
|IDL_MT[6]||43|左股ロール|
|IDL_MT[7]||43|左股ピッチ|
|IDL_MT[8]||43|左膝ピッチ|
|IDL_MT[9]||43|左足首ピッチ|
|IDL_MT[10]||43|左足首ロール|
|IDL_MT[11]||0|追加テスト用|
|IDL_MT[12]||0|追加テスト用|
|IDL_MT[13]||0|追加テスト用|
|IDL_MT[14]||0|追加テスト用|
|IDR_MT[0]||43|腰ヨー|
|IDR_MT[1]||43|右肩ピッチ|
|IDR_MT[2]||43|右肩ロール|
|IDR_MT[3]||43|右肘ヨー|
|IDR_MT[4]||43|右肘ピッチ|
|IDR_MT[5]||43|右股ヨー|
|IDR_MT[5]||43|右股ヨー|
|IDR_MT[6]||43|右股ロール|
|IDR_MT[7]||43|右股ピッチ|
|IDR_MT[8]||43|右膝ピッチ|
|IDR_MT[9]||43|右足首ピッチ|
|IDR_MT[10]||43|右足首ロール|
|IDR_MT[11]||0|追加テスト用|
|IDR_MT[12]||0|追加テスト用|
|IDR_MT[13]||0|追加テスト用|
|IDR_MT[14]||0|追加テスト用|
|**各サーボの内外回転+-方向補正**||||
|IDL_CW[0]|-1,1|1|頭ヨー|
|IDL_CW[1]|-1,1|1|左肩ピッチ|
|IDL_CW[2]|-1,1|1|左肩ロール|
|IDL_CW[3]|-1,1|1|左肘ヨー|
|IDL_CW[4]|-1,1|1|左肘ピッチ|
|IDL_CW[5]|-1,1|1|左股ヨー|
|IDL_CW[6]|-1,1|1|左股ロール|
|IDL_CW[7]|-1,1|1|左股ピッチ|
|IDL_CW[8]|-1,1|1|左膝ピッチ|
|IDL_CW[9]|-1,1|1|左足首ピッチ|
|IDL_CW[10]|-1,1|1|左足首ロール|
|IDL_CW[11]|-1,1|1|追加テスト用|
|IDL_CW[12]|-1,1|1|追加テスト用|
|IDL_CW[13]|-1,1|1|追加テスト用|
|IDL_CW[14]|-1,1|1|追加テスト用|
|IDR_CW[0]|-1,1|1|腰ヨー|
|IDR_CW[1]|-1,1|1|右肩ピッチ|
|IDR_CW[2]|-1,1|1|右肩ロール|
|IDR_CW[3]|-1,1|1|右肘ヨー|
|IDR_CW[4]|-1,1|1|右肘ピッチ|
|IDR_CW[5]|-1,1|1|右股ヨー|
|IDR_CW[6]|-1,1|1|右股ロール|
|IDR_CW[7]|-1,1|1|右股ピッチ|
|IDR_CW[8]|-1,1|1|右膝ピッチ|
|IDR_CW[9]|-1,1|1|右足首ピッチ|
|IDR_CW[10]|-1,1|1|右足首ロール|
|IDR_CW[11]|-1,1|1|追加テスト用|
|IDR_CW[12]|-1,1|1|追加テスト用|
|IDR_CW[13]|-1,1|1|追加テスト用|
|IDR_CW[14]|-1,1|1|追加テスト用|
|**各サーボの直立デフォルト値(degree)**|||具体的な数値を入れて現物調整|
|IDL_TRIM[0]||0|頭ヨー|
|IDL_TRIM[1]||-2.36|左肩ピッチ|
|IDL_TRIM[2]||-91.13|左肩ロール|
|IDL_TRIM[3]||0|左肘ヨー|
|IDL_TRIM[4]||89.98|左肘ピッチ|
|IDL_TRIM[5]||0|左股ヨー|
|IDL_TRIM[6]||0|左股ロール|
|IDL_TRIM[7]||-1.35|左股ピッチ|
|IDL_TRIM[8]||-58.05|左膝ピッチ|
|IDL_TRIM[9]||-20.25|左足首ピッチ|
|IDL_TRIM[10]||-0.68|左足首ロール|
|IDL_TRIM[11]||0|追加テスト用|
|IDL_TRIM[12]||0|追加テスト用|
|IDL_TRIM[13]||0|追加テスト用|
|IDL_TRIM[14]||0|追加テスト用|
|IDR_TRIM[0]||0|腰ヨー|
|IDR_TRIM[1]||0|右肩ピッチ|
|IDR_TRIM[2]||-89.44|右肩ロール|
|IDR_TRIM[3]||0|右肘ヨー|
|IDR_TRIM[4]||89.98|右肘ピッチ|
|IDR_TRIM[5]||0|右股ヨー|
|IDR_TRIM[6]||1.69|右股ロール|
|IDR_TRIM[7]||-3.38|右股ピッチ|
|IDR_TRIM[8]||-57.38|右膝ピッチ|
|IDR_TRIM[9]||-20.25|右足首ピッチ|
|IDR_TRIM[10]||-2.36|右足首ロール|
|IDR_TRIM[11]||0|追加テスト用|
|IDR_TRIM[12]||0|追加テスト用|
|IDR_TRIM[13]||0|追加テスト用|
|IDR_TRIM[14]||0|追加テスト用|