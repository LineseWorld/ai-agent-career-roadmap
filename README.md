# AI Agent 工程化学习路线

本仓库整理 AI Agent 应用开发所需的 Python 后端、数据持久化、Tool Calling、RAG、工程化和面试知识，并提供可执行的阶段学习计划。

项目源代码已经拆分到独立仓库：

- [Service Desk Copilot](https://github.com/LineseWorld/service-desk-copilot)

## 适用岗位

1. AI Agent 应用工程师
2. 大模型应用开发工程师
3. RAG / Python AI 后端工程师
4. AI 解决方案工程师
5. 边缘 AI / C++ 推理部署工程师
6. 工业互联网 + AI 应用工程师

暂不作为主要方向：纯大模型训练、强化学习算法、要求论文或多年 SFT/RLHF 经历的岗位。

## 文档入口

- [八周冲刺计划](docs/八周冲刺计划.md)（学习、项目和面试准备的总执行入口）
- [企业智能工单 Agent 需求](docs/企业智能工单智能体需求.md)（当前唯一主项目需求）
- [第一轮开发指南](docs/第一轮开发指南.md)
- [Python 学习路线](docs/Python学习路线.md)
- [面试准备清单](docs/面试准备清单.md)
- [每周任务看板](docs/每周任务看板.md)
- [第一阶段学习归档](docs/第一阶段学习归档.md)
- [第二阶段学习归档：PostgreSQL 持久化](docs/第二阶段学习归档-PostgreSQL持久化.md)

## 推荐技术栈

```text
Python 3.11+
FastAPI + Pydantic + asyncio
原生 Tool Calling + LangGraph
PostgreSQL + pgvector + Redis
Docker Compose + pytest
OpenAI 兼容模型 API
Ollama / vLLM 基础部署
```

## 执行原则

- 建议每周投入约 40～45 小时，按 8 周集中学习。
- 50% 时间编码，20% 原理与面试，15% 岗位研究，15% 文档与复盘。
- 项目达到最小可演示状态后即可开始验证岗位匹配度，不必等待全部功能完成。
- 只主学一套技术栈，框架以 LangGraph 为主。
- 作品必须可以运行、测试、部署、演示和评测。

## 最终交付标准

- 1 个完整主项目：企业智能工单 Agent，不同时启动第二个作品项目。
- Git 仓库具备一键启动、测试、架构图、评测报告和演示视频。
- 能用 3 分钟介绍自己、15 分钟讲清核心项目。
- 能够在简历和面试中准确说明个人既有工程经验与 AI 应用能力的结合点。
