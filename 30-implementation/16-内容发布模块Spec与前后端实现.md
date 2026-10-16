```
/opsx:explore

目的：为{{内容模块名称}}模块设计capability spec

1. 参考{{项目说明文件路径}}中"{{内容业务定义所在章节}}"的定义
   以及{{认证后端API的Spec路径}}的spec结构
   输出{{内容模块标识}}的capability spec

2. 内容数据模型：Markdown富文本
   字段：title/content(Markdown)/coverImage/tags/status
   支持：发布、编辑、列表、详情

3. 接口需要JWT认证（写操作），读操作公开

4. 参考{{认证模块Spec路径}}的WHEN/THEN格式定义验收标准
```

```
/opsx:explore

目的：根据{{内容模块标识}} spec实现后端CRUD

1. {{内容实体类}}继承{{实体基类}}
   业务字段：authorId/title/content(Markdown)/
   coverImage/tags(JSON)/status(draft|published)

2. 严格遵循三层架构 + DTO分离
   Response继承{{响应基类}}，禁止返回Entity

3. 写操作（POST/PUT/DELETE）需要JWT认证
   参考{{认证控制器类}}的Bearer token提取模式
   读操作（GET列表/GET详情）公开

4. 遵循{{后端开发规则文件}} + {{数据库规则文件}}
```

```
/opsx:explore

目的：根据{{内容模块标识}} spec实现前端页面

1. 页面路由（参考{{认证模块路由分组}}路由分组模式）：
   - {{内容列表页面路径}} → 内容列表
   - {{内容发布页面路径}} → 发布（需登录）
   - {{内容详情页面路径}} → 详情

2. 选用合适的React Markdown编辑器组件（带工具栏）
   支持标题、Markdown正文、封面图URL、标签输入

3. API封装参考{{认证API封装文件路径}}的
   {{API响应泛型类型}} + {{响应解析函数}}模式

4. 遵循{{前端开发规则文件}} + {{样式规则文件}}
```