----  
<h3>int Deg2RSxx(float degree, float trim, int cw)</h3>
----  
小数点２桁までの角度値Degreeを、FUTABAのRSxx系サーボの値に変換して返します。  
引数1 : degree角度値(float型)  
引数2 : サーボのトリム補正degree角度値(float型)  
引数3 : サーボの回転方向+-補正値(int型 -1,+1)  
結果はint型、-1600〜1600の範囲に限定されます。  
　　
<br>  
```  
/**
 * @brief Degree value to Futaba's RSxx Servo value.
 *
 * @param[in] degree Source degree
 * @param[in] trim Trim degree value
 * @param[in] cw Correction value for direction of rotation（+1 or -1）
 * @return int, Futaba's RSxx Servo value（-1600 to 1600）
 */
  
int Meridian::Deg2RSxx(float degree, float trim, int cw)
{
    float _x = (degree + trim) * 10 * cw; 
    if (_x > 1600)                        // max limit
    {
        _x = 1600;
    }
    else if (_x < -1600) // min limit
    {
        _x = -1600;
    }
    return static_cast<int>(_x);
}
```