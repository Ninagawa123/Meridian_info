----  
<h3>bool mrd_servos_all_off(Meridim90Union a_meridim)</h3>
----  
第一引数のMeridim配列のすべてのサーボモーターをオフ（フリー状態）に設定する.  
引数 : a_meridim サーボの動作パラメータを含むMeridim配列.  
戻り値 : 設定完了時にtrueを返す.  
  
<br>  
```  
/// @brief 第一引数のMeridim配列のすべてのサーボモーターをオフ（フリー状態）に設定する.
/// @param a_meridim サーボの動作パラメータを含むMeridim配列.
/// @return 設定完了時にtrueを返す.
bool mrd_servos_all_off(Meridim90Union a_meridim) {
  for (int i = 0; i < 15; i++) {
    a_meridim.sval[i * 2 + 20] = 0; // サーボのコマンドをオフに設定
    a_meridim.sval[i * 2 + 50] = 0; //
  }
  Serial.println("All servos torq off.");
  return true;
}
```  