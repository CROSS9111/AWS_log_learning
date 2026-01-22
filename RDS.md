# RDS

**対象：SFDC用リレーショナルデータベース**

---

# 【現行調査】

RDSはSDFC用に追加になるコンポーネントのため、現状の取得しているログはなし

---

# 【追加分】（今回の要求で必須）

- 「誰が・いつ・どのDB構成を変更したか」を証跡として残す
- 不正な設定変更・削除を検知可能にする

## 1. RDS 管理イベント（CloudTrail） | デフォルトで取得

| アクション                                          | 説明                     |
| --------------------------------------------------- | ------------------------ |
| CreateDBInstance / DeleteDBInstance                 | DBインスタンス作成・削除 |
| ModifyDBInstance                                    | インスタンス設定変更     |
| CreateDBCluster / ModifyDBCluster / DeleteDBCluster | Aurora クラスター操作    |
| CreateDBSnapshot / DeleteDBSnapshot                 | スナップショット操作     |
| RestoreDBInstanceFromSnapshot                       | スナップショット復元     |
| ModifyDBParameterGroup                              | パラメータ変更           |
| AddTagsToResource / RemoveTagsFromResource          | タグ操作                 |

## 2. RDS データプレーン操作（DB内操作） | 追加で取得

### PostgreSQL / Aurora PostgreSQL

| ログ                                 | 内容                          |
| ------------------------------------ | ----------------------------- |
| log_connections / log_disconnections | ログイン/ログアウト           |
| log_statement                        | SQL実行履歴                   |
| pgaudit                              | SELECT/INSERT/UPDATE/DDL 監査 |

---

## 3. CloudWatch メトリクス（異常検知） | デフォルトで取得

**目的：**

- 監査ログの「補助線」
- 不正アクセス・異常負荷の兆候検知

| メトリクス           | 用途             |
| -------------------- | ---------------- |
| DatabaseConnections  | 不審な接続増加   |
| CPUUtilization       | 異常負荷         |
| FreeableMemory       | リソース枯渇     |
| ReadIOPS / WriteIOPS | 想定外の大量操作 |
