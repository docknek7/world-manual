# The World Manual

一个用于长期整理“财富与时间、国家运行、产业链、金融系统、生活结构”的个人知识库。

## 本地运行

```bash
python -m venv .venv
```

Windows:

```bash
.venv\Scripts\activate
pip install -r requirements.txt
mkdocs serve
```

macOS / Linux:

```bash
source .venv/bin/activate
pip install -r requirements.txt
mkdocs serve
```

然后打开：

```text
http://127.0.0.1:8000
```

## 发布到 GitHub Pages

1. 新建一个 GitHub 仓库，例如 `world-manual`
2. 把本项目全部文件推送到仓库
3. 修改 `mkdocs.yml` 中的 `site_url`
4. GitHub 仓库进入 Settings → Pages
5. Source 选择 **GitHub Actions**
6. 推送到 `main` 分支后，网站会自动构建并部署

## 日常写作

以后基本只需要在 `docs/` 里新建 Markdown 文件，然后更新 `mkdocs.yml` 里的 `nav`。

建议每篇笔记都包含：

- 一句话结论
- 为什么关心
- 核心概念
- 一个具体例子
- 数据或证据
- 我目前的理解
- 尚未解决的问题
- 来源
