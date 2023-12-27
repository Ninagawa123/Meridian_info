----  
<h2><b>int HfDeg2Krs(int hfdegree, float trim, int cw)</b></h2>
----  
小数点２桁までの角度値Degreeを100倍した値を、近藤科学のKRS系サーボの値に変換して返します。  
引数1 : degree角度値を100倍した値(int型)  
引数2 : サーボのトリム補正degree角度値(float型)  
引数3 : サーボの回転方向+-補正値(int型 -1,+1)  
結果はint型、3500〜11500の範囲に限定されます。  
  
<br>  
```  
/**
 * @brief Hundredfold degree value to Kondo's KRS Servo value.
 *
 * @param[in] hfdegree Source degree value * 100
 * @param[in] trim Trim degree value
 * @param[in] cw Correction value for direction of rotation（+1 or -1）
 * @return Kondo's KRS Servo value（3500-11500）
 */

int Meridian::HfDeg2Krs(int hfdegree, float trim, int cw)
{
    float _x = 7500 + (trim * 29.6296) + (hfdegree * 0.296296 * cw);
    if (_x > 11500) // max limit
    {
        _x = 11500;
    }
    else if (_x < 3500) // min limit
    {
        _x = 3500;
    }
    return static_cast<int>(_x);
}
```