----  
<h3>bool mrd_eeprom_write_read_check(UnionEEPROM a_write_data, bool a_do, bool a_protect, int a_bhd)</h3>
----  
EEPROMに設定値を書き込み, その後で読み込んで内容を確認し, シリアルポートに出力する.  
引数 : a_write_data EEPROM書き込み用の配列データ.  
引数 : a_do EEPROMの読み書きチェックを実施するかのブール値.  
引数 : a_protect EEPROMの書き込み許可があるかどうかのブール値.  
引数 : a_bhd ダンプリストの表示形式.(0:Bin, 1:Hex, 2:Dec)  
戻り値 : EEPROMの書き込みと読み込みが成功した場合はtrueを, それ以外はfalseを返す.  
  
<br>  
```  
/// @brief EEPROMに設定値を書き込み, その後で読み込んで内容を確認し, シリアルポートに出力する.
/// @param a_write_data EEPROM書き込み用の配列データ.
/// @param a_do EEPROMの読み書きチェックを実施するかのブール値.
/// @param a_protect EEPROMの書き込み許可があるかどうかのブール値.
/// @param a_bhd ダンプリストの表示形式.(0:Bin, 1:Hex, 2:Dec)
/// @return EEPROMの書き込みと読み込みが成功した場合はtrueを, それ以外はfalseを返す.
bool mrd_eeprom_write_read_check(UnionEEPROM a_write_data, bool a_do, bool a_protect, int a_bhd) {
  if (!a_do) // EEPROMの読み書きチェックを実施するか
  {
    return false;
  }

  // EEPROM書き込みを実行
  Serial.println("Try to write EEPROM: ");
  mrd_eeprom_dump_to_serial(a_write_data, a_bhd); // 書き込み内容をダンプ表示

  if (mrd_eeprom_write(a_write_data, a_protect)) {
    Serial.println("...Write OK.");
  } else {
    Serial.println("...Write failed.");
    return false;
  }

  // EEPROM読み込みを実行
  Serial.println("Read EEPROM: ");
  UnionEEPROM read_data_tmp = mrd_eeprom_read();
  mrd_eeprom_dump_to_serial(read_data_tmp, a_bhd); // 読み込み内容をダンプ表示
  Serial.println("...Read completed.");

  return true;
}
```  