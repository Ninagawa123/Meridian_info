----  
<h3>void print_controlpad(int pad_mount, int pad_freq)</h3>
----  
起動時などに接続されたコントロールパッドの種類を表示します。  
引数1 : コントロールパッドのタイプ番号  
引数2 : コントロールパッドの問い合わせフレーム間隔(ms)  
  
<コントロールパッドのタイプ番号>   
0:None, 1:SBDBT, 2:KRC-5FH, 3:PS3, 4:PS4, 5:Wii_yoko, 6:Wii+Nun, 7:WiiPro,  
8:Xbox, 9:Merimote, 10:Retro  
  
<br>  
```  
/**
 * @brief Print mounted control pad.
 *
 * @param[in] pad_mount Type of control pad.
 * @param[in] pad_freq Freqency of calling control pad.(every ms)
 */

void Meridian::print_controlpad(int pad_mount, int pad_freq)
{
    Serial.print("Controll Pad Receiver mounted: ");
    switch (pad_mount)
    {
    case 0:
        Serial.println("None. ");
        break;
    case 1:
        Serial.print("SBDBT ");
        break;
    case 2:
        Serial.print("KRC-5FH ");
        break;
    case 3:
        Serial.print("PS3");
        break;
    case 4:
        Serial.print("PS4");
        break;
    case 5:
        Serial.print("Wii_yoko");
        break;
    case 6:
        Serial.print("Wii+Nun");
        break;
    case 7:
        Serial.print("WiiPro");
        break;
    case 8:
        Serial.print("Xbox");
        break;
    case 9:
        Serial.print("Merimote");
        break;
    case 10:
        Serial.print("Retro");
        break;
    default:
        break;
    }

    if (pad_mount != 0)
    {
        Serial.print("  freq: ");
        Serial.println(pad_freq);
    }
    delay(100);
}
```