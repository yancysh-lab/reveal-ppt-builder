# Reveal.js PPT 风格 HTML 页面生成工具

**项目名称**: reveal-ppt-builder  
**项目类型**: 纯 Web 应用（无需安装，浏览器打开即用）  
**技术栈**: React 19 + TypeScript + Zustand + TailwindCSS + Vite + reveal.js

---

## 功能概述

一个基于 reveal.js 的 PPT 风格 HTML 页面生成工具，提供所见即所得的编辑体验。

### 核心特性

1. **左右分栏编辑** - 左侧编辑、右侧实时预览
2. **双模式编辑** - 大纲模式快速生成 + 逐页模式精细调整
3. **模板系统** - 3 套核心模板（简约白、深色经典、商务蓝）+ 自定义能力
4. **图片支持** - 本地上传 + Unsplash 图库搜索
5. **单文件导出** - 导出自包含 HTML 文件，可离线使用和分享

---

## 快速开始

```bash
# 安装依赖
cd /mnt/c/Users/yancy/reveal-ppt-builder
npm install

# 启动开发服务器
npm run dev

# 构建生产版本
npm run build
```

访问 http://localhost:5173/

---

## 功能模块

### 1. 大纲编辑器
- 使用 Markdown 语法编写大纲
- `#` 标题 = 新建一页幻灯片
- `##` 副标题 = 标题+副标题布局
- `-` 列表项 = 幻灯片要点
- `> 布局:` 指定布局类型
- `> 图片:` 触发 Unsplash 搜索

### 2. 逐页编辑器
- 9 种布局类型可选：
  - 标题页 (title)
  - 标题+副标题 (title-subtitle)
  - 标题+正文 (title-body)
  - 全屏图片 (image-full)
  - 左图右文 (image-left)
  - 右图左文 (image-right)
  - 双栏布局 (two-column)
  - 引言样式 (quote)
  - 空白页 (blank)
- 支持编辑：标题、副标题、正文、图片、背景色

### 3. 预览模块
- reveal.js 实时预览
- 页面切换导航
- 实时反映编辑内容

### 4. 模板系统
- 3 套预设模板
- 自定义颜色、字体、字号
- 页面切换效果选择（无/滑动/淡入/凸出/凹陷/缩放）

### 5. 导出功能
- 单文件 HTML 导出
- Google Fonts 内嵌
- 图片 Base64 内嵌

---

## 文件结构

```
reveal-ppt-builder/
├── src/
│   ├── components/
│   │   ├── AppLayout.tsx       # 基础布局容器
│   │   ├── Toolbar.tsx         # 顶部工具栏
│   │   ├── OutlineEditor.tsx   # 大纲编辑器
│   │   ├── SlideEditor.tsx     # 逐页编辑器
│   │   ├── SlideList.tsx       # 幻灯片列表
│   │   ├── PreviewContainer.tsx # 预览容器
│   │   └── TemplateCustomizer.tsx # 模板自定义
│   ├── store/
│   │   └── index.ts            # Zustand 状态管理
│   ├── types/
│   │   └── index.ts            # TypeScript 类型定义
│   ├── templates/
│   │   └── presets.ts          # 模板预设配置
│   ├── layouts/
│   │   └── index.ts            # 布局类型配置
│   ├── lib/
│   │   ├── db.ts               # IndexedDB 存储
│   │   └── exporter.ts        # HTML 导出器
│   ├── App.tsx                 # 应用主组件
│   ├── main.tsx                # 入口文件
│   └── index.css               # 全局样式
├── package.json
├── vite.config.ts
├── tsconfig.json
└── README.md
```

---

## 依赖列表

| 依赖 | 版本 | 用途 |
|------|------|------|
| react | ^19.2.4 | UI 框架 |
| zustand | ^5.0.12 | 状态管理 |
| reveal.js | ^6.0.1 | 演示框架 |
| tailwindcss | ^4.2.2 | 样式框架 |
| @dnd-kit | ^10.0.0 | 拖拽排序 |
| idb | ^8.0.3 | IndexedDB 封装 |
| uuid | ^13.0.0 | ID 生成 |

---

## 开发进度

- [x] 项目初始化与基础框架
- [x] 大纲编辑器 (Markdown 解析)
- [x] 逐页编辑器 (9 种布局)
- [x] 幻灯片列表 (拖拽排序)
- [x] 实时预览 (reveal.js)
- [x] 模板系统 (3 套核心模板)
- [x] 模板自定义面板
- [x] 页面切换效果选项
- [x] HTML 导出功能
- [ ] 双栏布局支持
- [ ] 引言布局支持
- [ ] 空白页布局支持
- [ ] 优化预览显示效果

---

## 已知问题

1. ~~大纲模式下输入文本后，点击"解析大纲"按钮无反应~~ - 已修复
2. ~~右侧预览界面显示偏移~~ - 部分修复，可能还需调整
3. ~~逐页模式下无法编辑文字~~ - 已支持
4. ~~无页面切换效果选项~~ - 已添加

---

## 许可证

MIT