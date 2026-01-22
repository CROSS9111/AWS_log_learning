以下はLambdaの監査イベント一覧となる

---

- 参考ドキュメント：
  - [Lambda 管理イベント](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/logging-using-cloudtrail.html)

---

## Amazon Lambda 管理イベント（コントロールプレーン）

デフォルトで、以下の API アクションはイベントとして CloudTrail ファイルに記録されます。

### 関数管理

| アクション                  | イベント名                            | 説明                                                                 |
| --------------------------- | ------------------------------------- | -------------------------------------------------------------------- |
| CreateFunction              | CreateFunction20150331                | Lambda関数を作成する（※Environment/ZipFileパラメータはログから省略） |
| DeleteFunction              | DeleteFunction20150331                | Lambda関数を削除する                                                 |
| GetFunction                 | GetFunction                           | 関数の設定情報とコードの場所を取得する                               |
| GetFunctionConfiguration    | GetFunctionConfiguration              | 関数の設定情報を取得する                                             |
| ListFunctions               | ListFunctions                         | アカウント内の関数一覧を取得する                                     |
| UpdateFunctionCode          | UpdateFunctionCode20150331v2          | 関数のコードを更新する（※ZipFileパラメータはログから省略）           |
| UpdateFunctionConfiguration | UpdateFunctionConfiguration20150331v2 | 関数の設定を更新する（※Environmentパラメータはログから省略）         |
| PublishVersion              | PublishVersion20150331                | 関数の新しいバージョンを発行する                                     |

### エイリアス

| アクション  | イベント名          | 説明                           |
| ----------- | ------------------- | ------------------------------ |
| CreateAlias | CreateAlias20150331 | 関数のエイリアスを作成する     |
| DeleteAlias | DeleteAlias20150331 | 関数のエイリアスを削除する     |
| GetAlias    | GetAlias20150331    | エイリアスの詳細情報を取得する |
| UpdateAlias | UpdateAlias20150331 | エイリアスの設定を更新する     |

### イベントソースマッピング

| アクション               | イベント名                       | 説明                                                                   |
| ------------------------ | -------------------------------- | ---------------------------------------------------------------------- |
| CreateEventSourceMapping | CreateEventSourceMapping20150331 | イベントソースマッピングを作成する（SQS、Kinesis、DynamoDB Streams等） |
| DeleteEventSourceMapping | DeleteEventSourceMapping20150331 | イベントソースマッピングを削除する                                     |
| GetEventSourceMapping    | GetEventSourceMapping            | イベントソースマッピングの詳細を取得する                               |
| UpdateEventSourceMapping | UpdateEventSourceMapping20150331 | イベントソースマッピングの設定を更新する                               |
| ListEventSourceMappings  | ListEventSourceMappings          | イベントソースマッピング一覧を取得する                                 |

### 権限（リソースベースポリシー）

| アクション       | イベント名                 | 説明                                           |
| ---------------- | -------------------------- | ---------------------------------------------- |
| AddPermission    | AddPermission20150331v2    | 関数のリソースベースポリシーに権限を追加する   |
| RemovePermission | RemovePermission20150331v2 | 関数のリソースベースポリシーから権限を削除する |
| GetPolicy        | GetPolicy                  | 関数のリソースベースポリシーを取得する         |

### レイヤー

| アクション                | イベント名                  | 説明                                                                     |
| ------------------------- | --------------------------- | ------------------------------------------------------------------------ |
| PublishLayerVersion       | PublishLayerVersion20181031 | レイヤーの新しいバージョンを発行する（※ZipFileパラメータはログから省略） |
| AddLayerVersionPermission | AddLayerVersionPermission   | レイヤーバージョンに権限を追加する                                       |
| GetLayerVersionPolicy     | GetLayerVersionPolicy       | レイヤーバージョンのポリシーを取得する                                   |

### 同時実行

| アクション                         | イベント名                         | 説明                                         |
| ---------------------------------- | ---------------------------------- | -------------------------------------------- |
| PutFunctionConcurrency             | PutFunctionConcurrency20171031     | 関数の予約済み同時実行数を設定する           |
| DeleteFunctionConcurrency          | DeleteFunctionConcurrency20171031  | 関数の予約済み同時実行設定を削除する         |
| PutProvisionedConcurrencyConfig    | PutProvisionedConcurrencyConfig    | プロビジョニングされた同時実行を設定する     |
| DeleteProvisionedConcurrencyConfig | DeleteProvisionedConcurrencyConfig | プロビジョニングされた同時実行設定を削除する |

### 関数URL

| アクション              | イベント名              | 説明                    |
| ----------------------- | ----------------------- | ----------------------- |
| CreateFunctionUrlConfig | CreateFunctionUrlConfig | 関数URLを作成する       |
| DeleteFunctionUrlConfig | DeleteFunctionUrlConfig | 関数URLを削除する       |
| GetFunctionUrlConfig    | GetFunctionUrlConfig    | 関数URLの設定を取得する |
| ListFunctionUrlConfigs  | ListFunctionUrlConfigs  | 関数URL一覧を取得する   |
| UpdateFunctionUrlConfig | UpdateFunctionUrlConfig | 関数URLの設定を更新する |

### コード署名

| アクション                   | イベント名                   | 説明                             |
| ---------------------------- | ---------------------------- | -------------------------------- |
| PutFunctionCodeSigningConfig | PutFunctionCodeSigningConfig | 関数にコード署名設定を関連付ける |
| UpdateCodeSigningConfig      | UpdateCodeSigningConfig      | コード署名設定を更新する         |
| DeleteCodeSigningConfig      | DeleteCodeSigningConfig      | コード署名設定を削除する         |

### 非同期呼び出し設定

| アクション                      | イベント名                      | 説明                                                 |
| ------------------------------- | ------------------------------- | ---------------------------------------------------- |
| PutFunctionEventInvokeConfig    | PutFunctionEventInvokeConfig    | 非同期呼び出しの設定（リトライ、送信先等）を設定する |
| UpdateFunctionEventInvokeConfig | UpdateFunctionEventInvokeConfig | 非同期呼び出しの設定を更新する                       |

### ランタイム管理

| アクション                 | イベント名                 | 説明                                        |
| -------------------------- | -------------------------- | ------------------------------------------- |
| PutRuntimeManagementConfig | PutRuntimeManagementConfig | ランタイム更新モード（自動/手動）を設定する |

### タグ管理

| アクション    | イベント名              | 説明                   |
| ------------- | ----------------------- | ---------------------- |
| TagResource   | TagResource20170331v2   | 関数にタグを追加する   |
| UntagResource | UntagResource20170331v2 | 関数からタグを削除する |

## Amazon Lambda Cloud watch

### メトリックス
