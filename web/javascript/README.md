## JavaScriptのページです。

## 「JavaScript難しそうだなぁ」
こんなこと思っていますか？  
実は習得のしやすい言語といわれています。 構文は、Cと似ています。
習得しやすい言語ランキングみたいなものがあったとしたら、一位がPythonで、二位がJavaScript的な感じになると思います。  
しかし、Cを習得している方はPythonよりもJavascriptの方が圧倒的に習得しやすいと思います。  
というか、cと違うところがあんまない。(printfじゃない、ポインタ機能がないくらい？)  
ということで肩の力抜いていきましょう。  

### JavaScriptという言語紹介
JavaScriptというのは、ブラウザ上で動くという言語です。  
昔自分も勘違いしてましたが、`Java`と`JavaScript`は違う言語です。  
> Javaは禿げるほどムズイし、オワコン(うっかり失礼しました。すいません。)。JavaScriptは結構簡単で、流行っている。

普通のJavaScriptはブラウザ上でしか動きませんし、ブラウザ上ではJavaScript以外のプログラミング言語は動きません。ブラウザとラブラブ 😍 な言語です  
> 普通じゃないJavaScriptはブラウザ以外でも動くけど、それはまた今度。 
 
「htmlとcssもブラウザ上で動くから、JavaScript以外のプログラミング言語も動くぞ!」って思うかもしれませんが、あやつらは実はプログラミング言語じゃなくてマークアップ言語といいます。面倒くさいね。  
そんなことはさておき、JavaScriptを勉強していきましょう。

### 本題
#### 8日目~11日目 JavaScript入門
教材についてなんですが、迷ってます。  
とりあえず、これをやってみてください。  
[一日で多分駆け抜けられるJavaScript](https://github.com/ZDK-UTsukuba/ipc-web-training-2024/tree/master/phase2/handouts)  

ガッチリやる方がいいのかな。もし上のやつをやってもよくわからなかったら下をやってみてください。  
[文系大学生のためのJavaScript入門](https://zenn.dev/ojk/books/intro-to-javascript)

#### 12,13日目 JavaScript練習
JavaScript中間試験みたいなものです。  
これができたら、JavaScriptの基本は大丈夫です。  
[pokeAPIで練習するJavaScript](./pokeAPI)  

#### 14日目 WEBの仕組み(http)補強
APIについての説明を端折りすぎたので、補足資料書いたら結構長くなってしまいました。  
手を動かして遊ぶ形式ですが、自分で考えてコードを書く部分はありません。伏線回収回みたいな感じです。  
[APIをマイコンで作ろう](./pokeAPI_supplyment)

#### 15日目　非同期処理
JavaScriptのボスの非同期処理を勉強します。  
Cのポインターよりは難しくないけど、みんなが詰まるポイントです。  

1. javaScriptの処理の順番  
文中に出てくるコードは実際に手を動かしましょう。  
[javaScriptの処理の順番](https://samehack.com/javascript-asynchronous/)  

2. async awaitの使い方  
以下のページでasync/await文の使い方を身につけましょう。  
javaScriptの非同期処理で使う関数といえば、コールバック関数、promise、async/awaitです。  
この中で、一番分かりやすくて一番使うのが、async awaitです。async awaitなしにはコードは書けません。  
しかし、promiseに関しては結構難しいし、あまり使わないのでちゃんと理解する必要はありません。  
promiseとコールバック関数に関しては、サラサラと読み流して構いませんが、async await部分は実際にコードを動かしてね。   
[async awaitの使い方](https://www.otwo.jp/blog/asynchronous-processing/)