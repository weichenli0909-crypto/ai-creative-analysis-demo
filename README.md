# 🎬 AI Creative Analysis · Demo Reports

> 这是一个**只放报告交付物**的静态站点仓库，用于通过 GitHub Pages 在任何设备上查看 AI 广告素材分析的真实输出。
>
> 工具源码（私有）：[weichenli0909-crypto/korean-video-analyzer](https://github.com/weichenli0909-crypto/korean-video-analyzer)

## 🌐 在线访问

部署地址：<https://weichenli0909-crypto.github.io/ai-creative-analysis-demo/>

## 📂 目录

```
.
├── index.html                              ← 首页（报告索引卡片）
├── reports/
│   └── 2026-05-09-aoe-mobile-3countries/
│       ├── dashboard.html                  ← 🌐 交互看板（筛选/搜索/画廊/情绪曲线）
│       ├── cross-country-insight.md        ← 🧠 跨国文化归因（2500字）
│       ├── presentation.md                 ← 📝 汇报稿
│       ├── weekly-report.md                ← 📊 运营周报
│       ├── top-replicas.txt                ← 🔥 Top 复刻清单
│       ├── report.xlsx                     ← 📘 Excel 详表（30+字段/条）
│       └── README.md                       ← 📖 案例说明
```

## 🔄 新增报告

每次有新分析要发布时：

```bash
# 1. 复制输出目录到 reports/ 下（用英文目录名）
cp -r ~/Desktop/AI素材分析_XXX reports/2026-XX-XX-game-countries/

# 2. 重命名中文文件名为英文（交互看板→dashboard.html 等）
# 3. 在 index.html 加一个 .report-card 块
# 4. git add & commit & push

git add . && git commit -m "add report: XXX" && git push
```

几分钟后 GitHub Pages 自动更新。

## 🔐 隐私说明

- 本仓库**公开**，但仓库内容仅包含对**公开可见广告素材**的 AI 分析结果
- 不包含任何：API key、工具源码、内部数据、账号信息
- 工具本体放在私有仓库里
