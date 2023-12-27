----  
<h2><b>void monitor_joypad(uint16_t *arr)</b></h2>
----  
ジョイパッドの入力ステータスを表示します。  
引数 : ジョイパッド用の共用体配列  
※ 要動作検証  
  
<br>  
```  
/**
 * @brief Display gamepad keys.
 *
 * @param[in] arr array[3]
 */
  
void Meridian::monitor_joypad(uint16_t *arr)
{
    for (int i = 0; i < 4; i++)
    {
        Serial.print(arr[i]);
        if (i < 3)
        {
            Serial.print("/");
        }
    }
    Serial.println();
}
```