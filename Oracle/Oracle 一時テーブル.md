#oracle


PRIVATE TEMPORARY TABLE: 同一セッションからのみ使用できる
PUBLIC TEMPORARY TABLE: 他のセッションからも使用できる

```sql
CREATE PRIVATE TEMPORARY TABLE ORA$PTT_xxx (
   id       NUMBER,
   name VARCHAR2(32)
)
ON COMMIT PRESERVE DEFINITION
-- このようにすると、テーブル定義はせしょんが終了するまで残る。
-- **コミットでテーブル定義を消す場合は
ON COMMIT DROP DEFINITION
```

命名規則：
 「ORA$PTT_」 始まり　（private_temp_table_prefixパラメタに指定された値。デフォルトがORA\$PTT)

private_temp_table_prefixの設定値は以下で確認できる
```
SQL> SHOW PRAMETER private_temp_table_prefix
```
