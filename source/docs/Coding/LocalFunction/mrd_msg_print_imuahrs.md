----  
<h3>void mrd_msg_print_imuahrs(ImuAhrsType a_imuahrs_type)</h3>
----  
システムに接続されているIMU/AHRSセンサーのタイプを表示する.  
引数 : a_imuahrs_type 接続されているセンサーのタイプを示す列挙型.  
  
<br>  
```  
/// @brief システムに接続されているIMU/AHRSセンサーのタイプを表示する.
/// @param a_imuahrs_type 接続されているセンサーのタイプを示す列挙型.
void mrd_msg_print_imuahrs(ImuAhrsType a_imuahrs_type) {
  Serial.print("IMU/AHRS Sensor mounted: ");

  switch (a_imuahrs_type) {
  case NO_IMU:
    Serial.println("None. ");
    break;
  case MPU6050_IMU:
    Serial.println("MPU6050(GY-521) ");
    break;
  case MPU9250_IMU:
    Serial.println("MPU9250(GY-6050/GY-9250) ");
    break;
  case BNO055_AHRS:
    Serial.println("BNO055 ");
    break;
  default:
    break;
  }
}
```  