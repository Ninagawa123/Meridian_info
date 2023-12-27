----  
<h2><b>void monitor_servo_error(const String &text, int num, bool monitor_servo_error)</b></h2>
----  
信号エラーのあったサーボのIDをシリアルモニタで表示します。  
引数1 : 通信エラーのあったサーボモータの系列。"L","R","C"など  
引数2 : 通信エラーのあったサーボモーターのID番号。  
引数3 : サーボエラーのシリアル表示の有無。 0:OFF, 1:ON  
  
<br>  
```  
/**
 * @brief Show servo error id.
 *
 * @param[in] text String. "L","R","C",etc
 * @param[in] num Servo id.
 * @param[in] monitor_servo_error True:on ,False;off
 */  
  
void Meridian::monitor_servo_error(const String &text, int num, bool monitor_servo_error)
{
    if (monitor_servo_error)
    {
        Serial.print("Servo err ");
        Serial.print(text);
        Serial.print("_");
        Serial.println(num);
    }
}
```