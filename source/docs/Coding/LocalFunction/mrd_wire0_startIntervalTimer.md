----  
<h3>bool mrd_wire0_startIntervalTimer(bool a_check)</h3>
----  
インターバルタイマーを設定して, 定期的にAHRSセンサーからのデータ読み取りを行う.  
引数 : a_check タイマーを開始するかどうかの条件を示すブール値です.  
戻り値 : タイマーが正しく開始された場合はtrue, それ以外の場合はfalseを返す.  
  
<br>  
```  
/// @brief インターバルタイマーを設定して, 定期的にAHRSセンサーからのデータ読み取りを行う.
/// @param a_check タイマーを開始するかどうかの条件を示すブール値です.
/// @return タイマーが正しく開始された場合はtrue, それ以外の場合はfalseを返す.
bool mrd_wire0_startIntervalTimer(bool a_check) {
  if (a_check) {
    // bool rlst = wireTimer0.begin(mrd_wire0_run, IMUAHRS_INTERVAL * 1000); //
    // インターバルはマイクロ秒指定
    //  wireTimer.priority(90);
    // return rlst;
    return false;
  }
  return false;
}
```  