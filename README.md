# __HTMLにまつわる用語について__

## 1. [URLについて](#section1)
***
## 2. [クエリ文字列について](#section2)  
 * パスパラメーター（パス変数）とは〜クエリパラメータとの違い〜  
 * 見た目の違い
 * 中身の違い
***
## 3. [HTTPメソッドとは何か](#section3)
  * GET  
  * POST  
  * PUT  
  * PATCH  
  * DELETE  
***  
## 4. [HTTPステータスコードについて](#section4)
  * -200
  * -201
  * -400
  * -404
  * -500  
***  
## 5. [HTTPリクエストについて](#section5)  
  *リクエストライン  
  *リクエストヘッダ  
  *リクエストメッセージボディ  
***  
## 6. [HTTPレスポンスについて](#section6)　　
  *ステータスライン  
  *レスポンスヘッダ   
  *レスポンスボディ
***
## 7. [JSONとは何か](#section7)  
  *JSONの書き方  
  *文字列  
  *数値  
  *null  
  *bool値  
  *オブジェクト  
  *配置  
***
<br>
<br>
<br>

# __<a id="section1">1.URLについて</a>__

URLとは __「Uniform Resource Locator」__ の略称で、インターネット上に存在する情報資源（文章や画像など）の場所を指し示す技術方式。  
簡単に言えばインターネットにおける住所です。アドレスとも呼ばれます。  
通常 __<font color ="green">「プロトコル://ドメイン名/ディレクトリパス名/ファイル名」</font>__ という形式で構成されます。  

例）  
<img width="250" alt="URL" src="img/URL.webp"> 


# __<a id="section2">2.クエリ文字列について</a>__

クエリ文字列「query string」とはwebブラウザなどがwebサーバーに送信するデータを、送信先を指定するURLの末尾に特定の形式で表記したもの。　
URLの末尾に「？」を付け、続けて「名前＝値」の形式で内容を記述する。  
値が複数あるときは「＆」で区切り「？名前１＝値１＆名前２＝値２＆名前３＝値３」のように続ける。　 
# パスパラメーター（パス変数）とは〜クエリパラメータとの違い〜  
## 見た目の違い   
  
__<font color ="green">1.https:// qiita.com/ search</font>__  
__<font color ="green">2.https:// qiita.com/search?q=pathparameter</font>__  
1のパスパラメータは「search」の部分になる。
２の場合は、パスパラメータは１と同じく「search」、クエリパラメータは「?q=pathparameter」  
  
## 中身の違い　　  
  
例：株式会社アニメ（ドメイン：Anime.co.jp）に営業部(sales)があり、チームが以下のように分かれているとする。  
  
SalesTable  

| id  | name     |  
| --- | -------- |  
| 1   | Isono    |  
| 2   | Doraemon | 

チームの中のユーザーは以下の通り  
  
UsersTable  
  
| id | sales_id | name     |  
| -- | -------- | -------- |  
| 1  | 1        |  sazae   |
| 2  | 1        | kathuo   |
| 3  | 1        | wakame   |
| 4  | 2        | nobita   |
| 5  | 2        | doraemon |
| 6  | 1        | namihei  |
  
営業部のIsono(磯野)チームのページを表示するとURLは以下のようになる。  
  
__<font color="green">http:// Anime.co.jp/sales/{group_id}</font>__
  
「パスパラメータ」は __<font color="red">特別なもの（画像など）を表示したいときに必要になります。</font>__　　

 <br>

__<font color="blue">IsonoチームのSalesTableは「１」</font>__  
__<font color="green">http:// Anime.co.jp/sales/1</font>__  
もし、メンバー一覧を画面に表示したい場合は、下記のURLとする。 __<font color="red">(表示)</font>__  
__<font color="green">http:// Anime.co.jp/sales/1/members</font>__  
「クエリパラメータ」は __<font color="red">特定のもの（画面など）に条件を加える場合に必要になります。</font>__  

<br>

例：上記のメンバー一覧から特定の人を検索したい場合（今回はID検索と想定）  
「wakame」の検索をします。__<font color="red">（条件の追加）</font>__  
  
__<font color="green">http:// Anime.co.jp/sales/1/members?</font>__ __<font color="red">id=3</font>__  
  
<br>

  ## __パスパラメータ　:特定のものを判別する際に必要__  
  ## __クエリパラメータ :特定のものに条件を追加する際に必要__  
  
<br>
<br>
<br>    
  
# <a id="section3">__3.HTTPメソッドとは何か</a>__

## HTTPメソッドとは、対象のリソースに対して「何をしたいか」を支持する。  
HTTPメソッドにはおおまかにGET、POST、PUT、PATCH、DELETEがある。  

