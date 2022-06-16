## 認証

PublicationIQへのすべてのリクエストには、有効なPublication Finderカスタマー・プロファイルが含まれている必要があります。 プロファイルのパスワードは任意です。 パスワードが提供される場合、それはPublication Finder顧客プロファイルに割り当てられた有効なパスワードである必要があります。 パスワードが省略された場合、リクエストを行う環境でPublication Finder顧客プロファイルがゲストアクセスを許可している場合にのみ、リクエストは承認されます。 たとえば、サンドボックス環境でパスワードなしでPublicationIQにリクエストを行いたい場合、サンドボックス環境のPublication Finder顧客プロファイルでゲストアクセスを有効にする必要があります。 本番環境でも同様です。 PublicationIQのサンドボックス環境にアクセスするためには、EBSCOカスタマーサポートにお問い合わせください。

Publication Finderの顧客プロファイルは、pathパラメータとして指定するため、以下のように指定する必要があります。

profile {customerid.groupid.profileid}という形式の文字列で、固有の顧客プロファイルを指定します。


### サンドボックス環境

```HTTP
https://sandbox.ebsco.io/pf/pfaccount/{profile}/...
```

### 本番環境

```HTTP
https://api.ebsco.io/pf/pfaccount/{profile}/...
```

PublicationIQの認証に関する追加情報を請求して、お客様のシステムでPublicationIQのサブスクリプションをどのように利用できるかをさらに評価することができます。

[追加情報をリクエスト](https://www.ebsco.com/request-information)

PublicationIQのリクエストには、必ず有効なPublication Finderの顧客プロファイルを添付してください。