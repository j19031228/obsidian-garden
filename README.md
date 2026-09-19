# 半导体知识花园（站点源码）

🌐 https://j19031228.github.io/obsidian-garden

这个仓库只放**可以公开**的半导体学习笔记 + 站点构建配置，基于 [Quartz 4](https://quartz.jzhao.xyz/)（MIT）。
私人笔记（求职、项目、日记）放在另一个**私有**仓库 `obsidian-vault` 里，永远不会同步到这里。

## 内容流向

```
私有 vault（D:\Backup\Documents\Obsidian Vault）
   └─ 10-半导体/{概念,公司,每日速览}/**.md  ──sync_garden.py──▶  content/  ──Quartz──▶  public/  ──▶  GitHub Pages
```

同步脚本在本机：`%LOCALAPPDATA%\hermes\work\projects\obsidian-github\sync_garden.py`，
只白名单复制 `10-半导体/` 下的三类笔记，其它目录一律不复制（改白名单就在脚本顶部改 `PUBLIC_SUBTREES`）。

## 本地预览

```bash
npm ci
npx quartz build --serve     # http://localhost:8080
```

## 更新内容

```bash
python "%LOCALAPPDATA%\hermes\work\projects\obsidian-github\sync_garden.py"
git add -A && git commit -m "garden: 同步笔记" && git push
```

推送后 GitHub Actions（`.github/workflows/deploy.yml`）自动构建并发布。
也可以直接在本仓库页面 Actions → Deploy Quartz site → Run workflow 手动重跑。

## 改外观

- `quartz.config.ts`：站点标题、配色、字体（已设 `fontOrigin: "local"`，不依赖 Google Fonts，国内访问不卡）
- `quartz.layout.ts`：页面布局（侧栏、目录、图谱）

---
Based on Quartz v4 by jackyzha0 — docs: https://quartz.jzhao.xyz/
