----  
<h3>bool mrd_wire0_init_i2c(int a_i2c0_speed, int a_pinSDA = -1, int a_pinSCL = -1)</h3>
----  
Wire0 I2C通信を初期化し, 指定されたクロック速度で設定する.  
引数 : a_i2c0_speed I2C通信のクロック速度です.  
引数 : a_pinSDA SDAのピン番号. 下記と合わせて省略可.  
引数 : a_pinSCL SCLのピン番号. 上記と合わせて省略可.  
  
<br>  
```  
/// @brief Wire0 I2C通信を初期化し, 指定されたクロック速度で設定する.
/// @param a_i2c0_speed I2C通信のクロック速度です.
/// @param a_pinSDA SDAのピン番号. 下記と合わせて省略可.
/// @param a_pinSCL SCLのピン番号. 上記と合わせて省略可.
bool mrd_wire0_init_i2c(int a_i2c0_speed, int a_pinSDA = -1, int a_pinSCL = -1) {
  Serial.print("Initializing wire0 I2C... ");
  if (a_pinSDA == -1 && a_pinSCL == -1) {
    Wire.begin();
  } else {
    Wire.begin(a_pinSDA, a_pinSCL);
  }
  Wire.setClock(a_i2c0_speed);
  return true;
}
```  