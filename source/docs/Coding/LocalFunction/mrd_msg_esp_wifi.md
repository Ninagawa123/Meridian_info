----  
<h3>void mrd_msg_esp_wifi()</h3>
----  
wifiの接続開始メッセージを出力する.  
  
<br>  
```  
/// @brief wifiの接続開始メッセージを出力する.
void mrd_msg_esp_wifi() {
  Serial.println("WiFi connecting to => " + String(WIFI_AP_SSID)); // WiFi接続完了通知
}
```  