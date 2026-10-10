# yyc3-agent-core

YYC³（YanYuCloudCube）agent 核心库 monorepo —— Octop 四个伴随包的 **Fork-and-Own** 基线。

## 包一览

| 目录 | 发行名 | 上游基线 | 职责 |
| ---- | ------ | -------- | ---- |
| `packages/harness` | `yyc3-harness` | octop-harness 1.0.2 | Agent harness（deepagents + langchain 1.x + langgraph） |
| `packages/memory` | `yyc3-memory` | octop-memory 1.0.1 | 分层记忆 / FTS 检索 / 多后端（核心零依赖） |
| `packages/gateway` | `yyc3-gateway` | octop-gateway 1.0.1 | 8 平台 IM 通道桥接（飞书 / 钉钉 / Discord / 企业微信 / Telegram / QQ / MQTT / WebSocket） |
| `packages/browser` | `yyc3-browser` | octop-browser 1.0.0 | CDP 浏览器自动化（profile 登录持久化） |

## Fork-and-Own 原则

1. **发行名切换**：PyPI 发行名统一 `yyc3-*`；包间依赖同步改指向（harness → yyc3-memory / yyc3-browser）。
2. **内部模块名不变**：`octop_harness` / `octop_memory` / `octop_gateway` / `octop_browser` 保持上游原名，保证调用方 import 源码级兼容。
3. **独立演进**：与上游 TencentCloud/octop-* 无 remote、无同步义务；版本号自主线起独立推进。
4. **归属合规**：上游 MIT 许可，原始版权与来源见 [NOTICE.md](NOTICE.md) 与各包自带 `LICENSE`。

## 工作区

uv workspace 根（virtual manifest）：

```bash
uv sync --all-packages   # 安装全部工作区成员
uv run pytest packages/harness/tests -q
```