<br>

***
  
## __GETについて__  

<br>

URLで指定した情報を要求しURLがファイル名のときはそのファイルの中身を、プログラム名のときはそのプログラムの出力を返す。  
  
<font color="green">例：googleでjavaについて検索した。</font> __<font color="red">（googleでjavaについて情報を要求した。）</font>__  
GETメソッドはURLに追記されて値を送ります。（公開されている）

***

## __POSTについて__  

<br>

URLで指定した情報を送り内容をBody部に格納する。  
  
<font color="green">例：Amazonでクレジットカードにてカード情報を入力した。</font> __<font color="red">（Amazonでカード情報を値の見えないwebサーバーに送った。）</font>__  
POSTに関しては要求を封筒に入れて送信する。開封しないと見えない（非公開）  

<br>
  
## __GETとPOSTの違い__  

<br>

__<font color="red">GETメソッドはURLの後ろに値が表示されます。</font>__  
__<font color="red">POSTメソッドは値を見えないところに隠して送りますのでその為、URLには表示されません。</font>__  

<br>  

## __PUTについて__  
<br>  

情報を置き換える。POSTはリソースが追加されるが、PUTは既存のデータが上書きされる。

<br>

***

## __PATCHについて__  
<br>

リソースの部分置き換え。修正。  

***
  
## __PUTとPATCHの違い__　　
例:  
```
{  
  "FirstName" : "Taro",  
  "LastName" : "Yamada",  
  "age" : 25,  
  "sex" : male,  
  "state" : Tokyo  
}  
```
<br>
  

__PUTリクエストの場合__  
```
{ 
"FirstName" : "Ichiro",  
}
```  
  
__<font color="green">完全にデータが上書きされ、LastNameやageといった情報も消えてしまう。</font>__  

***

<br>

__PATCHリクエストの場合__  
```
{  
  "FirstName" : "Ichiro",  
  "LastName" : "Yamada",  
  "age" : 25,  
  "sex" : male,  
  "state" : Tokyo  
}
``` 

__<font color="green">データの一部が上書きされ、LastNameやageといった情報はそのまま。</font>__  

<br>

## __DELETEについて__  

<br>

DELETEメソッドとは、名の通り削除を求めるもの。通常は認証システムと合わせて席の権限を持つ利用者のみに許可される。

<br>
<br>
<br>
<br>

# __<a id="section4">4.HTTPステータスコードについて</a>__ 

<br>

__HTTPステータスコードとは、HTTPレスポンスに含まれるWebサーバーの処理結果を表現する３桁の数字のことを指す。__  
Webサーバーからの返事を表すコードです。要求にたいして処理できなかったり、エラーなどをコードで返します。  

<br>

 ## __200 OK__  
 ***  
 __「OK」です。<font color="green">リクエストは正常に処理できた。</font>__  
 <img width="400" alt="URL" src="img/200.jpeg">  
__・成功時に返すステータスコードとして最も多用される。__  
  
・リクエストした処理が成功。指定したデータの取得に成功。  
  ・GET：ボディにリソースが含まれる。  
・PUT,POST:ボディに処理結果が含まれる。  

## __201 Created__  
***  
__「リクエスト成功しリソースが作成完了！」__  
<img width="400" alt="URL" src="img/201.jpg">  
・POST,PUT：リクエストが成功しリソースが作成された。
・POSTの場合はレスポンスのLocationヘッダにURLが入る。  
・ユーザーの新規登録、画像のアップロード、DBのテーブル追加など。  
・ボディには新しく作成したリソースを入れることが多いが、特に何も入れなくて良い。  
  
## __400 Bad Request__  
***  
__「リクエストが不正」４００番台はクライアントエラーです。__  
<img width="400" alt="URL" src="img/400.jpg">  
・リクエストが不正  
・定義されていないメソッドを使ったり、パラメータに間違いがあるなど、クライアントのリクエストがおかしい場合。    
・他に適切なクライアントエラーを表すステータスコードがない場合にも用いる。  

## __404 Not Found__  
***  
__「Webページが見つからない」 一番みんな知ってますね！__  
<img width="400" alt="URL" src="img/404.jpeg">  

・リクエストされたリソースが存在しない  
・Webで頻繁にに見られる有名なエラーステータスコードのひとつ  
・そもそもURI自体が存在しないのか、取得対象のリソースが存在しなかったのかなど、詳細情報を示す必要がある。  
・許可されていないクライアントからリソースの存在を隠す為、４０３の代わりに４０４を返すこともある。  
  
