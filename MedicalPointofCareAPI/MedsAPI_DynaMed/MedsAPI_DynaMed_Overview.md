# MedsAPI DynaMed Overview

<!-- vscode-markdown-toc -->
## 目次
1. [イントロダクション](#introduction)
2. [クライアントアプリケーションの登録](#register)
3. [クライアント認証情報グラントタイプを利用する](#granttype)


##  1. <a id='introduction'>イントロダクション</a>
DynaMedは、医療の現場で最も有用な情報を医療従事者に提供することで、世界の健康状態を改善することを使命としています。 DynaMedは、実践的な臨床医に向けて、最新かつ正確な、エビデンスに基づくコンテンツをお届けします。 私たちの学際的なチームは、新しい科学文献や臨床診療ガイドラインを体系的かつ客観的に調査しています。 関連する情報は、迅速に収集、評価され、DynaMedの臨床コンテンツに統合されます。 サイトでは、1日に6回の更新が行われます。 DynaMedは、実用的なレコメンデーション、キーテイクアウェイ、シノプシス（要約）を表面化します。 また、ユーザーは、基礎となる知識体系や研究の詳細を深く掘り下げることができます。 DynaMedは、論文、論文の一部、画像を返すことができる使いやすい検索エンドポイントをユーザーに提供します。 また、検索結果には完全なHTMLコンテンツが含まれるため、ユーザー・インターフェースに簡単に表示することができます。

DynaMedは、アプリケーションの認証にOAuth 2.0を使用しています。 したがって、アプリケーションはOAuth 2.0を使用してリクエストを承認する必要があります。 DynaMedへのすべてのリクエストは、OAuth 2.0プロセスによって決定されるアクセストークンを含んでいなければなりません。 アクセストークンは、あなたのアプリケーションをEBSCOに識別させるという点で、API Keyに似ています。 OAuth 2.0 の背景については、Getting Started または OAuth 2.0 仕様を参照してください。

このセクションでは、DynaMedのコア・コンセプトについて簡単に説明します。 RESTful APIを使ったことがある方なら、ここで説明するコンセプトの多くは馴染みがあることでしょう。

##  2. <a id='register'>クライアントアプリケーションの登録</a>
OAuth 2.0の処理を開始し、アクセストークンを受け取る前に、APIにアプリを登録する必要があります。 これは、認可サーバーに以下の情報を提供するために必要です。

* アプリの名前。
* 必要に応じて、リダイレクトまたはコールバックURL。 リダイレクトURLやコールバックURLは、ユーザーがデータアクセスを認可した後に、ユーザーをリダイレクトさせるためのものです。

アプリが登録されると、アプリにはClient IDとClient Secretが割り振られます。 Client IDは、クライアントアプリケーションをアプリケーションとして識別するために使用される、公開された一意の識別子です。 Client Secretは、AppとAPIの間で秘密にされるプライベートな識別子です。 Client Secretは、Appがアクセストークンのリクエストを行う際に、Appを認証するために使用されます。

### アプリを登録するには ###

1. EBSCO Developerにログインします。

2. トップナビゲーションにあるMy Appsをクリックします。
![myapps](https://developer.ebsco.com/sites/default/files/myappsv1.png)

3. ページ上部の「Add a new App」ボタンをクリックします。

<img src="https://developer.ebsco.com/sites/default/files/addapp.png" width="120">

フォームが表示されます。
![form](https://developer.ebsco.com/sites/default/files/addappwindowv6.png)

4. App Nameを入力します。
5. Type of App（アプリの種類）を選択します。 
6. AppがユーザーIDおよび/または詳細へのアクセスを必要とするかどうかを指定します。
7. Product（s）をクリックします。 Callback URL（コールバックURL）、Customer ID（カスタマーID）、Group ID（グループID）の各フィールドは任意です。
8. **Create App**（アプリの作成）ボタンをクリックします。 My Appsページに戻り、新規アプリが表示されます。 新しいアプリは、情報の確認と承認が完了するまで保留となります。 アプリが承認されると、電子メールが送信されます。
![pending](https://developer.ebsco.com/sites/default/files/pendingmedsapi.png)
9. App Approvalのメールが届いたら、EBSCO Developerにログインしてください。
10. **My Apps** ページに移動します。 新しいAppのステータスはApprovedと表示されます。
11. リスト内のアプリケーション名をクリックします。 Credentialsセクションが表示されます。 アプリケーションの認証情報であるClient IDとClient Secretが表示されます。
![approved](https://developer.ebsco.com/sites/default/files/approveddiscoveryapp.png)
12. アプリの**Client ID**と**Client Secret**を控えておきます。 Client IDとClient SecretはOAuth 2.0の処理で使用してください。

## <a id='granttype'>クライアント認証情報グラントタイプを利用する</a>

OAuth 2.0では、クライアントアプリケーションがリソース所有者のアカウントにアクセスするための、いくつかのグラント（メソッド）が記述されています。 グラントタイプはユースケースに依存します。 この例では、すべてのグラントタイプのうち最もシンプルなクライアント認証のグラントタイプを使用します。クライアント認証のグラントタイプは、ユーザーの代わりに API 呼び出しを行わない機密性の高いクライアントアプリケーションに使用します。 アクセストークンは、アプリケーション自身に対して発行されます。 クライアント認証情報グラントタイプは、 認証サーバを使用して自身のサービスアカウントへのアクセスを取得します。 クライアントアプリケーションは、クライアントアプリケーション認証情報 (クライアント ID およびクライアントシークレット) を使って、認可サーバーからアクセストークンを受け取ることができます。 このアクセストークンを使って、リソースサーバー上のサービスアカウントの API エンドポイントにアクセスすることができます。 クライアント認証情報付与型のプロセスを、プロセスにおける役割の観点から説明します。

* クライアントアプリケーション - 自身のサービスアカウントへのアクセスを取得しようとするサードパーティアプリケーションです。
* 認可サーバー - アクセストークンを発行する。 
* リソースサーバー - サービスアカウントリソースをホストする。

クライアント認証のグラントタイプは、アプリケーションが自分のアカウント用のアクセストークンを必要とする場合に使用します。 以下では、クライアント認証 OAuth 2.0 のグラントタイプの処理について説明します。

### 認可サーバーへのアクセストークン要求

OAuth 2.0 のクライアント認証情報付与タイプにおける最初のステップは、クライアントアプリケーションが認可サーバーにアクセストークンリクエストを行うことです。 アクセストークンリクエストは、認可サーバーにアクセストークンを要求するために使用されます。 認可サーバーへのアクセストークンリクエストは、以下のパラメータが必要です。

* client id - 登録時にアプリケーションに付与されたクライアントID。
* grant type - OAuth 2.0 のグラントタイプで、使用する処理フローを決定します。 クライアント認証のグラントタイプフローを使用する場合、この値はclient_credentials となります。
* client secret - 登録時にアプリケーションに与えられたクライアントシークレット。
* product - クライアントがアクセスを要求しているAPIのセット。

![accesstoken](https://developer.ebsco.com/sites/default/files/accesstokenrequestclientcreds.png)

### クライアントアプリケーションのアクセストークンリクエストのコードスニペット（Node.js）

```javascript


    const bodyjson = {
	grant_type: "client_credentials",
        product: "dynamed",
	client_id: "{your client id}", 
	client_secret: "{your client_secret}"
    };

    const access_token_options = {
        method: 'POST',
        url: 'https://apis.ebsco.com/medsapi-auth/v1/token',
        headers: {
           'Content-Type': 'application/json',
           'accept': 'application/json', 
        },
        body: JSON.stringify(bodyjson) 
    };


    // Requestを送信
    request(access_token_options, function (error, response, body) {
    if (error) throw new Error(error);
    
    // bodyのjsonレスポンスを処理
    });


```

### 認可サーバーがアクセストークンを返す

クライアントアプリケーションからアクセストークンのリクエストを受けると、認可サーバーはクライアントアプリケーションにアクセストークンを返信します。 クライアントアプリケーションは、その応答からアクセストークンを取り出すことができます。

![accesstoken](https://developer.ebsco.com/sites/default/files/accesstokenclientcreds.png)


### 認可サーバーのレスポンスからアクセストークンを抽出するクライアントアプリケーションのコードスニペット（Node.js）


```javascript

    request(access_token_options, function (error, response, body) {
       if (error) throw new Error(error);
       const body_json = JSON.parse(body);
       const access_token = body_json.access_token;
    
    });

```

### APIの利用

クライアントアプリケーションはアクセストークンを取得したことで、アプリケーションのサービスアカウントに対して自由にAPIリクエストを行うことができるようになりました。 クライアントアプリケーションからAPIへのリクエストは、すべてヘッダーにアクセストークンを記述する必要があります。

![useapi](https://developer.ebsco.com/sites/default/files/useapiclientcreds.png)

### クライアントアプリケーションのコードスニペット アクセストークンを使ってAPIにリクエストを送信する（Node.js）


```javascript

    // Form the Request
    let options = {
        method: 'GET',
        url: 'https://apis.ebsco.com/medsapi-dynamed/v1/search?query=heart',
        headers: {
           'Cache-Control': 'no-cache',
           Authorization: `Bearer ${access_token}` }
     };

     // Send the Request
     request(options, function (error, response, body) {
         if (error) throw new Error(error);
     
         // Now process the json response in the body
     });

```

そして、クライアントアプリケーションが要求したサービスアカウントリソースをAPIから受信します。

![resource](https://developer.ebsco.com/sites/default/files/ClientCredsGrant.png)

クライアント認証付与は、アプリケーションがユーザーの代理ではなく、自分自身のリソースにアクセスするためにアクセストークンを要求する必要がある場合に使用されます。 最終的には、アプリケーションが自身のサービスアカウントにアクセスするためのアクセストークンを取得することになります。
