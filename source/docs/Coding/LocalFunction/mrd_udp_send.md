----  
<h3>bool mrd_udp_send(byte *a_meridim_bval, int a_len)</h3>
----  
第一引数のMeridim配列のデータをUDP経由でWIFI_SEND_IP, UDP_SEND_PORTに送信する.  
引数 : a_meridim_bval バイト型のMeridim配列  
引数 : a_len バイト型のMeridim配列の長さ  
戻り値 : 送信完了時にtrueを返す.  
  
<br>  
```  
/// @brief 第一引数のMeridim配列のデータをUDP経由でWIFI_SEND_IP, UDP_SEND_PORTに送信する.
/// @param a_meridim_bval バイト型のMeridim配列
/// @param a_len バイト型のMeridim配列の長さ
/// @return 送信完了時にtrueを返す.
bool mrd_udp_send(byte *a_meridim_bval, int a_len)
{
    udp.beginPacket(WIFI_SEND_IP, UDP_SEND_PORT); // UDPパケットの開始
    udp.write(a_meridim_bval, a_len);
    udp.endPacket(); // UDPパケットの終了
    return true;
}
```  