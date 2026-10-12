# 由简入深 · AI 学习站（L1–L16）

> 16 个纯静态中文 AI 学习小站，从「先把 AI 用起来」一路走到「把智能体部署上线」。
> 零后端、零依赖、无需构建，下载下来打开就能看。

A series of 16 static Chinese-language sites that teach AI from zero to production agents.
Pure static HTML/CSS/JS — no backend, no build step, no dependencies.

---

## 这套东西是什么

这不是一份大纲或者一篇长文，而是 **16 个各自独立、可以直接部署上线的学习站点**。
每一站聚焦一个台阶，前一站解决「用起来」，后一站解决「讲清楚」，最后一站把整套东西落到能跑的服务上。

设计上刻意避开了两个常见毛病：

- **不讲用不上的原理。** 每一节都对应一个能立刻动手练的动作。
- **不堆砌术语。** 能用类比讲清楚的地方，不引入公式；必须引入公式的地方，配手算小例子。

---

## 十六站总览

| # | 站点 | 目录 | 主题 | 建议天数 |
|---|------|------|------|---------|
| L1 | AI 入门 | `sites/01-ai101` | 从零开始会用 AI：怎么问、怎么验、怎么避开胡说八道 | 7 天 |
| L2 | 大模型原理 | `sites/02-llm-course` | 词元、注意力、预训练到对齐，看懂大模型怎么来的 | 14 天 |
| L3 | 深度学习基础 | `sites/03-dl` | 神经网络、反向传播、梯度下降，含手写多层感知机 | 10 天 |
| L4 | RAG 与 Agent | `sites/04-rag` | 给模型接资料库、让它会调用工具 | 10 天 |
| L5 | 微调与部署 | `sites/05-finetune` | 微调到底在改什么，以及模型怎么上线 | 10 天 |
| L6 | RLHF 对齐 | `sites/06-rlhf` | 偏好数据、奖励模型、PPO / DPO 讲成人话 | 10 天 |
| L7 | AIGC 创作 | `sites/07-aigc` | 文生图与文生视频，从提示词到出片 | — |
| L8 | MCP 协议 | `sites/08-mcp` | 让模型接上外部工具的标准插头 | — |
| L9 | Agent 实战 | `sites/09-agent` | 任务规划、记忆、工具调用，部署成可用服务 | — |
| L10 | 本地部署大模型 | `sites/10-local` | 选型、显存估算、量化取舍与常见坑 | — |
| L11 | 提示词工程 | `sites/11-prompt` | 结构化提示词、少样本、思维链与反面教材 | — |
| L12 | 多模态与 ComfyUI | `sites/12-comfy` | 本地跑图像与视频生成，工作流自己搭 | — |
| L13 | 企业级 RAG | `sites/13-ragpro` | 切分、混合检索、重排、评测与线上效果保障 | — |
| L14 | 微调实战进阶 | `sites/14-ftplus` | 训练数据构造、超参选择、过拟合判断 | — |
| L15 | AI 应用开发平台 | `sites/15-dify` | 不写代码把 AI 应用搭出来 | — |
| L16 | 推理模型与思维链 | `sites/16-reason` | 为什么「先想再答」能提高难题正确率 | — |

---

## 本地预览

不需要任何依赖，用任意静态服务器指向 `sites/` 下的某一站即可：

```bash
git clone https://github.com/oraguinal9/by-simple-to-deep.git
cd by-simple-to-deep

# 用 Python 起一个静态服务
python3 -m http.server 8080

# 浏览器打开
# http://localhost:8080/sites/01-ai101/
```

---

## 部署到服务器

每一站都是一个独立目录，直接作为 nginx 的站点根目录即可：

```nginx
server {
    listen 443 ssl http2;
    server_name ai101.example.com;
    root /var/www/ai101;
    index index.html;
    location / { try_files $uri $uri/ $uri.html =404; }
}
```

16 个站点可以用同一个目录结构、不同 `server_name` 批量配置。

---

## 目录结构

```
by-simple-to-deep/
├── sites/
│   ├── 01-ai101/          # 每站均含 index.html + assets/
│   ├── 02-llm-course/
│   ├── ...
│   └── 16-reason/
└── README.md
```

---

## 关于第三方材料

第 2 站（`sites/02-llm-course`）在线上版本中还包含一个 `materials/` 目录，内含两份**第三方开源项目**的文档，因其版权归属原作者，**本仓库不包含该目录**：

- [happy-llm](https://github.com/datawhalechina/happy-llm) —— 中文大模型原理与实践教程
- [llms-from-scratch-cn](https://github.com/datawhalechina/llms-from-scratch-cn) ——《从零构建大模型》中文版

有需要请前往上述原仓库获取。本仓库仅保留自己撰写的部分。

---

## 许可

[MIT](LICENSE)
