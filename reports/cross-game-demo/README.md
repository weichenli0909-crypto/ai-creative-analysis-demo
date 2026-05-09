# 🎮 跨游戏交叉分析 Demo

本案例展示 **跨游戏对比看板** 的形态。当前只有 1 款游戏（Age of Empires Mobile，300 条素材合并），主要作为 4 Tab 布局和未来扩展的演示。

## 分析思路

传统买量分析都是"同一款游戏内"的切分（国家 × 平台 × 时间），看不到**行业全景**。当同一研发/发行手里同时运营 SLG/4X/末日等多款产品，或者想系统性追踪竞品时，需要一个**跨游戏对比视图**：

1. 哪款游戏在哪个国家/平台投得最狠？赛道分布？（大盘矩阵）
2. 每款游戏的 Hook 卖点、CTA 福利、口播语气各自靠什么？（堆叠对比）
3. 视觉场景、素材结构、情绪曲线的差异在哪里？
4. **最关键**：是否存在"同一套爆款脚本被多款游戏复用"的现象？

## 技术实现

- **数据合并**：扫描多份 `AI素材分析_*/分析结果_raw.json`，按统一 schema 合并
- **游戏名识别**：从文件名/子文件夹/相对路径自动抽取，内置常见 SLG 别名映射词典（AOE Mobile、ROK、SoS、Last War、Whiteout Survival、Evony...）
- **跨游戏剧本相似度**：对「完整台词」做 3-gram Jaccard 相似度比对，≥15% 即视为同剧本复用（天然跳过同游戏内部的同款）
- **单游戏降级**：只有 1 款游戏时其它 Tab 正常，剧本复用 Tab 提示"加一款游戏即自动启用"

## 如何扩展

```bash
# 分析每款游戏后产出的 AI素材分析_xxx/ 目录，自动合并
python3 cross_game_analyze.py
# 或手动指定若干份
python3 cross_game_analyze.py \
  "/桌面/AI素材分析_AOE_2026xxxx" \
  "/桌面/AI素材分析_ROK_2026xxxx" \
  "/桌面/AI素材分析_SoS_2026xxxx"
```

看板会在 `~/Desktop/跨游戏对比看板_时间.html` 生成，无外链、纯本地 HTML，可直接分享。

脚本源码：[`cross_game_analyze.py`](https://github.com/weichenli0909-crypto/korean-video-analyzer)

---

## 4 个 Tab 说明

| Tab | 内容 |
|-----|------|
| 📊 大盘 | 游戏 × 国家 / 游戏 × 平台 / 游戏 × 赛道 三张热力矩阵 + KPI |
| 🎯 Hook / CTA | 每款游戏的 Top Hook 卖点、CTA 福利、口播语气 堆叠条 |
| 🎨 视觉 / BGM / 情绪 | 场景、素材结构、情绪曲线 跨游戏分布 |
| 🧬 跨游戏剧本复用 | 同剧本 Top 30 配对（左右并排原文 + 国家 + 文件名 + 相似度）|

---

**数据来源**：Age of Empires Mobile（美 / 日 / 韩，2024.10 - 2025.06）AdMob + Facebook + Instagram + YouTube 共 300 条素材合并
