----  
<h3>bool execute_master_command_2(Meridim90Union a_meridim, bool a_flg_exe)</h3>
----  
Master Commandの第2群を実行する. 受信コマンドに基づき, 異なる処理を行う.  
引数1 : a_meridim 実行したいコマンドの入ったMeridim配列を渡す.  
引数2 : a_flg_exe Meridimの受信成功判定フラグを渡す.    
戻り値 : コマンドを実行した場合はtrue, しなかった場合はfalseを返す. 
  
<br>  
```  
/// @brief Master Commandの第2群を実行する. 受信コマンドに基づき, 異なる処理を行う.
/// @param a_meridim 実行したいコマンドの入ったMeridim配列を渡す.
/// @param a_flg_exe Meridimの受信成功判定フラグを渡す.
/// @return コマンドを実行した場合はtrue, しなかった場合はfalseを返す.
bool execute_master_command_2(Meridim90Union a_meridim, bool a_flg_exe) {
  if (!a_flg_exe) {
    return false;
  }
  
  // コマンド[90]: 1~999は MeridimのLength. デフォルトは90

  // コマンド:[0] 全サーボ脱力
  if (a_meridim.sval[MRD_MASTER] == 0) {
    mrd_servos_all_off(s_udp_meridim);
    return true;
  }

  // コマンド:[1] サーボオン 通常動作

  // コマンド:MCMD_UPDATE_YAW_CENTER (10002) IMU/AHRSのヨー軸リセット
  if (a_meridim.sval[MRD_MASTER] == MCMD_UPDATE_YAW_CENTER) {
    ahrs.yaw_origin = ahrs.yaw_source;
    Serial.println("cmd: yaw reset.");
    return true;
  }

  // コマンド:MCMD_ENTER_TRIM_MODE (10003) トリムモードに入る（既存のものは廃止し, 検討中）

  // コマンド:MCMD_BOARD_TRANSMIT_PASSIVE (10006) UDP受信の通信周期制御をPC側主導に（SSH的な動作）
  if (a_meridim.sval[MRD_MASTER] == MCMD_BOARD_TRANSMIT_PASSIVE) {
    flg.udp_board_passive = true; // UDP送信をパッシブモードに
    flg.frame_timer_reset = true; // フレームの管理時計をリセットフラグをセット
    return true;
  }

  // コマンド:MCMD_RESET_MRD_TIMER) (10007) フレーム管理時計tmr.mrd_milを現在時刻にリセット
  if (a_meridim.sval[MRD_MASTER] == MCMD_RESET_MRD_TIMER) {
    flg.frame_timer_reset = true; // フレームの管理時計をリセットフラグをセット
    return true;
  }

  // コマンド:MCMD_STOP_BOARD_DURING (10008) ボードの末端処理を指定時間だけ止める.
  if (a_meridim.sval[MRD_MASTER] == MCMD_STOP_BOARD_DURING) {
    flg.stop_board_during = true; // ボードの処理停止フラグをセット
    // ボードの末端処理をmeridim[2]ミリ秒だけ止める.
    Serial.print("Stop ESP32's processing during ");
    Serial.print(int(a_meridim.sval[MRD_STOP_FRAMES_MS]));
    Serial.println(" ms.");
    for (int i = 0; i < int(a_meridim.sval[MRD_STOP_FRAMES_MS]); i++) {
      delay(1);
    }
    flg.stop_board_during = false; // ボードの処理停止フラグをクリア
    flg.frame_timer_reset = true; // フレームの管理時計をリセットフラグをセット
    return true;
  }
  return false;
}
```