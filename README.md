# YAX-J

Java 后端 / 微服务。把业务拆成服务，把服务跑到线上。

作品集（系统结构、部署方式与取舍）：**https://yax-j.github.io/portfolio/**

## 项目

### [stellar-ink](https://github.com/YAX-J/stellar-ink) — 写作社区

Vue 3 前端 + Spring Cloud Alibaba 后端。三个 Java 进程：网关、用户服务、内容服务。

- 网关只留显式路由（关掉 discovery locator），按路径和角色鉴权；JWT 无状态验签，登出与改密把令牌摘要写进 Redis 撤销列表，路由前拦截。
- 缓存键是「命名空间版本 + 参数指纹」，写入后推进版本，旧参数组合立刻不可达；Redis 故障回源 MySQL 并熔断 30 秒。
- Nginx 前置：登录 10 次/分、公开写接口 6 次/分限流；Docker Compose 编排，Cloudflare 源站 TLS。

`Java 17` `Spring Boot 3` `Spring Cloud Alibaba` `Nacos` `MyBatis-Plus` `MySQL` `Redis` `Vue 3` `Docker`

### [RepoSleuth](https://github.com/YAX-J/RepoSleuth) — 多 Agent 代码侦探

输入一个 GitHub 链接，或者一句「帮我找一个处理 PDF 的库」；它自己检索、clone、精读，输出 mermaid 架构图、新人上手路线和风险清单。

- Scout 选库，三个分析 Agent 并行：Cartographer 画结构、Reader 管可读性、Auditor 挑风险，最后由 Chief 汇总。
- LangGraph 状态机编排；检索排序 Top1 达到阈值才自动选定，否则把候选交给人确认。
- 同一套工具封装成无状态 MCP Server（5 个工具），可挂进 Claude / Cursor；网页端 FastAPI + SSE 推送阶段事件。
- 单测用假模型 + 两个真实仓库基线，不联网也能跑。

`Python` `LangGraph` `MCP` `Gradio` `FastAPI` `GitHub API`

## 常用

Java 17 / Spring Boot 3 / Spring Cloud Alibaba / Nacos / MyBatis-Plus / MySQL / Redis / Docker / Nginx / Vue 3 / Python

## 找到我

- 作品集：https://yax-j.github.io/portfolio/
- 仓库：https://github.com/YAX-J
