# Notes from Yuan's Bench

个人技术笔记，记录探测器电子学、模拟前端设计、ADC、FPGA、DAQ、仪器仪表，以及硬件实验中那些不太显眼的细节。

**在线访问：<https://yuanmk26.github.io/>**

## 内容方向

- 探测器电子学与读出链路
- 模拟前端（AFE）设计
- ADC / 采样与噪声
- FPGA 与 DAQ 系统
- 实验室仪器与测量方法

## 技术栈

| 项目 | 说明 |
| --- | --- |
| 静态站点 | [Hugo](https://gohugo.io/) extended，v0.166.0 |
| 主题 | [Blowfish](https://github.com/nunocoracao/blowfish) |
| 托管 | GitHub Pages |
| 部署 | GitHub Actions，推送 `main` 自动构建发布 |

## 本地预览

需要先安装 Hugo extended 版（v0.166.0 或更高），然后克隆并拉取主题：

```bash
git clone --recurse-submodules https://github.com/yuanmk26/yuanmk26.github.io.git
cd yuan-bench
hugo server -D
```

打开 <http://localhost:1313/> 即可预览，`-D` 表示同时显示草稿。

如果克隆时忘了 `--recurse-submodules`，补一句：

```bash
git submodule update --init --recursive
```

## 新建一篇笔记

```bash
hugo new posts/my-note.md
```

编辑 `content/posts/my-note.md`，写完后把 front matter 里的 `draft` 改为 `false`，
提交并推送到 `main`，站点会自动更新。

## 目录结构

```
content/posts/    文章（Markdown）
content/about.md  关于页
hugo.toml         站点配置：标题、菜单、主题参数
assets/img/       头像等参与构建的图片
static/           直接拷贝到站点根目录的静态文件
layouts/          对主题局部覆盖的模板
themes/blowfish/  主题（git submodule）
```

更详细的开发说明见 [AGENTS.md](AGENTS.md)。

## 许可

笔记文字版权归作者所有，转载请注明出处。
主题 Blowfish 采用 [MIT 许可](https://github.com/nunocoracao/blowfish/blob/main/LICENSE)。
