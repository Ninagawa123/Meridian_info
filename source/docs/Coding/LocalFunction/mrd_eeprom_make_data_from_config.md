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
    // 例: IXL_mt[20] = -21; → FUTABA_RSxTTLサーボを逆転設定でマウント
    array_tmp.saval[0][20 + i * 2] = short(sv.IXL_mount[i] * sv.IXL_cw[i]);
    array_tmp.saval[0][50 + i * 2] = short(sv.IXR_mount[i] * sv.IXR_cw[i]);
    // 各サーボの直立デフォルト値 degree
    array_tmp.saval[1][21 + i * 2] = mrd.float2HfShort(sv.IXL_trim[i]);
    array_tmp.saval[1][51 + i * 2] = mrd.float2HfShort(sv.IXR_trim[i]);
  };
  return array_tmp;
}
```  