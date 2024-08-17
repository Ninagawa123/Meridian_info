----  
<h3>short cksm_val(short arr[ ], int len)</h3>
----  
Meridim配列のチェックサムを算出します.   
引数1 : Meridim配列(short型)  
引数2 : 配列の長さ(int型)
Meridim配列の末尾-1までの数値を合計して最後にビット反転し,   
Short型に変換したものをチェックサム値として返します.   
  
<br>  
```
/**
* @brief calculate checksum of Meridim
*
* @param[in] arr Meridim array
* @param[in] len Length of array
* @return short checksum value
*/

short Meridian::cksm_val(short arr[], int len)
{
    int _cksm = 0;
    for (int i = 0; i < len - 1; i++)
    {
        _cksm += int(arr[i]);
    }
    return short(~_cksm);
}
```