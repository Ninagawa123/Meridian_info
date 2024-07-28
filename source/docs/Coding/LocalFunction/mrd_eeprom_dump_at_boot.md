----  
<h3>bool mrd_eeprom_dump_at_boot(bool a_do_dump, int a_bhd)</h3>
----  
EEPROM格納用の配列データをシリアルにダンプ出力する.(起動時用)  
引数 : a_do_dump 実施するか否か.  
引数 : a_bhd ダンプリストの表示形式.(0:Bin, 1:Hex, 2:Dec)  
戻り値 : 終了時にtrueを返す.  
  
<br>  
```  
/// @brief EEPROM格納用の配列データをシリアルにダンプ出力する.(起動時用)
/// @param a_do_dump 実施するか否か.
/// @param a_bhd ダンプリストの表示形式.(0:Bin, 1:Hex, 2:Dec)
/// @return 終了時にtrueを返す.
bool mrd_eeprom_dump_at_boot(bool a_do_dump, int a_bhd) {
  if (a_do_dump) {
    mrd_eeprom_dump_to_serial(mrd_eeprom_read(), a_bhd);
    return true;
  }
  return false;
}
```  