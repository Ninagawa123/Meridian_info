----  
<h3>void MONITOR_ERR_SERVOor(const String &text, int num, bool MONITOR_ERR_SERVOor)</h3>
----  
信号エラーのあったサーボのIDをシリアルモニタで表示します.   
引数1 : 通信エラーのあったサーボモータの系列. "L","R","C"など  
引数2 : 通信エラーのあったサーボモーターのID番号.   
引数3 : サーボエラーのシリアル表示の有無.  0:OFF, 1:ON  
  
<br>  
```  
/**
 * @brief Show servo error id.
 *
 * @param[in] text String. "L","R","C",etc
 * @param[in] num Servo id.
 * @param[in] MONITOR_ERR_SERVOor True:on ,False;off
 */  
  
void Meridian::MONITOR_ERR_SERVOor(const String &text, int num, bool MONITOR_ERR_SERVOor)
{
    if (MONITOR_ERR_SERVOor)
    {
        Serial.print("Servo err ");
        Serial.print(text);
        Serial.print("_");
        Serial.println(num);
    }
}
```