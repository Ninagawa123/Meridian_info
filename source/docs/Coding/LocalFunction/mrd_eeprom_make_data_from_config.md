----  
<h3>UnionEEPROM mrd_eeprom_make_data_from_config()</h3>
----  
config.hにあるサーボの諸設定からEEPROM格納用の配列データを作成する.  
戻り値 : config.hから作成したEEPROM格納用の配列データを返す.  
  
<br>  
```  
/// @brief config.hにあるサーボの諸設定からEEPROM格納用の配列データを作成する.
/// @return config.hから作成したEEPROM格納用の配列データを返す.
UnionEEPROM mrd_eeprom_make_data_from_config() {
  UnionEEPROM array_tmp = {0};
  for (int i = 0; i < 15; i++) {
    // 各サーボのマウントありなし（0:サーボなし, +:サーボあり順転, -:サーボあり逆転）
    // 例: idl_mt[20] = -21; → FUTABA_RSxTTLサーボを逆転設定でマウント
    array_tmp.saval[0][20 + i * 2] = short(sv.idl_mount[i] * sv.idl_cw[i]);
    array_tmp.saval[0][50 + i * 2] = short(sv.idr_mount[i] * sv.idr_cw[i]);
    // 各サーボの直立デフォルト値 degree
    array_tmp.saval[1][21 + i * 2] = mrd.float2HfShort(sv.idl_trim[i]);
    array_tmp.saval[1][51 + i * 2] = mrd.float2HfShort(sv.idr_trim[i]);
  };
  return array_tmp;
}
```  