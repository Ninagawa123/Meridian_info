----  
<h3>bool mrd_msg_seq_number(uint16_t a_seq_expect, uint16_t a_seq_rcvd, bool mrd_disp_seq_num)</h3>
----  
期待するシーケンス番号と実施に受信したシーケンス番号を表示する.  
引数 : a_seq_expect 期待するシーケンス番号.  
引数 : a_seq_rcvd 実際に受信したシーケンス番号.  
戻り値 : エラーメッセージを表示した場合はtrueを, 表示しなかった場合はfalseを返す.  
  
<br>  
```  
/// @brief 期待するシーケンス番号と実施に受信したシーケンス番号を表示する.
/// @param a_seq_expect 期待するシーケンス番号.
/// @param a_seq_rcvd 実際に受信したシーケンス番号.
/// @return エラーメッセージを表示した場合はtrueを, 表示しなかった場合はfalseを返す.
bool mrd_msg_seq_number(uint16_t a_seq_expect, uint16_t a_seq_rcvd, bool mrd_disp_seq_num) {
  if (mrd_disp_seq_num) {
    Serial.print("Seq ep/rv ");
    Serial.print(a_seq_expect);
    Serial.print("/");
    Serial.println(a_seq_rcvd);
    return true;
  }
  return false;
}
```  