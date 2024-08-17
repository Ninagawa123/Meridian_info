----  
<h3>float HfShort2float(short val)</h3>
----  
int型の値を100で割ったものをfloat型として返します.   
Short型に格納された値を通常のdegree角度値に変換する際など使用します.   
  
<br>  
```  
/**
 * @brief Short type value divided by 100 to float type.
 *
 * @param[in] val Source value
 * @return float Source value / 100
 */

float Meridian::HfShort2float(short val)
{
    return static_cast<float>(val) / 100;
}
```