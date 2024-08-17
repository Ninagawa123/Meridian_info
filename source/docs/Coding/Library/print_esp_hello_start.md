----  
<h3>void print_esp_hello_start(String version, String serial_pc_bps, String wifi_ap_ssid)</h3>
----  
ESP等での起動メッセージを表示します. (Wi-Fi接続前から)   
引数1 : バージョン文字列  
引数2 : PCシリアル通信速度  
引数3 : Wi-FI AP SSID文字列  
  
<br>  
```  
/**
 * @brief Print wake-up massage to serial.
 *
 * @param[in] version VESRION of Meridian.
 * @param[in] serial_pc_bps PC-Serial speed.
 * @param[in] wifi_ap_ssid Wi-Fi AP adress to connect.
 */  
  
void Meridian::print_esp_hello_start(String version, String serial_pc_bps, String wifi_ap_ssid)
{
    Serial.println();
    Serial.println("Hello, This is " + version); // バージョン表示
    delay(100);
    Serial.println("PC Serial Speed : " + serial_pc_bps + " bps"); // PCシリアル速度
    Serial.println("WiFi connecting to => " + wifi_ap_ssid);       // WiFi接続完了通知
}

```