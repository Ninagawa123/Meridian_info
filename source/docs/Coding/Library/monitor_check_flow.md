----  
<h3>void monitor_check_flow(const String &text, bool monitor_flow)</h3>
----  
デバック用のフロー表示を行います.   
引数1 : シリアルモニタに表示する文字列  
引数2 : True:ON, False:OFF  
  
<br>  
```  
/**
 * @brief Show text massage if monitor_flow is true. This is for debagging.
 *
 * @param[in] text Text message to display.
 * @param[in] monitor_flow True:on ,False;off
 */  
  
void Meridian::monitor_check_flow(const String &text, bool monitor_flow)
{
    if (monitor_flow)
    {
        Serial.print(text);
    }
}
```