```
/opsx:explore

目的：将数据库从H2内存库切换到本地MySQL 8

1. pom.xml：添加 mysql-connector-j 依赖，移除 h2

2. application.yml：
   - datasource.url → jdbc:mysql://{{MySQL主机}}:{{MySQL端口}}/{{数据库名称}}
   - driver → com.mysql.cj.jdbc.Driver
   - ddl-auto → update（保留数据，只同步结构变更）
   - 移除 h2.console 配置

3. MySQL准备：
   - 创建 {{数据库名称}} 数据库
   - 字符集 utf8mb4

4. 遵循 {{数据库规则文件}}（UUID主键、snake_case表名）
```

