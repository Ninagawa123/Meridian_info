----  
<h2><b>float Krs2Deg(int krs, float trim, int cw)</b></h2>
----  
近藤科学のKRS系サーボの値を、小数点２桁までの角度値DegreeのShort型に変換します。  
引数1 : KRS系サーボの位置の値(int型)  
引数2 : サーボのトリム補正degree角度値(float型)  
引数3 : サーボの回転方向+-補正値(int型 -1,+1)  
結果はint型、3500〜11500の範囲に限定されます。  
  
<br>  
```  
/**
 * @brief Kondo's KRS Servo value to degree value.
 *
 * @param[in] krs Source Kondo's KRS Servo value（3500-11500）
 * @param[in] trim Trim degree value
 * @param[in] cw Correction value for direction of rotation（+1 or -1）
 * @return float, degree
 */
　　
float Meridian::Krs2Deg(int krs, float trim, int cw)
{
    float _x = (krs - 7500 - (trim * 29.62963)) * 0.03375 * cw ;
    return _x;
}
```