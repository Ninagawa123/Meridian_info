----  
<h3>void print_tsy_hello(String version, int spi_speed, int i2c_speed)</h3>
----  
Teensy等での起動メッセージを表示します.   
引数1 : バージョン文字列  
引数2 : SPI通信速度  
引数3 : I2C通信速度  
  
<br>  
```  
/**
 * @brief Print version, I2C speed, SPI speed.
 *
 * @param[in] version This　Merisian's VERSION
 * @param[in] spi_speed SPI speed
 * @param[in] i2c_speed I2C speed
 */
  
void Meridian::print_tsy_hello(String version, int spi_speed, int i2c_speed)
{
    Serial.println();
    Serial.print("Hi, This is ");
    Serial.println(version);
    Serial.print("Set SPI speed: ");
    Serial.println(spi_speed);
    Serial.print("Set I2C speed: ");
    Serial.println(i2c_speed);
}
```