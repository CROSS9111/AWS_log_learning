# Lambda

**対象：tavily検索,pdf解析,bedrock agent作動**

---

---

# 【現行調査】

## コンポーネント側

## Amazon Lambda 管理イベント（コントロールプレーン）

**デフォルトで取得**

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

---

## CloudWatch メトリクス

**デフォルトで取得**

### 呼び出しメトリクス

Lambda の関数呼び出しの結果に関するカウント系指標です。

| メトリクス名                                 | 説明                                            |
| -------------------------------------------- | ----------------------------------------------- |
| `Invocations`                                | 関数が呼び出された回数（成功＋失敗含む）        |
| `Errors`                                     | 関数エラーが発生した呼び出し数                  |
| `DeadLetterErrors`                           | 非同期で送られたイベントが DLQ へ送れなかった数 |
| `DestinationDeliveryFailures`                | 非同期送信先への配信失敗数                      |
| `Throttles`                                  | スロットリングによって拒否された呼び出し数      |
| `OversizedRecordCount`                       | DocumentDB イベントで 6MB 超のイベント数        |
| `ProvisionedConcurrencyInvocations`          | プロビジョニングされた同時実行での呼び出し数    |
| `ProvisionedConcurrencySpilloverInvocations` | 標準同時実行にフォールバックした数              |
| `RecursiveInvocationsDropped`                | 無限再帰検出によってドロップされた呼び出し数    |

### デプロイメトリクス

Lambda 関数のデプロイ検証に関する指標です。

| メトリクス名                | 説明                                 |
| --------------------------- | ------------------------------------ |
| `SignatureValidationErrors` | コード署名検証に失敗したデプロイの数 |

### パフォーマンスメトリクス

関数実行のパフォーマンス情報を表します。

| メトリクス名                    | 説明                                       |
| ------------------------------- | ------------------------------------------ |
| `Duration`                      | 関数の実行時間（ミリ秒）                   |
| `PostRuntimeExtensionsDuration` | 拡張機能の追加処理時間                     |
| `IteratorAge`                   | ストリームイベントの最終レコードの経過時間 |
| `OffsetLag`                     | Kafka のオフセットラグ                     |

### 同時実行メトリクス

同時実行数や利用率に関する指標です。

| メトリクス名                        | 説明                                     |
| ----------------------------------- | ---------------------------------------- |
| `ConcurrentExecutions`              | 同時実行中の関数インスタンス数           |
| `ProvisionedConcurrentExecutions`   | プロビジョニング同時実行数               |
| `ProvisionedConcurrencyUtilization` | プロビジョニング同時実行の使用率         |
| `UnreservedConcurrentExecutions`    | 予約なし同時実行数                       |
| `ClaimedAccountConcurrency`         | アカウントで既に割り当てられた同時実行数 |

### 非同期呼び出しメトリクス

非同期イベントのキュー関連の指標です。

| メトリクス名          | 説明                                   |
| --------------------- | -------------------------------------- |
| `AsyncEventsReceived` | 非同期イベントを正常にキューに入れた数 |
| `AsyncEventAge`       | キュー投入から実行までの時間           |
| `AsyncEventsDropped`  | 処理されずにドロップされたイベント数   |

### イベントソースマッピングメトリクス

ストリーム系イベントソース（SQS / DynamoDB / Kinesis / MSK 等）に関する指標です。

| メトリクス名                              | 説明                                       |
| ----------------------------------------- | ------------------------------------------ |
| `PolledEventCount`                        | ポーリングしたイベント数                   |
| `FilteredOutEventCount`                   | フィルタ除外イベント数                     |
| `InvokedEventCount`                       | マッピングから関数を呼び出したイベント数   |
| `FailedInvokeEventCount`                  | 呼び出しに失敗したイベント数               |
| `DroppedEventCount`                       | ドロップされたイベント数                   |
| `OnFailureDestinationDeliveredEventCount` | 失敗送信先へ正常送信されたイベント数       |
| `DeletedEventCount`                       | 正常に削除されたイベント数                 |
| `ProvisionedPollers`                      | プロビジョニングモードで稼働中のポーラー数 |

## CloudWatch Logs

**デフォルト**

## Lambda システムログ／プラットフォームログ

