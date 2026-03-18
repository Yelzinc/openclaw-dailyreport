# AI 技术行业日报 - 自动存档系统

## 📋 功能说明

每天上午 9:00（香港时间）自动执行：

1. **收集 AI 新闻** - 从多个来源获取最新 AI 动态
2. **发送 Telegram** - 推送到用户的 Telegram 账号
3. **本地存档** - 保存 markdown 文件到 workspace
4. **GitHub 同步** - 自动推送到 GitHub 仓库

## 📁 存档位置

### 本地存档
```
/root/.openclaw/.openclaw/workspace/archives/ai-news/
├── ai-news-2026-03-12.md
├── ai-news-2026-03-13.md
└── ...
```

### GitHub 仓库
- **仓库地址**: https://github.com/Yelzinc/openclaw-backup
- **存档目录**: `archives/ai-news/`
- **可见性**: 私有仓库

## 🔧 配置文件

### Cron 任务
- **任务 ID**: `6c644468-f4bb-4598-85a8-9df081049e79`
- **任务名称**: AI 新闻每日播报
- **执行时间**: 每天 9:00 (Asia/Hong_Kong)
- **超时设置**: 120 秒

### 查看任务状态
```bash
openclaw cron list
openclaw cron status "6c644468-f4bb-4598-85a8-9df081049e79"
```

## 📊 新闻来源

1. **GitHub Trending** - AI/ML 热门开源项目
2. **The Verge AI** - 国际 AI 科技新闻
3. **TechCrunch AI** - AI 创业与融资动态
4. **百度搜索** - 国内 AI 热点话题

## 🛠️ 手动操作

### 手动触发任务
```bash
openclaw cron run "6c644468-f4bb-4598-85a8-9df081049e79"
```

### 手动存档（测试用）
```bash
cd /root/.openclaw/.openclaw/workspace
python3 scripts/archive_ai_news.py
```

### 查看本地存档
```bash
ls -lh /root/.openclaw/.openclaw/workspace/archives/ai-news/
cat /root/.openclaw/.openclaw/workspace/archives/ai-news/ai-news-$(date +%Y-%m-%d).md
```

### 手动推送到 GitHub
```bash
cd /root/.openclaw/.openclaw/workspace
git add archives/ai-news/
git commit -m "docs: 添加 AI 日报存档"
git push
```

## 📝 存档格式

每份日报包含：

```markdown
# AI 技术行业日报

**存档日期**: 2026-03-12 11:00:00
**日报日期**: 2026-03-12

---

# 🤖 AI 技术行业日报

**日期**: 2026 年 3 月 12 日
**来源**: GitHub Trending + The Verge + TechCrunch
**方案**: multi-search-engine（无需 API Key）

---

## 🔥 GitHub 热门 AI 项目（今日）
...

## 📰 国际 AI 动态
...

## 🇨🇳 国内 AI 热点
...

## 📊 统计
...
```

## ⚙️ 配置说明

- ✅ **已配置**: Cron 定时任务（每天 9:00 HKST）
- ✅ **搜索方案**: multi-search-engine（无需 API Key）
- ✅ **发送渠道**: Telegram（当前会话）
- ✅ **报告格式**: 中文摘要 + 原文链接 + 热度统计
- ✅ **GitHub 存档**: 自动推送到 Yelzinc/openclaw-backup
- ⏰ **下次执行**: 明天上午 9:00

## 🔍 故障排查

### 任务未执行
```bash
# 检查 cron 状态
openclaw cron status

# 查看任务列表
openclaw cron list

# 查看执行历史
openclaw cron runs
```

### GitHub 推送失败
```bash
# 检查 GitHub 认证
gh auth status

# 检查 git 状态
cd /root/.openclaw/.openclaw/workspace
git status

# 手动推送
git push origin main
```

### 搜索失败
- 检查网络连接
- 更换搜索引擎（multi-search-engine 支持 17 个引擎）
- 考虑注册 Brave API（免费 1000 次/月）

## 📈 统计信息

- **存档开始日期**: 2026-03-12
- **预计每月存档**: 30 份日报
- **预计每年存档**: 365 份日报
- **单文件大小**: ~5-10 KB
- **年存储需求**: ~2-4 MB

## 🎯 优化建议

1. **定期清理** - 可考虑只保留最近 1 年的日报
2. **月度汇总** - 每月生成一份月度精选
3. **标签分类** - 为日报添加标签（产品、融资、研究等）
4. **搜索优化** - 根据用户反馈调整搜索关键词

---

**最后更新**: 2026-03-12
**维护者**: AI Assistant
