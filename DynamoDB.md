以下はDynamoDBの監査イベント一覧となる

---

- 参考ドキュメント：
  - [DynamoDB 管理イベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html)
  - [DynamoDB データイベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html)

---

## Amazon DynamoDB 管理イベント（コントロールプレーン）

デフォルトで、以下の API アクションはイベントとして CloudTrail ファイルに記録されます。

### テーブル管理

| アクション    | 説明                                            |
| ------------- | ----------------------------------------------- |
| CreateTable   | テーブルを作成する                              |
| DeleteTable   | テーブルを削除する                              |
| DescribeTable | テーブルの詳細情報を取得する                    |
| UpdateTable   | テーブルの設定（スループット、GSI等）を更新する |
| ListTables    | アカウント内のテーブル一覧を取得する            |

### バックアップ・復元

| アクション                | 説明                                                   |
| ------------------------- | ------------------------------------------------------ |
| CreateBackup              | テーブルのオンデマンドバックアップを作成する           |
| DeleteBackup              | バックアップを削除する                                 |
| DescribeBackup            | バックアップの詳細情報を取得する                       |
| ListBackups               | バックアップ一覧を取得する                             |
| RestoreTableFromBackup    | バックアップからテーブルを復元する                     |
| DescribeContinuousBackups | ポイントインタイムリカバリ（PITR）の設定を取得する     |
| RestoreTableToPointInTime | ポイントインタイムリカバリを使用してテーブルを復元する |

### グローバルテーブル

| アクション          | 説明                                           |
| ------------------- | ---------------------------------------------- |
| CreateGlobalTable   | グローバルテーブルを作成する                   |
| DescribeGlobalTable | グローバルテーブルの詳細情報を取得する         |
| ListGlobalTables    | グローバルテーブル一覧を取得する               |
| UpdateGlobalTable   | グローバルテーブルにリージョンを追加・削除する |

### TTL（Time To Live）

| アクション         | 説明                                  |
| ------------------ | ------------------------------------- |
| DescribeTimeToLive | テーブルのTTL設定を取得する           |
| UpdateTimeToLive   | テーブルのTTL設定を有効化・無効化する |

### タグ管理

| アクション         | 説明                                   |
| ------------------ | -------------------------------------- |
| TagResource        | リソースにタグを追加する               |
| UntagResource      | リソースからタグを削除する             |
| ListTagsOfResource | リソースに付与されたタグ一覧を取得する |

### キャパシティ・制限

| アクション                        | 説明                                                       |
| --------------------------------- | ---------------------------------------------------------- |
| DescribeLimits                    | アカウントのテーブル・スループット制限を取得する           |
| DescribeReservedCapacity          | 購入済みのリザーブドキャパシティを取得する                 |
| DescribeReservedCapacityOfferings | 利用可能なリザーブドキャパシティの購入オプションを取得する |
| PurchaseReservedCapacityOfferings | リザーブドキャパシティを購入する                           |

### Auto Scaling

| アクション              | 説明                                           |
| ----------------------- | ---------------------------------------------- |
| DescribeScalableTargets | スケーラブルターゲットの設定を取得する         |
| RegisterScalableTarget  | Auto Scalingのスケーラブルターゲットを登録する |
