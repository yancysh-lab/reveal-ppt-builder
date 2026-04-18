# 项目修订日志

## 2026-04-16

### 1. 大纲模式 Markdown 解析规则优化 (`OutlineEditor.tsx`)

**问题**: 解析大纲时无法正确选择布局模板，所有 `#` 开头的都被当作"标题页"，丢失了正文内容。

**修复**:
- 定义 Markdown 语法规则：
  - `# 标题` → 标题页（无正文时为 `title`，有正文自动改为 `title-body`）
  - `## 标题` → 标题+副标题布局（默认 `title-subtitle`）
  - `### 副标题` → 设置副标题内容
  - `- 文字` → 识别为正文要点（构建数组 body）
  - `> 图片: 关键词` → 设为 image-left 布局
  - `> 引用: 名言` → 设为 quote 布局
  - `> 布局: 类型` → 强制指定布局
- 新增 `determineLayout()` 函数，根据内容自动选择布局：
  - 有图片 → `image-left`
  - 有正文 → `title-body`
  - 有副标题 → `title-subtitle`
  - 否则 → `title`

**文件**: `src/components/OutlineEditor.tsx`

---

### 2. 正文列表渲染修复 (`OutlineEditor.tsx` + `exporter.ts`)

**问题**: `-` 开头的行没有正确换行，都连成了一行。

**修复**:
- 解析时检测是否包含 `-` 开头的内容，设置 `hasBulletItems = true`
- 如果有 bullet items，将 body 存为 `string[]` 数组
- 导出器判断 body 是否为数组，分别渲染 `<ul><li>...</li></ul>` 或 `<p>`

**文件**:
- `src/components/OutlineEditor.tsx`
- `src/lib/exporter.ts`

---

### 3. 逐页模式同步到预览窗口 (`App.tsx` + `PreviewContainer.tsx`)

**问题**: 点击左侧页面列表，右侧预览窗口不会同步切换到对应页面。

**修复**:
- 传入 `selectedSlideId` 到 `PreviewContainer` 组件
- 使用 `key` 属性强制在选中页面变化时重新初始化
- 添加 `useEffect` 监听 `selectedSlideId` 变化
- 调用 Reveal.js 的 `slide(index)` API 切换页面
- 添加 100ms 延迟确保 Reveal.js 初始化完成

**文件**:
- `src/App.tsx`
- `src/components/PreviewContainer.tsx`

---

### 4. Vite 开发服务器配置 (`vite.config.ts`)

**为 WSL 环境配置**:
- 设置 host 为 `0.0.0.0` 允许外部访问
- 固定端口 5173

**文件**: `vite.config.ts`

---

### 修改文件清单

| 文件 | 修改类型 |
|------|----------|
| src/App.tsx | 修改 |
| src/components/OutlineEditor.tsx | 大幅修改 |
| src/components/PreviewContainer.tsx | 修改 |
| src/components/SlideEditor.tsx | （之前已存在）|
| src/lib/exporter.ts | 修改 |
| src/store/index.ts | 修改 |
| vite.config.ts | 修改 |