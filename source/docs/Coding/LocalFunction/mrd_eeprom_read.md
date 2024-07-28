----  
<h3>UnionEEPROM mrd_eeprom_read()</h3>
----  
EEPROMの内容を読み込んで返す.  
戻り値 : UnionEEPROM のフォーマットで配列を返す.  
  
<br>  
```  
/// @brief EEPROMの内容を読み込んで返す.
/// @return UnionEEPROM のフォーマットで配列を返す.
UnionEEPROM mrd_eeprom_read() {
  UnionEEPROM read_data_tmp;
  for (int i = 0; i < EEPROM_SIZE; i++) // データを読み込む時はbyte型
  {
    read_data_tmp.bval[i] = EEPROM.read(i);
  }
  return read_data_tmp;
}
```  