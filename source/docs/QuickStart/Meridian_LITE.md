----  
## Meridian_LITE ボードについて  
----  

<img width="400" src="https://user-images.githubusercontent.com/8329123/177022808-50ccf555-4afd-450c-a07e-3302771d45cf.jpg">

"Meridian board -LITE-" は半二重通信回路2系統を搭載とSPI,I2Cなどの出力ピンを備えたボードです。  
ESP32devkitCを搭載することで、半二重通信方式のコマンドサーボを扱えるロボット用ボードとして機能します。  
  

### ピンアサイン

<img width="800" alt="lite_pinassign" src="https://user-images.githubusercontent.com/8329123/177044311-0021c4bc-42ca-4f08-afd5-a440fdac624f.png">
ピンアサインは上記の通りです。  
IOがESP32DevkitCのピン番号に該当しているので、ESP32Devkitのデータシート等を参考に使うことができます。  
またSPIやSDカードを使用しない場合は、アサインされたピンをGNDと組み合わせるなどで他の役割を与えることもできます。  
Fとなっている箇所は未接続のピンとなっています。背面で好きな箇所と導線をはんだ付けすることで自由に機能を与えることができます。  
搭載するESP32DevkitCはUSBコネクタがMeridian -LITE-のロゴ側を向くように設置してください。  
  

### マウントと機能拡張
<img width="400" alt="SS 2267" src="https://user-images.githubusercontent.com/8329123/177022972-3c9931ae-cfe3-44bb-9145-84303330a387.png">
上図のようにKHR-3HVのランドセルに本体無改造で固定することができます。  
ただしランドセル側とボードの間には1~2mm程度のスペーサーが入れるとボード底面の干渉を回避できます。  
秋月電子で販売のSDカードホルダ[AE-MICRO-SD-DIP]をSPI端子にそのまま接続することができます。  
ただしSDカードホルダ側にメスのピンヘッダを取り付ける必要があります。  
９軸センサについては秋月で販売のBNO055[AE-BNO055-BO]をI2Cに接続することを標準としています。  
またリモコン受信機KRR-5FHも内臓できます。左下のビス穴のみを使いた簡易固定ができます。  
蓋もギリギリですが閉じることができます。  
  

## Meridian_LITE インストール方法
Meridian LITE のボードを使う方法です。  
開発環境として、VScodeとPlatformIOを使用します。  
※ArduinoIDEを使用した場合、WIFIライブラリの関係でESP32のパフォーマンスが発揮しきれません。  
  

### PlatformIOのインストール
ご利用の環境にPlatformIOをインストールしてください。  
参考URL  
https://qiita.com/JotaroS/items/1930f156aab953194c9a  
https://platformio.org/  
  

### 開発環境のインストール  
PlatformIOを起動し、「Platformes」の検索窓で「ESP32」を検索します。  
  
<img width="300" alt="1" src="https://user-images.githubusercontent.com/8329123/176886184-a702c39d-9b57-41f9-8653-66529a109976.png">  
「Espressif 32」が見つかるので、バージョン「3.5.0」をインストールします。  
新しいバージョン(4.x.x)だとwifi関連がうまく動かない可能性が高いです。  
  

### 新規プロジェクトを作成する  
<img width="600" alt="2" src="https://user-images.githubusercontent.com/8329123/176886274-bbe57e27-7a14-4a1a-8df7-48d7f7bf495f.png">  
「Home」タブより「+New Project」を選びます。  
  
<img width="400" alt="3" src="https://user-images.githubusercontent.com/8329123/176886509-4ad96264-c89f-4e3f-9b69-21799f7ad162.png">  
Name:Meridian_LITE_xxxxxxx  
Board:Espressif ESP32 Dev Module  
Framework:Arduino Framework  
とします。  
  

### ライブラリのインストール
#### IcsHardSerialClassを導入する
<img width="600" alt="SS 2266" src="https://user-images.githubusercontent.com/8329123/177020842-92d11f38-49b1-4cde-86f8-171febd849da.png">
PCのエクスプローラー(Macはファインダ)で内で先ほど作成したプロジェクトのフォルダのある場所を探します。  
その中に「lib」があるのを確認します。  　
  
近藤科学様のサイトより、ICS_Library_for_Arduino_V2_1.zip をDLし、解凍します。  
https://kondo-robot.com/faq/ics-library-a2   
解凍後、さらにその中のIcsClass_V210.zipを解凍します。  
IcsClass_V210のフォルダを、さきほどの「lib」に入れます。  
  
<img width="300" alt="SS 2264" src="https://user-images.githubusercontent.com/8329123/177020750-c8210d92-e1d1-4970-a4c3-e04960a4a3f7.png">
ディレクトリ構造が上図のようになっていればOKです。  
  

