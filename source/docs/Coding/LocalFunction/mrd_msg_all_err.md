----  
<h3>bool mrd_msg_all_err(MrdErr a_err, bool mrd_disp_all_error)</h3>
----  
システム内の様々な通信エラーとスキップ数をモニタリングし, シリアルポートに出力する.  
引数 : a_err エラーデータの入った構造体.  
引数 : mrd_disp_all_error モニタリング表示のオンオフ.  
戻り値 : エラーメッセージを表示した場合はtrueを, 表示しなかった場合はfalseを返す.  
  
<br>  
```  
/// @brief システム内の様々な通信エラーとスキップ数をモニタリングし, シリアルポートに出力する.
/// @param a_err エラーデータの入った構造体.
/// @param mrd_disp_all_error モニタリング表示のオンオフ.
/// @return エラーメッセージを表示した場合はtrueを, 表示しなかった場合はfalseを返す.
bool mrd_msg_all_err(MrdErr a_err, bool mrd_disp_all_error) {
  if (mrd_disp_all_error) {
    Serial.print("[ERR] es>pc:");
    Serial.print(a_err.esp_pc);
    Serial.print(" pc>es:");
    Serial.print(a_err.pc_esp);
    Serial.print(" es>ts:");
    Serial.print(a_err.esp_tsy);
    Serial.print(" ts>es:");
    Serial.print(a_err.esp_tsy);
    Serial.print(" tsSkp:");
    Serial.print(a_err.tsy_skip);
    Serial.print(" esSkp:");
    Serial.print(a_err.esp_skip);
    Serial.print(" pcSkp:");
    Serial.print(a_err.pc_skip);
    Serial.println();
    return true;
  }
  return false;
}
```  