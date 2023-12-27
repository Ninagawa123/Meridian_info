----  
<h2> <b>short float2HfShort(float val)</b>  </h2>
----  
float型の値を100倍したものをShort型として返します。  
引数 : float値  
戻り値として-32767 to 32767までの小数点2桁までの精度の値を扱えます。　　
※Meridainでは-327.67度〜327.67度の範囲のdegree角度値をShort型に格納するために使用しています。  
  
<br>  
```  
/**
 * @brief Evaluate checksum of Meridim.
 *
 * @param[in] arr[] Meridim array
 * @param[in] len Length of array
 * @return true Check OK
 * @return false Check NG
 */  

short Meridian::float2HfShort(float val)
{
    int _x = round(val * 100);
    if (_x > 32766)
    {
        _x = 32767;
    }
    else if (_x < -32766)
    {
        _x = -32767;
    }
    return static_cast<short>(_x);
}
```