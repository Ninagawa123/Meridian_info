# Coarding guidelines
  
<br>  
## C++ LLVM Coding Standardsに準拠
----  
Arduino, ESP32, TeensyなどのC++系のコーディングスタイルはおおむね [LLVM Coding Standards](https://llvm.org/docs/CodingStandards.html) に準拠する.  
自動変換の .clang-format では現状, 下記のような定義とする.

<br>
#### .clang-format:
```
BasedOnStyle: LLVM
ColumnLimit: 100
AlignTrailingComments: true
AlignConsecutiveMacros: true
```
  
<br>
その他, Meridianとして下記のローカルルールを推奨する. 

<br>
## C++ Meridian 命名規則ローカルルール
----  
1. 変数名はスネークケースとする. 例）flg.meridim_rcvd  
1. 関数名はスネークケースとする(ROS風).  
1. クラス名・構造体名・列挙型名はパスカルケースとする.  
1. 関数宣言時の引数は a_ をつける. 例）a_meridim  
1. 関数内の補助変数は _tmp をつける. 例）int count_tmp  
1. モジュールとなるファイル名は mrd_ をつける. 例）mrd_wifi.h  

<br>
## スネークケースの使い方  
1. カテゴリ(名詞) > 内容（名詞・動詞）> 補足 の優先順とする. 例) mrd_wire0_init  
2. meridianオリジナルの関数は先頭に mrd_ をつける.  
3. 関数をライブラリやクラスに昇格する際は, _の区切りでカテゴライズする.  
   例）　mrd_wire0_init → mrd_wire0.init  
  

<br>
## C++ ドキュメンテーションコメント
----  
  
関数などの解説には下記のように///を使用する.  

```
/// @brief 解説.
/// @param 引数.
/// @return 戻り値.
```

/\*\* \*/はコードの改造時にブロックコメントアウトとして使用できるよう, 
ドキュメンテーションコメントとしては使用しないこと. 

変数などの解説は同じ行もしくは一つ上の行に // でコメントをつける. 
  
こうすることで,  VSCODE上で関数や変数にカーソルを当てた時に説明が表示されるようになる.  

<br> 
## 主な用語
----  

|用語|説明|
|:--|:------|
|Meridian|デバイスやソフトを中間プロトコルでつなぐリアルタイムシステム|
|Meridim|Meridianのコアとなる配列 |
|Meridim90|基準となる簡易的な固定配列(90要素, 180バイト 固定)|
|MeridimFX|基準となる簡易的な固定配列(最大 700要素, 1400バイトまで可変長)|


<br> 
## 主な定数の命名ルール
----  

|用語|説明|
|:--|:------|
|MODE_|動作モードのconfig|
|EEPROM_|EEPROM関連|
|CHECK_|起動時の動作チェック関連|
|MONITOR_|シリアルモニタリング|
|MOUNT_ |ハードウェアのマウント設定|
|PAD_ |ジョイパッド・リモコン関連|
|SERVO_|サーボの通信設定関連|
|MCMD_ |Meridimのマスターコマンド|
|PIN_|ピンアサイン|
|IXR_|L系統のサーボパラメータ|
|IXL_|R系統のサーボパラメータ|
|IXC_|C系統のサーボパラメータ|
|MRD_|Meridim90の配列キー（例外ありconfig.h参照）|

<br>  
## C# 未定  
----  
C# は主にUnityで使用します.   
詳細未定ですが,  計算コードなどをなるべくコピペなどでそのままC++に移植できる書式を想定しています.   
  
<br>  
## Java 未定  
----  
JavaもC#と同様, 計算コードなどをC++に移植しやすい書式を想定しています.   
  
<br>  
## Python PEP8に準拠 
----  
  
Python ファイルはおおむね [PEP8](https://peps.python.org/pep-0008/) に準拠します. 
  
(現状, Meridian_console.pyはまだPEP8を遵守できていません. )
