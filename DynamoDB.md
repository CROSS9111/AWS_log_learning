以下はDynamoDBの監査イベント一覧となる

---
- 参考ドキュメント：
  - [DynamoDB 管理イベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html)
  - [DynamoDB データイベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html)
  - [DynamoDB API リファレンス](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Operations.html)
  - [DynamoDB Streams API リファレンス](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Operations_Amazon_DynamoDB_Streams.html)
  - [DAX API リファレンス](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_Operations_Amazon_DynamoDB_Accelerator_(DAX).html)

---

## Amazon DynamoDB テーブル管理アクション

| アクション | 説明 |
|-----------|------|
| CreateTable | テーブルを作成する |
| DeleteTable | テーブルを削除する |
| DescribeTable | テーブルの詳細情報を取得する |
| ListTables | アカウント内のテーブル一覧を取得する |
| UpdateTable | テーブルの設定を更新する |
| DescribeTableReplicaAutoScaling | グローバルテーブルのレプリカのAuto Scaling設定を取得する |
| UpdateTableReplicaAutoScaling | グローバルテーブルのレプリカのAuto Scaling設定を更新する |
| DescribeKinesisStreamingDestination | Kinesis Data Streamsへのストリーミング設定を取得する |
| EnableKinesisStreamingDestination | Kinesis Data Streamsへのストリーミングを有効化する |
| DisableKinesisStreamingDestination | Kinesis Data Streamsへのストリーミングを無効化する |
| DescribeTimeToLive | TTL設定を取得する |
| UpdateTimeToLive | TTL設定を更新する |

## Amazon DynamoDB アイテム操作アクション

| アクション | 説明 |
|-----------|------|
| BatchGetItem | 複数のアイテムを一括取得する |
| BatchWriteItem | 複数のアイテムを一括書き込み・削除する |
| DeleteItem | アイテムを削除する |
| GetItem | アイテムを取得する |
| PutItem | アイテムを作成または置換する |
| Query | パーティションキーを指定してアイテムをクエリする |
| Scan | テーブル全体をスキャンする |
| UpdateItem | アイテムの属性を更新する |
| TransactGetItems | トランザクションで複数のアイテムを取得する |
| TransactWriteItems | トランザクションで複数のアイテムを書き込む |

## Amazon DynamoDB インデックス管理アクション

| アクション | 説明 |
|-----------|------|
| DescribeGlobalTableSettings | グローバルテーブルの設定を取得する |
| UpdateGlobalTableSettings | グローバルテーブルの設定を更新する |

## Amazon DynamoDB バックアップ・復元アクション

| アクション | 説明 |
|-----------|------|
| CreateBackup | オンデマンドバックアップを作成する |
| DeleteBackup | バックアップを削除する |
| DescribeBackup | バックアップの詳細を取得する |
| ListBackups | バックアップ一覧を取得する |
| RestoreTableFromBackup | バックアップからテーブルを復元する |
| RestoreTableToPointInTime | ポイントインタイムリカバリでテーブルを復元する |
| DescribeContinuousBackups | 継続的バックアップ設定を取得する |
| UpdateContinuousBackups | 継続的バックアップ設定を更新する |

## Amazon DynamoDB Global Tables アクション

| アクション | 説明 |
|-----------|------|
| CreateGlobalTable | グローバルテーブルを作成する |
| DescribeGlobalTable | グローバルテーブルの詳細を取得する |
| ListGlobalTables | グローバルテーブル一覧を取得する |
| UpdateGlobalTable | グローバルテーブルにレプリカを追加・削除する |

## Amazon DynamoDB エクスポート・インポートアクション

| アクション | 説明 |
|-----------|------|
| ExportTableToPointInTime | テーブルをS3にエクスポートする |
| DescribeExport | エクスポートの詳細を取得する |
| ListExports | エクスポート一覧を取得する |
| ImportTable | S3からテーブルをインポートする |
| DescribeImport | インポートの詳細を取得する |
| ListImports | インポート一覧を取得する |

## Amazon DynamoDB タグ管理アクション

| アクション | 説明 |
|-----------|------|
| TagResource | リソースにタグを付ける |
| UntagResource | リソースからタグを削除する |
| ListTagsOfResource | リソースのタグ一覧を取得する |

## Amazon DynamoDB リソースポリシーアクション

| アクション | 説明 |
|-----------|------|
| GetResourcePolicy | リソースベースポリシーを取得する |
| PutResourcePolicy | リソースベースポリシーを設定する |
| DeleteResourcePolicy | リソースベースポリシーを削除する |

## Amazon DynamoDB その他のアクション

| アクション | 説明 |
|-----------|------|
| DescribeLimits | アカウントのキャパシティ制限を取得する |
| DescribeEndpoints | リージョナルエンドポイント情報を取得する |
| ListContributorInsights | Contributor Insights設定一覧を取得する |
| DescribeContributorInsights | Contributor Insights設定の詳細を取得する |
| UpdateContributorInsights | Contributor Insights設定を更新する |

## Amazon DynamoDB Streams アクション

| アクション | 説明 |
|-----------|------|
| DescribeStream | ストリームの詳細を取得する |
| GetRecords | ストリームからレコードを取得する |
| GetShardIterator | シャードイテレータを取得する |
| ListStreams | ストリーム一覧を取得する |

## Amazon DynamoDB Accelerator (DAX) アクション

| アクション | 説明 |
|-----------|------|
| CreateCluster | DAXクラスターを作成する |
| CreateParameterGroup | パラメータグループを作成する |
| CreateSubnetGroup | サブネットグループを作成する |
| DecreaseReplicationFactor | クラスターのノード数を減らす |
| DeleteCluster | DAXクラスターを削除する |
| DeleteParameterGroup | パラメータグループを削除する |
| DeleteSubnetGroup | サブネットグループを削除する |
| DescribeClusters | クラスターの詳細を取得する |
| DescribeDefaultParameters | デフォルトパラメータを取得する |
| DescribeEvents | イベント一覧を取得する |
| DescribeParameterGroups | パラメータグループ一覧を取得する |
| DescribeParameters | パラメータの詳細を取得する |
| DescribeSubnetGroups | サブネットグループ一覧を取得する |
| IncreaseReplicationFactor | クラスターのノード数を増やす |
| ListTags | リソースのタグ一覧を取得する |
| RebootNode | ノードを再起動する |
| TagResource | リソースにタグを付ける |
| UntagResource | リソースからタグを削除する |
| UpdateCluster | クラスターの設定を更新する |
| UpdateParameterGroup | パラメータグループを更新する |
| UpdateSubnetGroup | サブネットグループを更新する |

## PartiQL アクション

| アクション | 説明 |
|-----------|------|
| ExecuteStatement | 単一のPartiQLステートメントを実行する |
| BatchExecuteStatement | 複数のPartiQLステートメントを一括実行する |
| ExecuteTransaction | トランザクションでPartiQLステートメントを実行する |
