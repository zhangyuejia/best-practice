## 1. 配置相关
## 2. 用法相关
### 2.1 使用流式查询
```java
   void queryValidBlacklist(ResultHandler<PbListBlack> handler);
```
```xml
  <select id="queryValidBlacklist" resultType="com.montnets.umc.portal.common.entity.PbListBlack" resultSetType="FORWARD_ONLY" >
    SELECT ID, BLTYPE, CORPCODE, SVRTYPE, PHONE FROM PB_LIST_BLACK WHERE OPTYPE=1
  </select>
```
## 3. SQL相关
### 3.1 判断表是否存在
```xml
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