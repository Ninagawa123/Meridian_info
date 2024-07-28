----  
<h3>bool mrd_eeprom_init(int a_eeprom_size)</h3>
----  
EEPROMの初期化  
引数 : a_eeprom_size EEPROMのバイト長  
戻り値 : 初期化が成功すればtrue, 失敗ならfalseを返す.  
  
<br>  
```  
/// @brief EEPROMの初期化
/// @param a_eeprom_size EEPROMのバイト長
/// @return 初期化が成功すればtrue, 失敗ならfalseを返す.
bool mrd_eeprom_init(int a_eeprom_size) {
  Serial.print("Initializing EEPROM... ");
  if (EEPROM.begin(a_eeprom_size)) {
    Serial.println("OK.");
    return true;
  } else {
    Serial.println("Failed.");
  }
  return false;
}
```  