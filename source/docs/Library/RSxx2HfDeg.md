----  
<h2><b>int RSxx2HfDeg(int rsxx, float trim, int cw)</b></h2>
----  
FUTABAのRSxx系サーボの値を、小数点２桁までの角度値Degreeを100倍した値に変換します。  
引数1 : FutabaRSxx系サーボの位置の値(int型)  
引数2 : サーボのトリム補正degree角度値(float型)  
引数3 : サーボの回転方向+-補正値(int型 -1,+1)   
結果はint型、-32766〜32766の範囲に限定されます。  
  
<br>  
```  
/**
 * @brief Futaba's RSxx Servo value to hundredfold degree value.
 *
 * @param[in] rsxx Source futaba's RSxx Servo value（-1600 to 1600）
 * @param[in] trim Trim degree value
 * @param[in] cw Correction value for direction of rotation（+1 or -1）
 * @return int, degree * 100
 */
  
int Meridian::RSxx2HfDeg(int rsxx, float trim, int cw)
{
    float _x = (rsxx - (trim * 10)) * 10 * cw;
    if (_x > 32766)
    {
        _x = 32766;
    }
    else if (_x < -32766)
    {
        _x = -32766;
    }
    return static_cast<int>(_x);
}
```