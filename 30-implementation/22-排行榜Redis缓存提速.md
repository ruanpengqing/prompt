```
/opsx:explore

目的：{{目标资源}}排行榜每次请求都查MySQL，想加一层缓存提速

1. 加Redis依赖
   - pom.xml 添加 spring-boot-starter-data-redis

2. 加Redis连接配置
   - application.yml 添加 {{Redis主机}}:{{Redis端口}} 的连接信息

3. 新建 {{排行榜缓存服务类}}
   - 方法1：查询排行榜缓存
     先从Redis里找有没有缓存的数据
     → 有，直接返回（不用查MySQL了）
     → 没有，调原来的{{业务查询服务类}}查数据库
       → 查完后把结果存一份到Redis
       → Redis里这份数据5分钟后自动删除（避免太旧）
   - 方法2：清除排行榜缓存
     {{目标资源}}数据有变化时，把Redis里存的那份删掉

4. 改造{{业务查询服务类}}.getRanking()
   - 不再直接查数据库
   - 改为调用{{排行榜缓存服务类}}
     让缓存来决定走Redis还是走数据库

5. 缓存key格式：{{业务缓存命名空间}}:ranking:{type}
   例如：{{业务缓存命名空间}}:ranking:heat
```