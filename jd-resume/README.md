# JD 解读 & 简历生成器

> 粘贴招聘 JD，AI 自动分析岗位要求并生成匹配的简历内容草稿。纯静态网页，无需服务器，3 步部署到 GitHub Pages。

---

## 功能特性

- **JD 结构分析**：提取岗位名称、级别、经验学历要求、必备技能、加分技能、核心关键词
- **简历内容生成**：自动生成「个人总结 / 核心技能 / 工作经历示例 / 项目经历示例」四大模块
- **流式输出**：AI 内容边生成边展示，打字机效果
- **一键复制**：每个模块独立复制 + 全部内容一键复制
- **多 API 兼容**：支持 OpenAI、DeepSeek、Moonshot、硅基流动等所有 OpenAI 格式接口
- **隐私安全**：API Key 仅存储在浏览器本地 localStorage，不经过任何服务器

---

## 快速部署到 GitHub Pages（3 步）

### 第 1 步：Fork 仓库

点击本页右上角的 **Fork** 按钮，将仓库复制到你的账号下。

### 第 2 步：开启 GitHub Pages

进入你 Fork 的仓库：

1. 点击顶部 **Settings** 选项卡
2. 左侧菜单找到 **Pages**
3. Source 选择 `Deploy from a branch`
4. Branch 选择 `main`，目录选择 `/ (root)`
5. 点击 **Save**

### 第 3 步：访问你的网站

等待约 1 分钟后，访问：

```
https://你的用户名.github.io/仓库名
```

---

## 本地使用

无需任何安装或构建工具，直接用浏览器打开 `index.html` 即可。

> 注意：部分浏览器限制本地文件的 `fetch` 请求（CORS），推荐用 GitHub Pages 或本地 HTTP 服务器运行：
> ```bash
> # Python 3
> python -m http.server 8080
> # 然后访问 http://localhost:8080
> ```

---

## API 配置

首次打开页面，设置面板会自动展开，填写以下信息：

| 字段 | 说明 | 示例 |
|------|------|------|
| API Key | 你的 API 密钥 | `sk-...` |
| Base URL | API 服务地址 | `https://api.openai.com` |
| 模型名称 | 使用的模型 | `gpt-4o-mini` |

点击面板内的快捷按钮可一键填入常用 API 地址。

### 推荐 API 服务对比

| 服务商 | Base URL | 推荐模型 | 价格参考 | 特点 |
|--------|---------|---------|---------|------|
| **OpenAI** | `https://api.openai.com` | `gpt-4o-mini` | $0.15/1M tokens | 质量最高 |
| **DeepSeek** | `https://api.deepseek.com` | `deepseek-chat` | ¥1/1M tokens | 性价比极高，中文优秀 |
| **Moonshot** | `https://api.moonshot.cn` | `moonshot-v1-8k` | ¥12/1M tokens | 中文优化 |
| **硅基流动** | `https://api.siliconflow.cn` | `Qwen/Qwen2.5-72B-Instruct` | 免费额度 | 国内访问快 |

> 推荐使用 **DeepSeek** —— 价格极低，中文效果优秀，非常适合简历生成场景。

---

## 使用流程

1. 打开网页，配置 API Key
2. 将目标岗位的招聘 JD 粘贴到左侧文本框
3. 点击「🔍 分析 JD」—— 查看岗位结构化分析（关键词、技能要求等）
4. 点击「✨ 生成简历内容」—— AI 流式生成简历内容草稿
5. 点击各模块的复制按钮，将内容填入你的简历模板

> **提示**：AI 生成的简历内容是基于 JD 的通用模板，请结合你的真实工作经历进行修改和完善，不要直接投递。

---

## 快捷键

| 快捷键 | 功能 |
|--------|------|
| `Ctrl + Enter` | 快速分析当前 JD |

---

## 隐私说明

- API Key 仅保存在你自己浏览器的 `localStorage` 中
- JD 内容会直接发送到你配置的 API 服务（OpenAI / DeepSeek 等），不经过本工具的任何服务器
- 本工具完全开源，可自行审查所有代码（仅 `index.html` 一个文件）
- 建议使用个人用途的 API Key，并定期轮换

---

## 技术栈

- 纯 HTML / CSS / JavaScript（无框架，无构建工具）
- 调用 OpenAI Chat Completions API（兼容格式）
- 流式输出使用 Server-Sent Events (SSE) 解析
- 所有数据存储在浏览器 localStorage

---

## 许可证

MIT License — 自由使用、修改、分发。
