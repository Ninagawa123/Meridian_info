----  
<h3>bool cksm_rslt(short arr[ ], int len)</h3>
----  
Meridim配列のチェックサムを判定します.   
引数1 : Meridim配列(short型)
引数2 : 配列の長さ(int型)
Meridim配列の末尾-1までの数値を合計し, 最後にビット反転しShort型に変換したチェックサム値と,   
Meridim配列の末尾のチェックサム値を比較します.   
結果がチェックOKならTrue, NGならFalseを返します.   
  
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

bool Meridian::cksm_rslt(short arr[], int len)
{
    int _cksm = 0;
    for (int i = 0; i < len - 1; i++)
    {
        _cksm += int(arr[i]);
    }
    if (short(~_cksm) == arr[len - 1])
    {
        return true;
    }
    return false;
}
```