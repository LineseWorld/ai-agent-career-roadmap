# Python 学习内容与方法

## 学习目标

目标不是把 Python 所有语法学完，而是在两周内具备开发 AI Agent 后端的基本能力：

- 能读懂和修改常见 Python 项目；
- 能用 FastAPI 编写异步 HTTP 服务；
- 能调用模型 API、数据库和设备接口；
- 能处理异常、超时、重试和并发；
- 能编写自动化测试；
- 能将服务打包并运行。

## 一、必须掌握的 Python 内容

### 1. 基础语法快速复查

- 字符串、数字、布尔值和 `None`
- list、tuple、dict、set
- 切片、列表/字典推导式
- 条件、循环和函数
- `*args`、`**kwargs`、默认参数
- 模块、包和 import
- 文件与 JSON 读写

掌握标准：看到代码能读懂，能够不查教程写出普通数据处理函数。不需要重复刷大量语法题。

### 2. 类型与数据建模

- `str | None`、`list[str]`、`dict[str, Any]`
- `Callable`、`Protocol`、`TypedDict`
- dataclass
- Enum
- Pydantic `BaseModel`
- 字段约束、自定义校验和序列化

对应 Agent 场景：工具参数 Schema、模型结构化输出、API 请求与响应、设备状态模型。

### 3. 面向对象与 Python 工程习惯

- 类、继承、组合和抽象接口
- 实例方法、类方法、静态方法
- 属性和对象生命周期
- 上下文管理器 `with`
- 迭代器与生成器基础
- 项目分层和依赖方向

不要照搬复杂 C++ 继承体系。Python 项目优先使用小类、组合和明确接口。

### 4. 异常、日志与配置

- `try/except/else/finally`
- 自定义异常
- `raise ... from ...`
- `logging`
- 环境变量与 `.env`
- 配置模型
- request_id / trace_id

对应 Agent 场景：区分模型错误、参数错误、工具错误、设备离线和业务规则拒绝。

### 5. 异步编程——重点

- coroutine、event loop、`async`、`await`
- `asyncio.create_task`
- `asyncio.gather`
- `asyncio.wait_for` / timeout
- Semaphore 并发限制
- Lock 与共享状态
- 任务取消和异常传播
- 阻塞 I/O 与异步 I/O 的区别
- 在线程池中运行阻塞代码

对应 Agent 场景：并发请求模型、数据库、多个工具和设备；处理超时、取消与流式输出。

### 6. HTTP 客户端与 FastAPI

- HTTP 方法、状态码和 JSON
- httpx 异步客户端
- FastAPI 路由
- 请求/响应模型
- Depends 依赖注入
- 中间件和异常处理器
- 生命周期管理
- SSE 流式响应
- 鉴权基础

### 7. 数据库

- SQL 基础：增删改查、JOIN、索引和事务
- SQLAlchemy ORM
- AsyncSession
- 数据库连接池
- Repository/Service 分层
- PostgreSQL
- Redis缓存、TTL和幂等键

### 8. 测试

- pytest 的 `assert`
- fixture
- parametrize
- mock / monkeypatch
- FastAPI TestClient
- HTTPX AsyncClient
- 单元测试与集成测试的边界
- 异常、超时和重试测试

### 9. 项目与环境管理

- Git 基本流程
- `pyproject.toml`
- 使用 uv 或虚拟环境管理依赖
- Ruff 格式化与静态检查
- pyright 或 mypy 类型检查
- Dockerfile 与 Docker Compose
- 环境变量和密钥隔离

## 二、当前不需要深入的内容

- Python 元类和描述符的复杂用法
- CPython 源码和解释器实现
- 高难度算法竞赛题
- GUI 框架
- Django 全家桶
- 数据科学全套工具
- NumPy/Pandas 的高级用法
- 深度学习模型从零训练

遇到项目真实需求时再补，不要用这些内容延迟 Agent 项目。

## 三、最有效的学习方式

采用“任务驱动 + 官方文档 + 立即重写”的方式。

### 每个知识点按四步学习

1. 用 20～40 分钟阅读官方教程，理解概念和最小示例；
2. 关闭文档，凭理解重新写一遍；
3. 把它接入企业智能工单 Agent 项目；
4. 主动制造一个失败场景，并为它补测试。

例如学习异步，不要只抄 `async/await`：

- 同时查询 5 台设备；
- 其中一台延迟 5 秒；
- 设置 1 秒超时；
- 限制最多 3 个并发；
- 取消请求后确认子任务正确退出；
- 用 pytest 验证结果。

### 三遍学习法

- 第一遍：能用——完成最小功能；
- 第二遍：能解释——说清原理和失败场景；
- 第三遍：能工程化——补异常、日志、测试和类型。

不要在第一遍就追求彻底掌握。

### 使用 AI 编程工具的规则

