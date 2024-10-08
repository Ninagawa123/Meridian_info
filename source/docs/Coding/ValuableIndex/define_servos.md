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
|FUTABA_RSxTTL|FTBRSX|21|(未)|
|DYNAMIXEL 1.0|DXL1|31|(未)|
|DYNAMIXEL 2.0|DXL2|32|(未)|
|KONDO_ICS 3.5/3.6|KOICS3|43||
|KONDO_PMX|KOPMX|44|(未)|
|JRPROPO_XBUS|JRXBUS|51|(未)|
|FEETECH_STS|FTCSTS|61|(未)|
|FEETECH_SCS|FTCSCS|62|(未)|
  
<br>  
<h4><b>サーボインデックスとサーボID</b> </h4>
サーボの識別番号には,   
コード上の処理に用いるサーボインデックス番号( IXL_, IXR_ と表記)と,    
実際にサーボハードウェアに登録されているサーボID番号( _ID と表記)  
の２つを用意してある. 
一連の計算処理にはサーボインデックス番号を用い, 最後にサーボに命令をする段階で, サーボインデックス番号に対応したサーボIDに指示を出すという使い方をする.   
これはサーボの組み替えがあった際にソフトウェア上でも対応できるようにするための処置であり, 通常はインデックス番号とサーボIDは同じ値でよい.   
  
