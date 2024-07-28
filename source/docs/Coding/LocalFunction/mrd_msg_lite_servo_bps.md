----  
<h3>void mrd_msg_lite_servo_bps()</h3>
----  
マウントされているサーボのbpsを表示する.  
  
<br>  
```  
/// @brief マウントされているサーボのbpsを表示する.
void mrd_msg_lite_servo_bps() {
  Serial.print("Set UART_L ");
  Serial.print(SERVO_BAUDRATE_L);
  Serial.println(" bps");
  Serial.print("Set UART_R ");
  Serial.print(SERVO_BAUDRATE_R);
  Serial.println(" bps");
}
```  