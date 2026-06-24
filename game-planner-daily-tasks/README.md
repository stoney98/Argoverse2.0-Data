# 游戏策划 · 每日任务清单

一个纯前端的本地任务管理网页，专为游戏策划日常工作设计。数据保存在浏览器 localStorage 中，无需联网、无需后端。

## 使用方法

直接用浏览器打开 `index.html` 即可：

```bash
# macOS
open index.html

# Windows
start index.html

# Linux
xdg-open index.html
```

也可以在项目目录启动一个本地静态服务器：

```bash
cd game-planner-daily-tasks
python3 -m http.server 8080
# 然后访问 http://localhost:8080
```

## 功能

- **每日任务管理**：按日期切换，添加、完成、删除任务
- **策划分类**：系统设计、数值策划、关卡设计、文案剧情、UI/UX、战斗设计、活动策划、文档输出、会议沟通等
- **优先级**：高 / 中 / 低
- **统计面板**：今日完成进度、分类统计、本周概览
- **本地持久化**：自动保存到 localStorage
- **导入 / 导出**：支持 JSON 备份与恢复

## 数据存储

所有数据保存在浏览器 `localStorage`，键名为 `game-planner-daily-tasks`。清除浏览器数据会导致任务丢失，建议定期使用「导出 JSON」备份。
