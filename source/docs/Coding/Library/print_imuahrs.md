----  
<h3>void print_imuahrs(int imuahrs_mount, int imuahrs_freq)</h3>
----  
接続されたの６軸,９軸センサーの種類を表示します。  
引数1 : センサのタイプ番号  
引数2 : センサへの問い合わせフレーム間隔(ms)  
  
<センサのタイプ番号>  
0:None, 1:MPU6050(GY-521), 2:MPU9250(GY-6050/GY-9250), 3:BNO055  
  
<br>  
```  
/**
 * @brief Print IMU/AHRS sensor's type to serial.
 *
 * @param[in] imuahrs_mount imuahrs_mount number
 *                          0:off, 1:MPU6050(GY-521), 2:MPU9250(GY-6050/GY-9250) 3:BNO055
 * @param[in] imuahrs_freq Frequency to calling imu/ahrs via I2C.
 */
  
void Meridian::print_imuahrs(int imuahrs_mount, int imuahrs_freq)
{
    Serial.print("I2C IMU/AHRS Sensor mounted: ");

    switch (imuahrs_mount)
    {
    case 0:
        Serial.print("None. ");
        break;
    case 1:
        Serial.print("MPU6050(GY-521) ");
        break;
    case 2:
        Serial.print("MPU9250(GY-6050/GY-9250) ");
        break;
    case 3:
        Serial.print("BNO055 ");
        break;
    default:
        break;
    }

    if (imuahrs_mount != 0)
    {
        Serial.print("  freq: ");
        Serial.println(imuahrs_freq);
    }
}
```