#### Adafruit_BNO055を導入する
アリ頭のアイコンから「QUICK ACCESS」→「PIO Home」→「Open」を開きます。  
右画面PIO Homeのタグの左メニューから「Libraries」を選択します。  
<img width="400" alt="5" src="https://user-images.githubusercontent.com/8329123/176911609-83cf3795-f890-4c41-88dc-92c2efcfb4ff.png">  
今回のプロジェクト（Meridian_LITE_xxxxxx）を選択し、Addボタンを押します。  
  

#### メインコードの作成
<img width="400" alt="6" src="https://user-images.githubusercontent.com/8329123/176911852-b245204b-b8c9-4379-9db5-7176ab3901d0.png">  
再び画面左上のファイルアイコンを押し、「src」→「main.cpp」を選択します。  
githubのコード（[URL](https://github.com/Ninagawa123/Meridian_LITE/blob/main/ESP32/Meridian_LITE_20220612/main.cpp)）をmain.cppのコードとしてコピペします。  
  

#### ESP32のシリアル通信ピンの設定
ESP32のデフォルトではSerial1のUARTシリアル通信が使う事ができないため、設定を変更して使えるようにします。  
  
PlatformIOを一旦閉じます。  
  
https://qiita.com/Ninagawa_Izumi/items/8ce2d55728fd5973087d  
を参考に、   
RX1を9番ピンから32番ピンに変更、  
TX1を10番ピンから27番ピンに変更する設定をしておきます。  
  

#### platformio.iniの設定
「platformio.ini」を開くと、  
<img width="600" alt="7" src="https://user-images.githubusercontent.com/8329123/176912503-e552925d-ca64-43e9-a7ae-8ce2ff32dd13.png">  
のようになっているので、以下のように書き加え、  
シリアルモニタのスピードを500000に、またOTAという無線でのプログラム書き換え機能を削除してメモリ領域を増やす設定にします。  
>[env:esp32dev]  
>platform = espressif32  
>board = esp32dev  
>framework = arduino  
>monitor_speed = 500000  
>board_build.partitions = no_ota.csv  
>lib_deps = adafruit/Adafruit BNO055@^1.5.3  
  

#### メインコードの修正
main.cpp内の  
>#define AP_SSID "xxxxxx"             // アクセスポイントのAP_SSID  
>#define AP_PASS "xxxxxx"             // アクセスポイントのパスワード  
>#define SEND_IP "192.168.1.xx"       // 送り先のPCのIPアドレス（PCのIPアドレスを調べておく）  

を変更する。  
送り先のPCのIPアドレスは、  
windowsならターミナルを開いてipconfigコマンド  
ubuntuならip aコマンド  
macなら画面右上のwifiアイコンから"ネットワーク"環境設定...  
で確認できます。  
  

#### メインコードの設定
main.cpp内の設定を手持ち機体に合わせて変更します。  
  
>#define SD_MOUNT 1   

　→ SDリーダーの搭載 (0:なし, 1:あり)  
  
>#define IMU_MOUNT 1  

　→ 6軸or9軸センサーの搭載 (0:なし, 1:BNO055, 2:MPU6050(未実装))  
  
>#define JOYPAD_MOUNT 2  

　→ ジョイパッドの搭載 (現在2のKRC-5FHのみ有効, ジョイパッドを接続しない場合は0)  
  

>/* 各サーボのマウントありなし（1:サーボあり、0:サーボなし） */  

　→ idl_mt[0]〜がサーボ左側系のサーボID 0〜 です。接続しているサーボIDはTrue, 非接続のIDにはFalseを設定します。  
　→ idr_mt[0]〜がサーボ右側系のサーボID 0〜 です。上記と同様に設定します。  
  

>/* 各サーボの直立デフォルト値　(KRS値  0deg=7500, +-90deg=7500+-2667  KRS値=deg/0.03375) */  

　→ 各サーボについてのトリム値を設定できます。  
  

#### ビルドとアップロード
<img width="612" alt="9" src="https://user-images.githubusercontent.com/8329123/176913879-d05eb45d-15a0-47f6-a538-aa481b31e988.png">  
画面左下のチェックマークを押すと、ビルドが行われます。  
押下して「====== [SUCCESS] Took x.xx seconds」と表示されればビルド成功です。  
  
PCとESP32をUSBケーブルせ接続し、矢印ボタンを押すとESP32の内容が上書きされます。  
アップロードが失敗する場合でも、何度か行うことで成功する場合があるので試してみてください。  
  

#### PC側の設定
以降のテキストは準備中ですが、下記を参考にPC側の設定をすることで、デモを動作できると思います。  
https://github.com/Ninagawa123/Meridian_core  
  
