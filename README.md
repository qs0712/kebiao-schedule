# 课表提醒 - IQ WATCH GT

一款专为 **IQ WATCH GT**（1.85寸 / 390×450px / 方表）设计的蓝河系统（BlueOS）手表应用，自动提醒每日课程。

## 功能

- **课表主页** — 按星期查看当日课程，左右切换星期
- **真实序号** — 自动匹配上课时段，显示 1~4 序号（两节课一组）
- **2×2 信息卡** — 课程名 | 教室 · 时间 | 老师，一目了然
- **课前提醒** — 每分钟后台检查，课前 N 分钟推送通知 + 震动
- **可调提醒时间** — 5 / 10 / 15 / 30 分钟可选
- **OrbitV 一键同步** — 手机端编辑课表，点一下同步到手表
- **网络下载导入** — 手机开 HTTP Server 直接拉取
- **粘贴导入** — 手机编辑器生成 JSON 后粘贴到手表

## 截图

主页 | 设置
:---:|:---:
![主页](screenshots/home.png) | ![设置](screenshots/settings.png)

## 技术栈

- **平台**: BlueOS（蓝河操作系统）
- **开发**: UX 应用 (HTML + CSS + JavaScript)
- **工具**: BlueOS SDK-1.1.0 / BlueOS Studio
- **构建**: `npm run build` 或 `bot build`

## 项目结构

```
kebiao-schedule/
├── src/
│   ├── app.ux                 # 应用入口 + 后台定时提醒
│   ├── manifest.json          # 应用配置
│   └── pages/
│       ├── Schedule/          # 主页 - 课表列表
│       └── Settings/          # 设置 - 提醒/同步/导入
├── phone_course_editor.html   # 手机课表编辑器
├── package.json
└── jsconfig.json
```

## 使用方法

### 从手机同步课表（推荐）

1. 手机打开 `phone_course_editor.html`，添加课程
2. 点击「生成课表 → 下载到手机」，保存 `courses.json`
3. **方式一**: OrbitV 用户 → 手机打开 OrbitV，导入 `courses.json`→ 手表点「从 OrbitV 拉取」
4. **方式二**: 装 Simple HTTP Server → 选 Download 目录启动 → 手表输入地址下载
5. **方式三**: 复制 JSON → 手表粘贴导入

### 支持的课程数据格式

```json
[
  {
    "name": "高等数学",
    "dayOfWeek": 1,
    "startTime": "08:00",
    "endTime": "08:45",
    "location": "A101",
    "teacher": "张老师",
    "color": "#4CAF50"
  }
]
```

`dayOfWeek`: 1=周一 … 7=周日

### 上课时间表

| 节次 | 序号 | 时间 |
|------|:---:|------|
| 第1节 | 1 | 08:00 - 08:45 |
| 第2节 | 1 | 08:55 - 09:40 |
| 第3节 | 2 | 10:20 - 11:05 |
| 第4节 | 2 | 11:15 - 12:00 |
| 第5节 | 3 | 14:30 - 15:15 |
| 第6节 | 3 | 15:25 - 16:10 |
| 第7节 | 4 | 16:25 - 17:10 |
| 第8节 | 4 | 17:15 - 18:00 |

## 版本历史

| 版本 | 说明 |
|------|------|
| v1.0.0 | 初始版本 |
| v1.1.0 | 精简页面、OrbitV 同步、课程序号映射、UI 优化 |

## 作者

**吃不饱的小乔**

---

*Built with BlueOS SDK-1.1.0*