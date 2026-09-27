# The World Manual

一个持续更新的个人知识库，用来收集和理解财富、时间、国家、产业、金融与生活结构之间的关系。

- **阅读网站**：https://docknek7.github.io/world-manual/
- **管理内容**：https://github.com/docknek7/world-manual
- **查看发布状态**：https://github.com/docknek7/world-manual/actions

## 网站怎么使用

网站由 MkDocs Material 生成，用于浏览、搜索和阅读笔记。当前没有登录后台或上传表单；添加资料时，在 GitHub 仓库编辑或上传文件，提交到 `main` 后，GitHub Actions 会重新构建并发布网站。

日常流程：**收集来源 → 写下摘要与自己的理解 → 保存到对应栏目 → 等待发布 → 在网站检查。**

## 内容放在哪里

| 栏目 | 仓库目录 | 适合收集的内容 |
| --- | --- | --- |
| 财富与时间 | `docs/wealth/` | 财务自由、固定支出、时间分配 |
| 国家如何运转 | `docs/states/` | GDP、生产率、公共政策、宏观指标 |
| 产业与公司 | `docs/industry/` | 产业链、商业模式、企业研究 |
| 金融系统 | `docs/finance/` | 利率、货币、银行、金融市场 |
| 国家案例 | `docs/countries/` | 某个国家的长期研究 |
| 数据与资料 | `docs/sources/` | 数据源、参考资料、待整理的链接 |

网站正文放在 `docs/` 中；仓库根目录的 `README.md` 是使用说明，修改它不会改变网站首页。网站首页对应 `docs/index.md`。

## 方法一：给已有页面补充内容

适合保存一条链接、一段摘记，或更新现有笔记。

1. 在 GitHub 仓库打开对应的 `.md` 文件。例如，资料链接可以先放到 `docs/sources/data-sources.md`。
2. 点击铅笔图标 **Edit this file**。
3. 在正文中补充内容，例如：

   ```markdown
   ### 资料标题
   - 来源：[原文标题](https://example.com/article)
   - 收集日期：YYYY-MM-DD
   - 主要内容：用自己的话概括。
   - 我的理解：这条资料与哪些已有笔记有关？
   - 待核实：哪些结论还需要其他证据？
   ```

4. 点击 **Preview** 检查格式，再点击 **Commit changes**。
5. 填写修改说明，例如“补充一条产业研究资料”。如果允许直接提交，选择提交到 `main`；如果选择新分支，需要合并 Pull Request 后才会发布。
6. 在仓库 **Actions** 页面等待这次部署成功，然后刷新网站。

修改已经出现在导航中的页面，无需修改导航配置。

## 方法二：新建一篇笔记

以新增一篇“通货膨胀笔记”为例：

1. 在仓库根目录点击 **Add file → Create new file**。
2. 文件名填写 `docs/finance/inflation.md`。建议用简短英文文件名，中文标题写在正文第一行。
3. 粘贴下面的模板，替换其中的提示文字后提交：

   ```markdown
   # 通货膨胀笔记

   更新日期：YYYY-MM-DD

   ## 一句话结论
   用一句话概括目前的理解。

   ## 为什么关心
   这个问题与我的生活、工作或研究有什么关系？

   ## 主要信息
   - 事实或数据：注明时间、单位和统计口径。
   - 来源观点：说明是谁提出的。
   - 我的判断：写清推理过程和不确定性。

   ## 例子与证据
   记录具体案例、数据或图表。

   ## 尚未解决的问题
   - 下一步想核实什么？

   ## 来源
   - [文章或报告标题](https://example.com/report) — 作者或机构，发布日期，访问日期。
   ```

4. 回到仓库根目录，编辑 `mkdocs.yml`，在现有 `nav:` 下的“金融系统”中追加一行：

   ```yaml
     - 金融系统:
         - finance/index.md
         - 利率为什么重要: finance/interest-rates.md
         - 通货膨胀笔记: finance/inflation.md
   ```

   保留其他栏目，只在现有栏目中增加条目。路径相对于 `docs/`，不要再写 `docs/` 前缀；缩进使用空格，并与相邻条目对齐。

5. 提交 `mkdocs.yml`，等待最新一次 Actions 部署成功。

当前网站手动配置了导航，所以新建文件后还需要添加导航条目，才能在菜单中找到它。编辑已有笔记则不需要重复添加。

## 方法三：上传图片、PDF 和其他附件

建议按用途存放：

```text
docs/
  assets/
    images/      # 笔记配图
    files/       # PDF、表格等附件
    stylesheets/ # 现有网站样式
```

1. 在电脑上准备 `images` 或 `files` 文件夹，把附件放入其中。
2. 在 GitHub 打开 `docs/assets/`，点击 **Add file → Upload files**，拖入准备好的文件夹；提交前检查上传路径。后续可以直接进入已有附件目录上传文件。
3. 在笔记中添加相对链接。例如，在 `docs/finance/inflation.md` 中引用附件：

   ```markdown
   ![图表说明](../assets/images/inflation-chart.png)

   [阅读研究报告（PDF）](../assets/files/inflation-report.pdf)
   ```

   上面的示例适用于栏目子目录里的笔记；如果在 `docs/index.md` 中引用，应使用 `assets/...`，不加 `../`。

4. 提交并等待部署成功，在网站中检查图片和附件链接。

GitHub 网页上传单个文件的上限是 **25 MiB**。较大的资料可以保留原始来源链接。PDF 和 Word 文件不会自动变成正文页面；建议另写一篇 Markdown 笔记，介绍资料并链接附件。

## 整理资料的小习惯

- 来不及整理时，先在“数据与资料”的现有页面记录链接和一句话摘要。
- 一个问题积累出完整内容后，再整理为独立笔记并加入导航。
- 区分原始事实、来源观点和自己的判断；为数据保留日期、单位与出处。
- 更新旧笔记时补充更新日期，方便以后判断信息是否仍然适用。

## 提交后为什么没有变化

先打开仓库的 [Actions 页面](https://github.com/docknek7/world-manual/actions)，查看最新一次 **Deploy MkDocs to GitHub Pages**：

- **正在运行**：等待构建和部署结束后再刷新网站。
- **运行失败**：打开失败步骤的日志。优先检查 `mkdocs.yml` 的缩进、文件路径，以及笔记中的链接。
- **部署成功但菜单没有新文章**：检查是否已将文章加入 `mkdocs.yml` 的 `nav`。
- **找不到对应的发布记录**：确认修改已经进入 `main`，而不是仍停留在其他分支。
- **只修改了 README**：这是仓库说明；要修改网站首页，请编辑 `docs/index.md`。

部署工作流位于 `.github/workflows/deploy.yml`。仓库 **Settings → Pages → Source** 应选择 **GitHub Actions**。

## 可选：在电脑上预览

在项目根目录打开终端，首次使用时执行：

```bash
python -m venv .venv
```

Windows PowerShell：

```powershell
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m mkdocs serve
```

macOS / Linux：

```bash
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m mkdocs serve
```

打开 http://127.0.0.1:8000/ 预览，按 `Ctrl+C` 停止。以后只需运行 `mkdocs serve` 对应的命令。电脑上的修改仍需提交并推送到 GitHub 才会更新公开网站。

## 参考

- [GitHub：创建新文件](https://docs.github.com/en/repositories/working-with-files/managing-files/creating-new-files)
- [GitHub：上传文件](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)

Built with MkDocs Material.
