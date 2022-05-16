# 1. 配置相关

# 2. SQL相关
## 2.1 判断表是否存在
```sql
    <select id="isTableExisted" resultType="java.lang.Boolean">
        SELECT COUNT(*) FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA=DATABASE() AND TABLE_NAME = UPPER(#{tableName})
    </select>

    <select id="isTableExisted" resultType="java.lang.Boolean" databaseId="oracle">
        SELECT COUNT(*) FROM USER_TABLES WHERE TABLE_NAME = UPPER(#{tableName})
    </select>

    <select id="isTableExisted" resultType="java.lang.Boolean" databaseId="sqlserver">
        SELECT COUNT(*) FROM DBO.SYSOBJECTS WHERE ID = OBJECT_ID(UPPER(#{tableName})) AND OBJECTPROPERTY(ID, N'ISUSERTABLE') = 1
    </select>

     <select id="isTableExisted" resultType="java.lang.Boolean" databaseId="db2">
        SELECT COUNT(*) FROM SYSCAT.TABLES WHERE TABNAME= UPPER(#{tableName})
    </select>
```