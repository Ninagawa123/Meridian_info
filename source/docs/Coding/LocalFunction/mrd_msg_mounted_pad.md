----  
<h3>void mrd_msg_mounted_pad()</h3>
----  
システムに接続設定したジョイパッドのタイプを表示する.  
  
<br>  
```  
/// @brief システムに接続設定したジョイパッドのタイプを表示する.
void mrd_msg_mounted_pad() {
  Serial.print("Pad Receiver mounted : ");

  if (MOUNT_PAD == MERIMOTE) {
    Serial.println("Merimote.");
  } else if (MOUNT_PAD == BLUERETRO) {
    Serial.println("BlueRetro.");
  } else if (MOUNT_PAD == SBDBT) {
    Serial.println("SBDBT.");
  } else if (MOUNT_PAD == KRR5FH) {
    Serial.println("KRC-5FH.");
  } else {
    Serial.println("None (PC).");
  }
}
```  