| 項目         | 内容                                                                |
| ------------ | ------------------------------------------------------------------- |
| 出力主体     | AWS Lambda 実行基盤（マネージドコンポーネント）                     |
| ログ保存先   | CloudWatch Logs（/aws/lambda/関数名）                               |
| 主な内容     | 実行開始・終了、実行時間、課金対象時間、メモリ使用量、基盤エラー    |
| 代表的なログ | START / END / REPORT<br>Task timed out<br>Runtime exited with error |
| 制御可否     | 不可（出力抑制・内容変更不可）                                      |
| 主な用途     | 実行証跡確認、性能分析、コスト分析、基盤障害検知                    |

## Lambda アプリ未処理例外・クラッシュログ）

| 項目         | 内容                                                  |
| ------------ | ----------------------------------------------------- |
| 出力主体     | アプリケーション（結果として）                        |
| ログ保存先   | CloudWatch Logs                                       |
| 主な内容     | 未処理例外、スタックトレース、ランタイム例外          |
| 代表的なログ | Traceback<br>ZeroDivisionError<br>Unhandled exception |
| 制御可否     | 一部可（try/except などで抑制・変換可能）             |
| 主な用途     | 障害調査、バグ検知、異常系把握                        |

**デフォルト外**

## Lambda　アプリログ

| 項目         | 内容                                                      |
| ------------ | --------------------------------------------------------- |
| 出力主体     | アプリケーション                                          |
| 出力方法     | 明示的に実装（print / logger 等）                         |
| 主な内容     | 業務処理ログ、操作ログ、監査ログ、状態遷移                |
| 代表的なログ | print / console.log<br>logging / logger<br>JSON構造化ログ |
| 制御可否     | 可（出力条件・形式・内容すべて制御可能）                  |
| 主な用途     | 監査証跡、業務可視化、原因追跡、分析                      |
| 監査向きか   | ◎（設計次第で要件を満たせる）                             |

---

# 【追加分】

**1. HTTPリクエスト/レスポンス証跡の保存**
記録が必要な内容：

- HTTPリクエスト（メソッド、パス、ヘッダー、ボディ）
- HTTPレスポンス（Status Code、レスポンスボディ）
- 処理時間

**2. 監査証跡要件への準拠**

Lambdaのログ出力は以下の監査証跡要件を満たす必要があります：

| 項目         | 必須（MUST）                   | 推奨（WANT）                 |
| ------------ | ------------------------------ | ---------------------------- |
| 操作日時     | 正確な時刻（タイムゾーン明示） | UTC統一                      |
| 操作ユーザー | ユーザーID、認証情報           | ロール・権限も記録           |
| 操作内容     | 何をしたか（CRUD等）           | API呼び出しやUI操作の種類    |
| 操作対象     | データ・サービス名             | 変更前後の値（Before/After） |
| 操作元情報   | IPアドレス、端末情報、アプリ名 | User-Agent、アクセス方法     |
| 結果         | 成功/失敗、エラーコード        | 通知内容・本文               |

**3. ログ暗号化**

Lambda内で出力するログについて：

- 業務データ・個人情報を平文で保存しない
- リクエストボディ・レスポンスボディに含まれる機微情報は論理暗号化が必要

**4. 異常アクセス検知**

Lambdaで以下のケースを検知・記録し、通知に繋げる：
コンポーネント側

- 想定された経路を経由しない呼び出し

アプリ側

- 権限のないリソースへのアクセス試行（403エラー）
- 認証失敗

**5. その他**
アプリ側

- ログレベル対応

**論点：Lambda実装で対応すべき事項**

1. 構造化ログの出力 - 監査証跡要件（3章）に準拠した形式
2. リクエスト/レスポンスのロギング - メソッド、パス、ヘッダー、ボディ、ステータスコード、処理時間
3. 機微情報のマスキング/暗号化 - 出力しないもしくは平文でログに残さない
4. 定常外アクセス・エラー・失敗時のログ出力 - 異常検知・通知のトリガーとして活用

---

- 参考ドキュメント：
  - [Lambda 管理イベント](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/logging-using-cloudtrail.html)
  - [Lambda メトリクスの種類](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/monitoring-metrics-types.html)
  - [Lambda 関数 ログの種類](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/monitoring-logs.html)
