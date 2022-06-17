## 環境

サンドボックス環境と本番環境に対応しています。 サンドボックス環境では、お客様のAPIクライアントコードをテストすることができます。 PublicationIQの場合、サンドボックス環境にアクセスするためには、Publication Finderの顧客プロファイルが必要です。 サンドボックスは、安全な環境でさまざまなAPI機能をテストするために使用できます。 テストや開発は、すべてサンドボックス環境で行ってください。

ご注意：PublicationIQへのアクセスには、Publication Finderのカスタマープロファイルが必要です。 プロファイルのパスワードは任意です。 パスワードが提供される場合、それはPublication Finder顧客プロファイルに割り当てられた有効なパスワードである必要があります。 パスワードが省略された場合、リクエストを行う環境でPublication Finderカスタマー・プロファイルがゲスト・アクセスを許可している場合にのみ、リクエストは承認されます。 たとえば、サンドボックス環境でパスワードなしでPublicationIQにリクエストを行いたい場合、サンドボックス環境のPublication Finder顧客プロファイルでゲストアクセスを有効にする必要があります。 本番環境でも同様です。 PublicationIQのサンドボックス環境にアクセスするためには、EBSCOカスタマーサポートにお問い合わせください。


### サンドボックス環境に対するPublicationIQのリクエスト

```HTTP
https://sandbox.ebsco.io/pf/pfaccount
```

### 本番環境に対するPublicationIQのリクエスト
```HTTP
https://api.ebsco.io/pf/pfaccount
```