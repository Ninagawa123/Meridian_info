----  
<h3>float RSxx2Deg(int rsxx, float trim, int cw)</h3>
----  
FUTABAのRSxx系サーボの値を, 小数点２桁までの角度値Degreeのfloat型に変換します.   
引数1 : FutabaRSxx系サーボの位置の値(int型)  
引数2 : サーボのトリム補正degree角度値(float型)  
引数3 : サーボの回転方向+-補正値(int型 -1,+1)   
結果をfloat型で返します.   
  
<br>  
```  
/**
 * @brief Futaba's RSxx Servo value to degree value.
 *
 * @param[in] rsxx Source Futaba's RSxx Servo value（-1600 to 1600）
 * @param[in] trim Trim degree value
 * @param[in] cw Correction value for direction of rotation（+1 or -1）
 * @return float, degree
 */
  
float Meridian::RSxx2Deg(int rsxx, float trim, int cw)
{
    float _x = (rsxx - (trim * 10)) * 0.1 * cw;
    return _x;
}
```