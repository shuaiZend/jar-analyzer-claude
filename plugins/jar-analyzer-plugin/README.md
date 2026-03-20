# jar-analyzer-plugin

基于 [jar-analyzer](https://github.com/jar-analyzer/jar-analyzer) 的 Claude Code 插件，
用于 Java JAR/WAR 包静态分析与安全审计。

## 功能

- **构建分析数据库**：从 JAR/WAR/Class 文件构建 SQLite 数据库，提取类信息、方法调用关系、继承关系等
- **安全审计分析**：基于数据库查询，检测 RCE、SQL 注入、SSRF、反序列化等常见漏洞模式
- **方法调用链追踪**：从危险 sink 回溯到 HTTP 入口，验证漏洞可达性
- **反编译验证**：内置 FernFlower 反编译器，快速查看可疑代码
- **Spring 组件分析**：自动识别 Controller、Mapping、拦截器等组件
- **字符串敏感信息检测**：搜索硬编码密码、密钥、JNDI 地址等

## Skills

| Skill | 说明 | 触发方式 |
|:------|:-----|:---------|
| `build-db` | 从 JAR/WAR 文件构建 SQLite 分析数据库 | `/build-db` |
| `do-analyze` | 对分析数据库执行安全审计查询 | `/do-analyze` |

### 典型工作流

```
1. /build-db    → 指定 JAR/WAR 文件，构建数据库
2. /do-analyze  → 对数据库执行安全分析查询
```

## 环境要求

- Java 8+（用于运行分析引擎和反编译）
- Python 3+（用于执行 SQL 查询脚本）

## 致谢

- [jar-analyzer](https://github.com/jar-analyzer/jar-analyzer) — 4ra1n
