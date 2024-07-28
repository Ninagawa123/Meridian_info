----  
<h3>bool mrd_servos_drive_lite(Meridim90Union a_meridim, int a_L_type, int a_R_type, ServoParam &a_sv)</h3>
----  
指定されたサーボにコマンドを分配する.  
引数 : a_meridim サーボの動作パラメータを含むMeridim配列.  
引数 : a_L_type L系統のサーボタイプ.  
引数 : a_R_type R系統のサーボタイプ.  
引数 : a_sv サーボパラメータの構造体.  
戻り値 : サーボの駆動が成功した場合はtrueを, 失敗した場合はfalseを返す.  
  
<br>  
```  
/// @brief 指定されたサーボにコマンドを分配する.
/// @param a_meridim サーボの動作パラメータを含むMeridim配列.
/// @param a_L_type L系統のサーボタイプ.
/// @param a_R_type R系統のサーボタイプ.
/// @param a_sv サーボパラメータの構造体.
/// @return サーボの駆動が成功した場合はtrueを, 失敗した場合はfalseを返す.
bool mrd_servos_drive_lite(Meridim90Union a_meridim, int a_L_type, int a_R_type, ServoParam &a_sv) {
  if (a_L_type == 43 && a_R_type == 43) // ICSサーボがL系R系に設定されていた場合はLR均等送信を実行
  {
    mrd_sv_drive_ics_double(a_meridim, a_sv);
    return true;
  } else {
    return false;
  }
}
```  