# PokeAPIで練習するJavaScript --補足編--

## はじめに
説明省きすぎてJavaScriptは分かったけど、モヤモヤ感が残る内容になってしまったので、少し伏線回収したいと思います。  
  
ということで、APIを自作するのですが、素のJavaScriptで作るのは無理ゲーなので、折角なら勉強したマイコンを使います。  
  
## 用意するもの
- ESP32(M5Stackでも可)  
- Platform IOが使えるPC  
  
## 0. PlatformIOの使いかた
[PlatformIOの使い方はここから思い出してください](https://qiita.com/nextfp/items/f54b216212f08280d4e0)  

## 1. WiFiの接続
WiFiの接続方法は2つあります。  
基本的に1番がセキュリティー的におすすめですが、センターのWiFiだとなぜか1番が使えないので、その場合2番を使いましょう。

### 1. WiFiの接続方法その1 
#### マイコン側の設定
`smart config`という機能を使用します。
次のようなコードを書いてください。
```main.cpp
#include <Arduino.h>
#include <WiFi.h>

void setup()
{
  // put your setup code here, to run once:

  Serial.begin(115200);
  Serial.println("smart config start!");
  WiFi.begin();
  // WiFiに接続できるまでループ
  while (WiFi.status() != WL_CONNECTED)
  {
    // millis()はマイコンの起動時間を取得できる関数。
    // ESP32は前回の接続情報を記憶し、自動で接続を試みるので、少しループを回して待機。
    // 定期的に"."を出力
    if (millis() % 500 == 0)
    {
      Serial.print(".");
      delay(1);
    }
    if (millis() > 10000) // 　自動接続に失敗したら入る処理
    {
      Serial.println("Smart Config Start!");
      WiFi.beginSmartConfig();
      // スマートコンフィグできるまで待機。
      while (!WiFi.smartConfigDone())
      {
        // 定期的に"."を出力
        if (millis() % 500 == 0)
        {
          Serial.print(".");
          delay(1);
        }
      }
      Serial.println("Smart Config Done!");
    }
  }

  Serial.println("WiFi Connected.");

  // WiFiが接続できた証拠にIPアドレスを表示。
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void loop()
{
  // put your main code here, to run repeatedly:
}
```

コードを書き終わったら、マイコンに書き込んでシリアルモニターを確認しましょう。
> ボーレートを115200に設定するのを忘れずに。

#### スマホ側
Android派の方は読み替えてお進みください。  
App Storeで`ESP touch`と調べて、`Espressif Esptouch`をインストールしてください。  
![alt text](image.png)  
  
EspTouchをタップ。  
![alt text](image-1.png)  
WiFiのパスワードを入力し、`confirm`をタップし、しばらく待つとESP32がWiFiに接続されます。  
![alt text](image-2.png)

なぜかセンターではつながりません。

### 2. WiFiの接続方法その2
```
#include <Arduino.h>
#include <WiFi.h>

const char *ssid = "WiFiのSSID";
const char *password = "WiFiのパスワード"; 

void setup()
{
  // put your setup code here, to run once:

  Serial.begin(115200);
  Serial.println("smart config start!");
  WiFi.begin();
  // WiFiに接続できるまでループ
  while (WiFi.status() != WL_CONNECTED)
  {
    // 定期的に"."を出力
    if (millis() % 500 == 0)
    {
      Serial.print(".");
      delay(1);
    }
  }

  Serial.println("WiFi Connected.");

  // WiFiが接続できた証拠にIPアドレスを表示。
  Serial.print("IP Address: ");
  Serial.println(WiFi.localIP());
}

void loop()
{
  // put your main code here, to run repeatedly:
}

```

> [!WARNING]
> ssidとパスワードを書き間違えないようにしてね。

実行するとどちらの方法もIPアドレスが表示されます。