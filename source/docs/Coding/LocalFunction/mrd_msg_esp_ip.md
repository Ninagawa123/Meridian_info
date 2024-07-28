----  
<h3>void mrd_msg_esp_ip(bool mode_fixed_ip)</h3>
----  
wifiの接続完了メッセージと各IPアドレスを出力する.  
  
<br>  
```  
/// @brief wifiの接続完了メッセージと各IPアドレスを出力する.
void mrd_msg_esp_ip(bool mode_fixed_ip) {
  Serial.println("WiFi successfully connected.");                      // WiFi接続完了通知
  Serial.println("PC's IP address target => " + String(WIFI_SEND_IP)); // 送信先PCのIPアドレスの表示

  if (mode_fixed_ip) {
    Serial.println("ESP32's IP address => " + String(FIXED_IP_ADDR) +
                   " (*Fixed)"); // ESP32自身のIPアドレスの表示
  } else {
    Serial.print("ESP32's IP address => "); // ESP32自身のIPアドレスの表示
    Serial.println(WiFi.localIP().toString());
  }
}
```  