可以使用 AI 辅助，但需要遵守：

- 先自己写接口和数据结构，再让 AI 补样板代码；
- 对生成代码逐行审查；
- 要求 AI 同时生成测试和失败用例；
- 不懂的代码不能合并；
- 每天至少有一个关键模块由自己从空文件写出；
- 能在不看代码时讲清执行流程。

## 四、两周全职学习安排

### 第 1 天：语法与项目环境

- 快速复查容器、函数、模块、文件和 JSON；
- 创建 `pyproject.toml`；
- 配置 uv、Ruff、pytest；
- 写一个设备 JSON 读取与校验程序。

### 第 2 天：类型、Pydantic 与数据模型

- 定义 Device、Command、CommandResult；
- 为速度范围、设备编号和命令类型添加校验；
- 为模型编写参数化测试。

### 第 3 天：类、接口、异常和日志

- 定义 DeviceGateway 接口；
- 实现内存模拟网关；
- 定义 DeviceOffline、InvalidTransition 等异常；
- 添加结构化日志。

### 第 4 天：asyncio

- 并发查询多个设备；
- 实现超时、并发限制和任务取消；
- 比较串行与并发耗时；
- 测试其中一个设备失败的情况。

### 第 5 天：httpx 与外部 API

- 调用一个 HTTP 服务；
- 实现连接超时、读取超时和有限重试；
- 使用 mock 测试 200、429、500 和超时。

### 第 6 天：FastAPI

- 实现设备和命令接口；
- 使用请求/响应模型；
- 添加统一异常处理和 OpenAPI 文档；
- 用 TestClient 测试。

### 第 7 天：复盘与重构

- 不增加新功能；
- 删除重复代码；
- 补齐类型、日志和测试；
- 在 10 分钟内讲解项目结构。

### 第 8 天：PostgreSQL 与 SQLAlchemy

- 保存设备、命令和执行记录；
- 实现事务；
- 学习索引与连接池；
- 编写数据库集成测试。

### 第 9 天：Redis 与可靠性

- 缓存设备状态；
- 使用幂等键防止重复命令；
- 设置 TTL；
- 测试缓存失效和重复请求。

### 第 10 天：依赖注入与分层

- 拆分 API、Service、Repository、Gateway；
- 用 FastAPI Depends 注入数据库和当前用户；
- 测试时替换真实依赖。

### 第 11 天：流式响应

- 实现 SSE；
- 模拟模型逐字输出；
- 客户端断开后取消后台任务；
- 记录首 Token 延迟。

### 第 12 天：测试专项

- 单元测试、API测试和集成测试；
- 覆盖正常、非法参数、超时、重复调用和设备离线；
- 目标不是盲目追求覆盖率，而是覆盖高风险行为。

### 第 13 天：Docker 与配置

- 编写 Dockerfile 和 Compose；
- 启动 API、PostgreSQL 和 Redis；
- 从环境变量读取密钥；
- 验证全新环境能一键启动。

### 第 14 天：综合验收

- 从空白实现一个小接口；
- 完整运行测试；
- 修复类型和静态检查错误；
- 更新 README；
- 录制 2 分钟演示。

## 五、学习资料顺序

以官方文档为主，不需要从第一页读到最后一页：

1. [Python 官方教程](https://docs.python.org/zh-cn/3/tutorial/)
2. [Python asyncio 文档](https://docs.python.org/zh-cn/3/library/asyncio.html)
3. [Python typing 文档](https://docs.python.org/3/library/typing.html)
4. [Pydantic 文档](https://docs.pydantic.dev/latest/concepts/models/)
5. [FastAPI Tutorial](https://fastapi.tiangolo.com/tutorial/)
6. [FastAPI async 说明](https://fastapi.tiangolo.com/async/)
7. [SQLAlchemy Unified Tutorial](https://docs.sqlalchemy.org/en/20/tutorial/)
8. [pytest 文档](https://docs.pytest.org/en/stable/)

视频课程只用来帮助理解难点，不以“看完课程”为目标。遇到问题优先查官方文档、运行最小实验，再搜索具体报错。

## 六、两周验收题

如果可以独立完成下面任务，就停止单独学习 Python，转入 Agent 主项目：

> 编写一个 FastAPI 服务，并发查询 5 台模拟设备；每台设备设置独立超时；将命令记录保存到 PostgreSQL；使用 Redis 幂等键阻止重复执行；设备离线时返回统一错误；通过 SSE 输出执行进度；为正常、超时、非法参数和重复命令编写测试；最后用 Docker Compose 一键运行。

验收标准：

- 不依赖教程逐行照抄；
- 能解释 `async def` 何时有用、何时会阻塞；
- 能定位堆栈和日志中的错误；
- 测试可以重复运行；
- 代码结构可以继续接入 LLM Tool Calling。
