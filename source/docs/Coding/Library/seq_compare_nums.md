----  
<h3>bool seq_compare_nums(int predict_seq_num, int received_seq_num)</h3>
----  
シーケンス番号の予測値として引数に＋１した値を返します。   
引数 : 前回のシーケンス番号  
戻り値の範囲は 0-59,999のint型  
※ Meridimのシーケンス番号は0-59,999を繰り返す。  
  
<br>  
```  
/**
 * @brief Compare expected seq number and received seq number.(0 to 59,000)
 *
 * @param[in] predict_seq_num Predict sequence number.
 * @param[in] received_seq_num Received sequence number.
 * @return true OK
 * @return false NG
 */  
  
bool Meridian::seq_compare_nums(int predict_seq_num, int received_seq_num)
{
    return (predict_seq_num == received_seq_num);
}
```