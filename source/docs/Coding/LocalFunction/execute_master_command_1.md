----  
<h3>bool execute_master_command_1(Meridim90Union a_meridim, bool a_flg_exe)</h3>
----  
Master Commandの第1群を実行する. 受信コマンドに基づき, 異なる処理を行う.  
引数1 : a_meridim 実行したいコマンドの入ったMeridim配列を渡す.  
引数2 : a_flg_exe Meridimの受信成功判定フラグを渡す.    
戻り値 : コマンドを実行した場合はtrue, しなかった場合はfalseを返す. 
  
<br>  
```  
/// @brief Master Commandの第1群を実行する. 受信コマンドに基づき, 異なる処理を行う.
/// @param a_meridim 実行したいコマンドの入ったMeridim配列を渡す.
/// @param a_flg_exe Meridimの受信成功判定フラグを渡す.
/// @return コマンドを実行した場合はtrue, しなかった場合はfalseを返す.
bool execute_master_command_1(Meridim90Union a_meridim, bool a_flg_exe) {
  if (!a_flg_exe) {
    return false;
  }

  // コマンド[90]: 1~999は MeridimのLength. デフォルトは90

  // コマンド:MCMD_CLEAR_SERVO_ERROR_ID (10004) 通信エラーサーボIDのクリア
  if (a_meridim.sval[MRD_MASTER] == MCMD_CLEAR_SERVO_ERROR_ID) {
    r_udp_meridim.bval[MRD_ERR_l] = 0;
    s_udp_meridim.bval[MRD_ERR_l] = 0;
    for (int i = 0; i < IDL_MAX; i++) {
      sv.idl_err[i] = 0;
    }
    for (int i = 0; i < IDR_MAX; i++) {
      sv.idr_err[i] = 0;
    }
    Serial.println("Servo Error ID reset.");
    return true;
  }

  // コマンド:MCMD_BOARD_TRANSMIT_ACTIVE (10005) UDP受信の通信周期制御をボード側主導に（デフォルト）
  if (a_meridim.sval[MRD_MASTER] == MCMD_BOARD_TRANSMIT_ACTIVE) {
    flg.udp_board_passive = false; // UDP送信をアクティブモードに
    flg.frame_timer_reset = true; // フレームの管理時計をリセットフラグをセット
    return true;
  }

  // コマンド:MCMD_ENTER_EEPROM_WRITE_MODE (10009) EEPROMの書き込みモードスタート
  if (a_meridim.sval[MRD_MASTER] == MCMD_ENTER_EEPROM_WRITE_MODE) {
    flg.eeprom_write_mode = true; // 書き込みモードのフラグをセット
    flg.frame_timer_reset = true; // フレームの管理時計をリセットフラグをセット
    return true;
  }
  return false;
}
```