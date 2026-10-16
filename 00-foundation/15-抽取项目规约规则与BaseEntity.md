```
/opsx:explore

目的：为进入业务模块开发做准备，需要完成两件事：

1. 规则文件补充
   当前 {{规则目录}}/ 只有{{现有编码规范文件}}（YAGNI/DRY/TDD）和
   {{现有工作流规则文件}}（工作流）。
   但代码中已形成大量隐含模式（{{统一响应基类}}、{{页面布局模式}}、@PrePersist、
   shadcn/ui + Tailwind、{{API响应泛型类型}} 等），需要抽取为独立规则文件，
   让Agent在写新模块时自动遵循。
   建议拆分为：
   - backend-conventions.md（后端分层、DTO、异常处理、响应格式）
   - frontend-conventions.md（前端目录、组件结构、状态管理）
   - styling-conventions.md（Tailwind、shadcn/ui、响应式、视觉设计原则）
   - database-conventions.md（Entity基类、公共字段、命名）
   - api-conventions.md（API响应格式、错误码、分页）

2. 数据模型公共字段设计
   当前{{现有实体类}}用UUID主键 + @PrePersist/@PreUpdate管理时间戳，
   没有BaseEntity抽象类。后续业务模块（{{后续业务模块列表}}）需要统一的
   公共字段模式。请分析{{现有实体类}}，提炼可复用的BaseEntity。
```