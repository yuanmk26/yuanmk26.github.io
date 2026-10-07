# Notes from Yuan's Bench

个人技术博客，记录探测器电子学、模拟前端设计、ADC、FPGA、DAQ、仪器仪表与硬件实验方面的笔记。

- 框架：Hugo（extended 版，v0.166.0）
- 主题：[Blowfish](https://github.com/nunocoracao/blowfish)（git submodule）
- 语言：简体中文（`zh-cn`），英文语言已禁用
- 部署：GitHub Pages，地址 https://yuanmk26.github.io/

## 文件结构

```
hugo.toml              站点主配置：baseURL、语言、菜单、主题参数
content/               文章内容（Markdown）
  about.md             关于页
  posts/               博客文章，一篇一个 .md
archetypes/default.md  新建文章的模板（hugo new 使用）
assets/img/avatar.jpg  头像，被 params.author.image 引用
static/                原样拷贝到 public/ 的静态文件（favicon.png 等）
layouts/partials/      对主题的部分覆盖（目前只有 favicons.html）
data/  i18n/           预留目录，当前为空
themes/                git submodule，不要直接改
  blowfish/            当前启用的主题
  PaperMod/            旧主题，已弃用，保留备用
public/                 hugo 构建产物（部分被 git 跟踪，见下）
resources/              Hugo 构建缓存（未跟踪）
.github/workflows/hugo.yaml  GitHub Pages 自动构建与部署
```

## 常用命令

```bash
hugo server -D          # 本地预览，包含草稿
hugo new posts/my-post.md   # 新建文章（默认 draft = true）
hugo --minify           # 生产构建，输出到 public/
```

## 撰写文章约定

新建文章使用 TOML front matter（见 `archetypes/default.md`），写完把 `draft` 改成 `false` 再提交。
`content/posts/` 下文章按日期排序，首页展示最近 5 篇。

数学公式已启用：块级用 `\[ \]` 或 `$$ $$`，行内用 `\( \)`。
Markdown 里可以直接写 HTML（`markup.goldmark.renderer.unsafe = true`）。

## 注意事项

- **不要直接修改 `themes/` 下的主题代码**。主题是 submodule，改动会在更新时丢失。
  覆盖主题行为请把对应文件放到项目根目录的 `layouts/`、`assets/` 或 `static/` 下。
- 主题配置写在 `hugo.toml` 的 `[params.*]` 中，参考 `themes/blowfish/` 的文档与示例。
- `public/` 里有早期提交遗留的构建产物被 git 跟踪，但 GitHub Actions 每次部署都会
  重新构建整个目录。**不要手动编辑 `public/` 里的文件**——改源头（`content/`、
  `hugo.toml`、`layouts/`、`assets/`）后重新构建。
- 部署是自动的：推送到 `main` 分支即触发构建发布，无需手动操作。
- 仓库目前没有 `.gitignore`，`resources/`、`.hugo_build.lock` 等构建产物处于未跟踪状态。
