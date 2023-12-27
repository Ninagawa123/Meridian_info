----  
<h2><b>void print_servo_mounts(int idl_svmt[ ], int idr_svmt[ ], int id3_svmt[ ])</b></h2>
----  
Teensy等での起動メッセージを表示します。  
引数1 : L系列のサーボマウント配列  
引数2 : R系列のサーボマウント配列  
引数3 : 3系列のサーボマウント配列  
  
<br>  
```  
/**
 * @brief Print mounted servomotor's id.
 *
 * @param[in] idl_svmt Left side servos arrey.
 * @param[in] idr_svmt Right side servos arrey.
 * @param[in] id3_svmt 3rd side servos arrey.
 */
  
void Meridian::print_servo_mounts(int idl_svmt[], int idr_svmt[], int id3_svmt[]))
{
    Serial.print("Left side Servos mounted:  ");
    for (int i = 0; i < 15; i++)
    {
        if (idl_svmt[i])
        {
            Serial.print(i);
            Serial.print(" ");
        }
    }
    Serial.println();

    Serial.print("Right side Servos mounted: ");
    for (int i = 0; i < 15; i++)
    {
        if (idr_svmt[i])
        {
            Serial.print(i);
            Serial.print(" ");
        }
    }
    Serial.println();

    int _x = 0;
    for (int i = 0; i < 15; i++)
    {
        _x = _x + id3_svmt[i];
    }
    if (_x){
        Serial.print("3rd side Servos mounted: ");
        for (int i = 0; i < 15; i++)
        {
            if (id3_svmt[i])
            {
                Serial.print(i);
                Serial.print(" ");
            }
        }
    Serial.println();
    }
}
```