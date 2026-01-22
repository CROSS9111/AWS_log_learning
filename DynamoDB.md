# DynamoDB

**対象：NoSQLデータベース、アプリケーションデータストア**

---

# 【現行調査】

## コンポーネント側

## Amazon DynamoDB 管理イベント（コントロールプレーン） | デフォルトで取得

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

## CloudWatch メトリクス | デフォルトで取得

### スループットメトリクス

テーブルとグローバルセカンダリインデックスの読み取り/書き込みキャパシティに関するメトリクスです。

| メトリクス名                     | 説明                                       |
| -------------------------------- | ------------------------------------------ |
| `ConsumedReadCapacityUnits`      | 指定期間に消費された読み取りキャパシティ   |
| `ConsumedWriteCapacityUnits`     | 指定期間に消費された書き込みキャパシティ   |
| `ProvisionedReadCapacityUnits`   | テーブルにプロビジョニングされた読み取り量 |
| `ProvisionedWriteCapacityUnits`  | テーブルにプロビジョニングされた書き込み量 |
| `ReadThrottleEvents`             | プロビジョニングを超えた読み取りリクエスト |
| `WriteThrottleEvents`            | プロビジョニングを超えた書き込みリクエスト |
| `ThrottledRequests`              | スロットリングされたリクエストの総数       |
| `AccountProvisionedReadCapacity` | アカウント全体の読み取りキャパシティ       |
| `AccountProvisionedWriteCapacity` | アカウント全体の書き込みキャパシティ       |

### レイテンシメトリクス

DynamoDBオペレーションの応答時間に関するメトリクスです。

| メトリクス名                    | 説明                                        |
| ------------------------------- | ------------------------------------------- |
| `SuccessfulRequestLatency`      | 成功したリクエストの経過時間（ミリ秒）      |
| `GetItem`（レイテンシ）         | GetItem操作のレイテンシ                     |
| `PutItem`（レイテンシ）         | PutItem操作のレイテンシ                     |
| `Query`（レイテンシ）           | Query操作のレイテンシ                       |
| `Scan`（レイテンシ）            | Scan操作のレイテンシ                        |
| `BatchGetItem`（レイテンシ）    | BatchGetItem操作のレイテンシ                |
| `BatchWriteItem`（レイテンシ）  | BatchWriteItem操作のレイテンシ              |
| `TransactWriteItems`（レイテンシ） | TransactWriteItems操作のレイテンシ          |
| `TransactGetItems`（レイテンシ）   | TransactGetItems操作のレイテンシ            |

### エラーメトリクス

リクエストの成功・失敗に関するメトリクスです。

| メトリクス名                        | 説明                                                                 |
| ----------------------------------- | -------------------------------------------------------------------- |
| `SystemErrors`                      | HTTPステータスコード500のシステムエラー数                            |
| `UserErrors`                        | HTTPステータスコード400のユーザーエラー数                            |
| `ConditionalCheckFailedRequests`    | 条件チェック失敗によるリクエスト数（楽観的ロック競合等）             |
| `TransactionConflict`               | トランザクション操作で発生した競合数                                 |
| `TimeToLiveDeletedItemCount`        | TTLにより削除されたアイテム数                                        |

### ストリームメトリクス（DynamoDB Streams）

DynamoDB Streamsに関するメトリクスです。

| メトリクス名                           | 説明                                            |
| -------------------------------------- | ----------------------------------------------- |
| `ReturnedRecordsCount`                 | ストリームから取得されたレコード数              |
| `ReturnedBytes`                        | ストリームから返されたバイト数                  |

---

# 【追加分】

**アイテムレベルの操作（GetItem、PutItem、DeleteItem等）による不正なデータアクセス・改ざんを防ぐため、DynamoDBデータイベントをCloudTrailで取得すべきと考える。また証跡（いつ誰がどのテーブルのどのアイテムを操作したか）を残すことができる。**

## 1. DynamoDBデータイベント（CloudTrail） | 追加有効化が必要

デフォルトでは無効。アイテムレベルの操作を監視するには明示的な有効化が必要。

### データプレーン操作

| アクション          | 説明                                       |
| ------------------- | ------------------------------------------ |
| GetItem             | 単一アイテムの読み取り                     |
| PutItem             | 単一アイテムの書き込み（新規作成/上書き）  |
| UpdateItem          | 既存アイテムの属性を更新                   |
| DeleteItem          | 単一アイテムの削除                         |
| BatchGetItem        | 複数アイテムの一括読み取り                 |
| BatchWriteItem      | 複数アイテムの一括書き込み・削除           |
| Query               | パーティションキーによるクエリ             |
| Scan                | テーブル全体のスキャン                     |
| TransactGetItems    | トランザクション内での複数アイテム読み取り |
| TransactWriteItems  | トランザクション内での複数アイテム書き込み |

### 監査証跡で記録される情報

| 項目               | 内容                                                                 |
| ------------------ | -------------------------------------------------------------------- |
| 操作日時           | UTC形式のタイムスタンプ                                              |
| 操作ユーザー       | IAMユーザー、ロール、Cognitoアイデンティティ                         |
| 操作内容           | GetItem、PutItem、DeleteItem等のAPI操作                              |
| 操作対象           | テーブル名、パーティションキー、ソートキー（※機微情報はマスク推奨） |
| 操作元             | SourceIPAddress、User-Agent                                          |
| 結果               | 成功/失敗、エラーコード                                              |
| リクエストパラメータ | アイテムキー、条件式等（※PII/機微情報の暗号化/マスキング必須）       |

## 2. ポイントインタイムリカバリ（PITR） | 追加有効化が必要

データ改ざんや誤削除からの復旧のため、ポイントインタイムリカバリの有効化を推奨。

