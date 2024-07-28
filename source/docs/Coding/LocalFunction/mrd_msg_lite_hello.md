----  
<h3>void mrd_msg_lite_hello()</h3>
----  
システムのバージョン情報と通信速度の設定を表示するためのメッセージを出力する.  
  
<br>  
```  
/// @brief システムのバージョン情報と通信速度の設定を表示するためのメッセージを出力する.
void mrd_msg_lite_hello() {
  Serial.println();
  Serial.print("Hi, This is ");
  Serial.println(VERSION);
  Serial.print("Set PC-USB ");
  Serial.print(SERIAL_PC_BPS);
  Serial.println(" bps");
  Serial.print("Set SPI0   ");
  Serial.print(SPI0_SPEED);
  Serial.println(" bps");
  Serial.print("Set i2c0   ");
  Serial.print(I2C0_SPEED);
  Serial.println(" bps");
}
```  