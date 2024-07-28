----  
<h3>void mrd_wire0_run()</h3>
----  
AHRSセンサーからデータを読み取るための関数を実行する.  
  
<br>  
```  
/// @brief AHRSセンサーからデータを読み取るための関数を実行する.
void mrd_wire0_run() { // ※IntervalTimer用の関数のためvoidのみ可
  mrd_wire0_read_ahrs_i2c(ahrs);
}
```  