## __500 Interal Server Error__    
***  
__「なんらかのサーバ内で起きたエラー」500番台はサーバエラー__  
<img width="400" alt="URL" src="img/500.jpeg">  
  
・サーバ側に何かしらの異常が発生し正常なレスポンスが返せない。  
・「何らかの異常が発生しました」というようなメッセージが返ることが多く、クライアント側では解決不能  
・他に適切なエラーコードがない場合にも用いる    
・サーバーのエラーログなどを見ると原因がわかることもある。  
  
# __<a id="section5">5.HTTPリクエストについて</a>__  

__HTTPリクエストは３つの部品から成り立っている。__  
***  
__<font color="green">HTTPリクエストライン</font>__  
「HTTPメソッド（GETやPOST）・URI（何を）・どんなルールで」が書いてある
    
__<font color="red">HTTPリクエストヘッダ</font>__  
「内容」が書かれている。  
  
例）    
|フィールド名| 意味                                  |
|----------|------------------------------------- |
|Host      | リクエスト先サーバー名DNS名を利用         |
|User-Agent| ユーザーが利用しているブラウザの種類やOS情報|
|Referer| 前のWebページのアドレスを表示               |
|Accept | 受け取り希望のデータの種類をサーバに通知（画像の種類や言語、文字コードなど）|  

  
__<font color="blue">HTTPリクエストメッセージボディ</font>__  
メッセージボディ。リクエストの追加情報。メッセージが存在しないHTTPリクエストメッセージもある。  
<br>
<br>  

 # __<a id="section6">6.HTTPレスポンスについて</a>__  
__HTTPレスポンスも３つの部品から成り立っている。__  

***  

__<font color="green">ステータスライン</font>__  
HTTPリクエストの結果を返します。HTTPステータスコードなど。 
<br>  

__<font color="red">レスポンスヘッダ</font>__  
ステータス行では表現しきれない、レスポンスに関する追加のデータを付与するためのヘッダー。  
サーバーに関する情報や、URIで指定されたリソースに関する追加の情報が記録されます。  
  
例）
|フィールド名| 意味                                                                  |
|----------|--------------------------------------------------------------------- |
|Location  | 訪問者をリクエストURL以外の場所へ「リダイレクト」するためのフィールド（項目）です。|
|Server| サーバ・ソフトの名称やバージョンに関する情報　　　|
|Accept-Ranges| Range要求があったときに対応可能か通知   |
|WWW-Authenticate | ユーザ認証用のデータを返す|    
<br>
  
__<font color="blue">レスポンスボディ</font>__  
Webブラウザで表示する情報。メインのリソース（コンテンツ）  
<img width=max alt=URL src=img/HTTP_header.jpeg> 
<br>

# __<a id="section7">7.JSONについて</a>__ 

JSONとは「JavaSprict Object Notation」の略で、「JavaScriptのオブジェクトの書き方を元にしたデータ定義方法」のことです。  
サポート言語も多く、Python、PHP、JavaScript、C++、Javaなどで利用でき、JSONを間に挟むことで各プログラミング言語間のデータの受け渡しがとても簡単にできます。  
<br>
  
 # __JSONの書き方__  
<br>

```
{ 
"key1":"value1",  
"key2":"value2",  
"key3":"value3"   
}
```

<br>

# __JSONが対応しているデータ型__  
JSONは次のデータ型に対応しています。 

***
   
## __文字列__  
文字列はダブルクォーテーション(")、バックスラッシュ(\)以外の文字であればなんでも使用できます（もちろん日本語もOK）。
  ```
  {
    "name":"tanaka"
  }
```
## __数値__  
数値はダブルクォーテーションで囲みません。ダブルクォーテーションで囲むと文字列扱いになるので注意が必要です。  
  
```
{
  "id",1
}  
```
## __null__    
nullは全て小文字で指定します。  
```
{
  "id",null
}
```    
## __bool値__  
bool値（true or false）の指定も可能。  
```
{
  "a":true,"b":false
}
```
  
## __オブジェクト__  
オブジェクト中にオブジェクトを入れることもできます。これを「ネストする」と言います。ここまでくるとデータ構造っぽさが出ます。  
```
{
   "id":1,`  
   "name":"tanaka",
   "attribute":{  
     "gender":"male",  
     "phone_number":"XXXXXXXXXXXX",
     "birth":"1991/01/01"
     } 
}
```  
## __配列__  
オブジェクトの場合は{}を使いましたが、配列を使いたい時は[]を使います。  
配列ないの要素はカンマで区切ることが複数入力できます。  
```
{
  "id":1,
  "name":"tanaka",
  "result":[
    87,
    83,
    71,
    59,
    91
  ]
}  
```
以上  
