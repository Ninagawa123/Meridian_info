----  
<h3>int seq_predict_num(int previous_seq_num)</h3>
----  
シーケンス番号の予測値として引数に＋１した値を返します.    
引数 : 前回のシーケンス番号  
戻り値の範囲は 0-59,999のint型  
※ Meridimのシーケンス番号は0-59,999を繰り返す.   
  
<br>  
```  
/**
 * @brief Generate expected sequence number from imput.
 *
 * @param[in] previous_seq_num Previous sequence number.
 * @return int, Expected sequence number. (0 to 59,999)
 */
  
int Meridian::seq_predict_num(int previous_seq_num)
{
    int _x = previous_seq_num + 1;
    if (_x > 59999) // Reset counter
    {
        _x = 0;
    }
    return _x;
}
```