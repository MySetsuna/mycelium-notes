# 发布包 (Mycelium Publish Bundle)

这个文件夹由 `mycelium publish` 生成，包含**已通过脱敏门禁**的可公开笔记。

## 内容

- `content/` —— 选中的 Markdown 笔记（日报 / 周报 / 技术总结 / 决策），保留 YAML frontmatter。
- `.github/workflows/deploy.yml` —— 用 Quartz 构建并部署到 GitHub Pages 的 Actions 工作流。

## 脱敏门禁

`mycelium publish` 在导出前对每篇笔记跑了一遍高置信度密钥扫描（私钥 / AWS / GitHub / Slack token / `secret=…` 赋值 / bearer）。**有发现就阻断导出**，除非显式 `--force`。

> 这是第一道防线。正式公开前，强烈建议再跑一遍 [`gitleaks`](https://github.com/gitleaks/gitleaks)（`docs/RESEARCH.md` 推荐）做全量扫描：
> ```bash
> gitleaks dir content --redact --report-format json
> ```

## 发布到 GitHub Pages

1. 新建一个 GitHub 仓库（如 `my-dev-notes`）。
2. 把本文件夹内容推上 `main` 分支。
3. 仓库 Settings → Pages → Source 选 **GitHub Actions**。
4. 推送即触发 `deploy.yml`：克隆 Quartz → 注入 `content/` → 构建 → 部署。

> 备选 SSG：Zola（Rust 单文件）速度更快，但需要把 YAML frontmatter 转成 TOML `+++`；Astro 主题更精致但需 Node 构建。Quartz 因直接吃 YAML frontmatter、自带图谱/反链/搜索，与 Mycelium 笔记最契合。