| 機能                 | 内容                                                       |
| -------------------- | ---------------------------------------------------------- |
| バックアップ期間     | 過去35日間の任意の時点に復元可能                           |
| 復元粒度             | 秒単位                                                     |
| 追加コスト           | テーブルサイズに応じた継続的バックアップストレージ料金     |
| カバーするリスク     | データ改ざん（Ⅳ/Ⅴ）、誤削除、証跡改ざん対策（Ⅴ）         |

## 3. 保存時暗号化（KMS） | 追加設定が必要

機密情報の平文保存を防ぐため、KMSカスタマーマネージドキーによる暗号化を推奨。

| 設定項目           | 推奨内容                                                       |
| ------------------ | -------------------------------------------------------------- |
| 暗号化キー         | KMSカスタマーマネージドキー（AWS所有キーではなく）            |
| キーローテーション | 有効化（年次自動ローテーション）                               |
| キー操作ログ       | CloudTrailでDecrypt、Encrypt、GenerateDataKey等を記録          |
| カバーするリスク   | 機密情報の平文保存（Ⅳ）、シークレット漏洩（Ⅳ）               |

## 4. CloudWatch Alarms + 異常検知 | 追加設定が必要

定常外のアクセスや異常操作を検知するため、CloudWatch Alarmsの設定を推奨。

### 推奨アラーム設定

| アラーム対象                          | 閾値例                                     | 通知先               | カバーするリスク               |
| ------------------------------------- | ------------------------------------------ | -------------------- | ------------------------------ |
| `ThrottledRequests`                   | > 10回/5分                                 | Slack通知            | 不正操作検知遅延（Ⅴ）         |
| `UserErrors`                          | > 100回/5分                                | Slack通知            | 異常アクセス検知（Ⅴ）         |
| `SystemErrors`                        | > 0回/5分                                  | Slack通知            | システム障害検知               |
| `ConditionalCheckFailedRequests`      | > 閾値（設計次第）                         | Slack通知（任意）    | 楽観的ロック競合・異常更新試行 |
| `ConsumedReadCapacityUnits`（急増）   | 通常時の3倍以上/5分                        | Slack通知            | データ大量持ち出しの兆候（Ⅳ） |
| `Scan`操作の頻発                      | 設計上不要な場合は検知                     | Slack通知            | 全件取得による情報漏洩（Ⅳ）   |
| データイベント：連続DeleteItem        | 短時間で大量削除                           | Slack通知            | データ削除攻撃（Ⅴ）           |

---

**論点：Lambda/ECS実装で対応すべき事項**

1. **構造化ログの出力** - 監査証跡要件（260123.md）に準拠した形式
2. **リクエスト/レスポンスのロギング** - 操作内容、対象テーブル、キー情報、ステータスコード、処理時間
3. **機微情報のマスキング/暗号化** - アイテムの属性値やキー情報に個人情報が含まれる場合はマスキング/暗号化
4. **定常外アクセス・エラー・失敗時のログ出力** - 異常検知・通知のトリガーとして活用
5. **認可ロジックの実装** - BOLA/IDOR対策として、リソース単位の認可検証を実施
6. **DynamoDB Streams活用** - Before/After値の記録が必要な場合、Streamsを利用してCloudWatch Logsに保存

---

- 参考ドキュメント：
  - [DynamoDB 管理イベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html)
  - [DynamoDB データイベント](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/logging-using-cloudtrail.html#cloudtrail-data-events)
  - [DynamoDB メトリクス](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/metrics-dimensions.html)
  - [ポイントインタイムリカバリ](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/PointInTimeRecovery.html)
  - [DynamoDB 暗号化](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/encryption.howitworks.html)

---

## 比較表

監査の要件ができれば管理イベントだけでもOKだが、アイテムレベルの詳細な追跡にはデータイベントが必須。

| 項目                   | 管理イベント（CloudTrail）        | データイベント（CloudTrail）              |
| ---------------------- | --------------------------------- | ----------------------------------------- |
| **目的**               | テーブル操作の監査                | アイテム操作の監査・セキュリティ監視      |
| **取得範囲**           | CreateTable、UpdateTable等        | GetItem、PutItem、DeleteItem等            |
| **デフォルト取得**     | ✅ 有効                            | ❌ 無効（明示的な有効化が必要）            |
| **料金**               | 無料（最初のコピーは無料）        | 有料（イベント数課金）                    |
| **ログ詳細度**         | テーブル設定変更                  | アイテムキー・属性値（マスキング可）      |
| **監査証跡の完全性**   | テーブルレベルの変更追跡          | データレベルの変更追跡                    |
| **統合性**             | CloudWatch、Athena、他AWSサービス | CloudWatch、Athena、他AWSサービス         |
| **カバーするリスク**   | 内部不正（Ⅴ）、設定変更追跡       | データ改ざん/不正取得（Ⅳ/Ⅴ）、BOLA/IDOR（Ⅰ） |

## 使い分け

**管理イベントのみで十分なケース**

- テーブル作成・削除等のインフラ操作の追跡のみが目的
- コスト最適化を優先
- データ操作の詳細な監査は不要

**データイベント有効化が必須なケース**

- セキュリティ監査・コンプライアンス要件
- 「誰がいつどのアイテムを操作したか」の完全な証跡が必要
- データ改ざん・不正取得のリスクが高い
- BOLA/IDOR対策として操作ログが必要

## 結論

**260123.mdの要件（データ改ざん/不正取得の追跡、内部不正対策）を満たすには、DynamoDBデータイベントの有効化が必須**です。管理イベントだけではアイテムレベルの操作が追跡できないため、監査証跡として不十分です。
