----  
<h3>bool mrd_udp_receive(byte *a_meridim_bval, int a_len)</h3>
----  
第一引数のMeridim配列にUDP経由でデータを受信, 格納する.  
引数 : a_meridim_bval バイト型のMeridim配列  
引数 : a_len バイト型のMeridim配列の長さ  
戻り値 : 受信した場合はtrueを, 受信しなかった場合はfalseを返す.  
  
<br>  
```  
/// @brief 第一引数のMeridim配列にUDP経由でデータを受信, 格納する.
/// @param a_meridim_bval バイト型のMeridim配列
/// @param a_len バイト型のMeridim配列の長さ
/// @return 受信した場合はtrueを, 受信しなかった場合はfalseを返す.
bool mrd_udp_receive(byte *a_meridim_bval, int a_len)
{
    if (udp.parsePacket() >= a_len) // データの受信バッファ確認
    {
        udp.read(a_meridim_bval, a_len); // データの受信
        return true;
    }
    return false;
}
```  