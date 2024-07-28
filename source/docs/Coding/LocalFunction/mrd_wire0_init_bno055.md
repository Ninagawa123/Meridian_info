----  
<h3>bool mrd_wire0_init_bno055(AhrsValue &a_ahrs)</h3>
----  
BNO055センサーの初期化を試みます.  
引数 : a_ahrs AHRSの値を保持する構造体.  
戻り値 : BNO055センサーの初期化が成功した場合はtrue, それ以外の場合はfalseを返す.  
  
<br>  
```  
/// @brief BNO055センサーの初期化を試みます.
/// @param a_ahrs AHRSの値を保持する構造体.
/// @return BNO055センサーの初期化が成功した場合はtrue, それ以外の場合はfalseを返す.
///         現在, この関数は常にfalseを返すように設定されています.
bool mrd_wire0_init_bno055(AhrsValue &a_ahrs) {
  if (!ahrs.bno.begin()) {
    Serial.println("No BNO055 detected ... Check your wiring or I2C ADDR!");
    return false;
  } else {
    Serial.println("BNO055 mounted.");
    delay(50);
    ahrs.bno.setExtCrystalUse(false);
    delay(10);
    return true;
  }
  // データの取得はセンサー用スレッドで実行
}
```  