<br>
<h4><b>サーボの初期パラメータ</b> </h4>
|int|値範囲|初期値|説明|
|--|:------:|:------:|-------------------|
|**各サーボのインデックス(IX)に対する<br>ハードウェアID**||||
|IXL_ID[0]||0||
|IXL_ID[1]||1||
|IXL_ID[2]||2||
|IXL_ID[3]||3||
|IXL_ID[4]||4||
|IXL_ID[5]||5||
|IXL_ID[6]||6||
|IXL_ID[7]||7||
|IXL_ID[8]||8||
|IXL_ID[9]||9||
|IXL_ID[10]||10||
|IXL_ID[11]||11||
|IXL_ID[12]||12||
|IXL_ID[13]||13||
|IXL_ID[14]||14||
|IXR_ID[0]||0||
|IXR_ID[1]||1||
|IXR_ID[2]||2||
|IXR_ID[3]||3||
|IXR_ID[4]||4||
|IXR_ID[5]||5||
|IXR_ID[6]||6||
|IXR_ID[7]||7||
|IXR_ID[8]||8||
|IXR_ID[9]||9||
|IXR_ID[10]||10||
|IXR_ID[11]||11||
|IXR_ID[12]||12||
|IXR_ID[13]||13||
|IXR_ID[14]||14||
|**各サーボのマウント有無(プロトコルタイプ)**||||
|IXL_MT[0]||43|頭ヨー|
|IXL_MT[1]||43|左肩ピッチ|
|IXL_MT[2]||43|左肩ロール|
|IXL_MT[3]||43|左肘ヨー|
|IXL_MT[4]||43|左肘ピッチ|
|IXL_MT[5]||43|左股ヨー|
|IXL_MT[6]||43|左股ロール|
|IXL_MT[7]||43|左股ピッチ|
|IXL_MT[8]||43|左膝ピッチ|
|IXL_MT[9]||43|左足首ピッチ|
|IXL_MT[10]||43|左足首ロール|
|IXL_MT[11]||0|追加テスト用|
|IXL_MT[12]||0|追加テスト用|
|IXL_MT[13]||0|追加テスト用|
|IXL_MT[14]||0|追加テスト用|
|IXR_MT[0]||43|腰ヨー|
|IXR_MT[1]||43|右肩ピッチ|
|IXR_MT[2]||43|右肩ロール|
|IXR_MT[3]||43|右肘ヨー|
|IXR_MT[4]||43|右肘ピッチ|
|IXR_MT[5]||43|右股ヨー|
|IXR_MT[5]||43|右股ヨー|
|IXR_MT[6]||43|右股ロール|
|IXR_MT[7]||43|右股ピッチ|
|IXR_MT[8]||43|右膝ピッチ|
|IXR_MT[9]||43|右足首ピッチ|
|IXR_MT[10]||43|右足首ロール|
|IXR_MT[11]||0|追加テスト用|
|IXR_MT[12]||0|追加テスト用|
|IXR_MT[13]||0|追加テスト用|
|IXR_MT[14]||0|追加テスト用|
|**各サーボの内外回転+-方向補正**||||
|IXL_CW[0]|-1,1|1|頭ヨー|
|IXL_CW[1]|-1,1|1|左肩ピッチ|
|IXL_CW[2]|-1,1|1|左肩ロール|
|IXL_CW[3]|-1,1|1|左肘ヨー|
|IXL_CW[4]|-1,1|1|左肘ピッチ|
|IXL_CW[5]|-1,1|1|左股ヨー|
|IXL_CW[6]|-1,1|1|左股ロール|
|IXL_CW[7]|-1,1|1|左股ピッチ|
|IXL_CW[8]|-1,1|1|左膝ピッチ|
|IXL_CW[9]|-1,1|1|左足首ピッチ|
|IXL_CW[10]|-1,1|1|左足首ロール|
|IXL_CW[11]|-1,1|1|追加テスト用|
|IXL_CW[12]|-1,1|1|追加テスト用|
|IXL_CW[13]|-1,1|1|追加テスト用|
|IXL_CW[14]|-1,1|1|追加テスト用|
|IXR_CW[0]|-1,1|1|腰ヨー|
|IXR_CW[1]|-1,1|1|右肩ピッチ|
|IXR_CW[2]|-1,1|1|右肩ロール|
|IXR_CW[3]|-1,1|1|右肘ヨー|
|IXR_CW[4]|-1,1|1|右肘ピッチ|
|IXR_CW[5]|-1,1|1|右股ヨー|
|IXR_CW[6]|-1,1|1|右股ロール|
|IXR_CW[7]|-1,1|1|右股ピッチ|
|IXR_CW[8]|-1,1|1|右膝ピッチ|
|IXR_CW[9]|-1,1|1|右足首ピッチ|
|IXR_CW[10]|-1,1|1|右足首ロール|
|IXR_CW[11]|-1,1|1|追加テスト用|
|IXR_CW[12]|-1,1|1|追加テスト用|
|IXR_CW[13]|-1,1|1|追加テスト用|
|IXR_CW[14]|-1,1|1|追加テスト用|
|**各サーボの直立デフォルト値(degree)**|||具体的な数値を入れて現物調整|
|IXL_TRIM[0]||0|頭ヨー|
|IXL_TRIM[1]||-2.36|左肩ピッチ|
|IXL_TRIM[2]||-91.13|左肩ロール|
|IXL_TRIM[3]||0|左肘ヨー|
|IXL_TRIM[4]||89.98|左肘ピッチ|
|IXL_TRIM[5]||0|左股ヨー|
|IXL_TRIM[6]||0|左股ロール|
|IXL_TRIM[7]||-1.35|左股ピッチ|
|IXL_TRIM[8]||-58.05|左膝ピッチ|
|IXL_TRIM[9]||-20.25|左足首ピッチ|
|IXL_TRIM[10]||-0.68|左足首ロール|
|IXL_TRIM[11]||0|追加テスト用|
|IXL_TRIM[12]||0|追加テスト用|
|IXL_TRIM[13]||0|追加テスト用|
|IXL_TRIM[14]||0|追加テスト用|
|IXR_TRIM[0]||0|腰ヨー|
|IXR_TRIM[1]||0|右肩ピッチ|
|IXR_TRIM[2]||-89.44|右肩ロール|
|IXR_TRIM[3]||0|右肘ヨー|
|IXR_TRIM[4]||89.98|右肘ピッチ|
|IXR_TRIM[5]||0|右股ヨー|
|IXR_TRIM[6]||1.69|右股ロール|
|IXR_TRIM[7]||-3.38|右股ピッチ|
|IXR_TRIM[8]||-57.38|右膝ピッチ|
|IXR_TRIM[9]||-20.25|右足首ピッチ|
|IXR_TRIM[10]||-2.36|右足首ロール|
|IXR_TRIM[11]||0|追加テスト用|
|IXR_TRIM[12]||0|追加テスト用|
|IXR_TRIM[13]||0|追加テスト用|
|IXR_TRIM[14]||0|追加テスト用|