----  
<h3>void print_esp_hello_ip(String wifi_send_ip, String wifi_localip, String fixed_ip_addr, bool mode_fixed_ip)</h3>
----  
ESP等での起動メッセージを表示します. (Wi-Fi接続後から)  
引数1 : 接続先のPCのIPアドレス  
引数2 : ESP32側のIPアドレス※  
引数3 : ESP32のIP固定時のIPアドレス (mode_fixed_ipがTrueの時に有効)
引数4 : ESP32のIP固定の有無.  True:ON, False:OFF  
※ 引数2のESP32側の動的IPアドレスはMeridian起動時にESP32のシリアルモニタに表示.   
  
<br>  
```  
/**
 * @brief Print Wi-Fi status to serial.
 *
 * @param[in] wifi_send_ip Send Wi-Fi IP. (PC's IP adress)
 * @param[in] wifi_localip Wi-Fi IP of this device.
 * @param[in] fixed_ip_addr Fixed Wi-Fi IP of this device. (If mode_fixed_ip is True)
 * @param[in] mode_fixed_ip Use fixed Wi-Fi IP or Not.
 */
  
void Meridian::print_esp_hello_ip(String wifi_send_ip, IPAddress wifi_localip, String fixed_ip_addr, bool mode_fixed_ip)
{
    Serial.println("WiFi successfully connected.");                          // WiFi接続完了通知
    Serial.println("PC's IP address target is  => " + String(wifi_send_ip)); // 送信先PCのIPアドレスの表示

    if (mode_fixed_ip)
    {
        Serial.println("ESP32's IP address is  => " + String(fixed_ip_addr) + " (*Fixed)"); // ESP32自身のIPアドレスの表示
    }
    else
    {
        Serial.print("ESP32's IP address is  => "); // ESP32自身のIPアドレスの表示
        Serial.println(wifi_localip);
    }
}
```