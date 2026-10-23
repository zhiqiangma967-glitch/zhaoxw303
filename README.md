# 禾间 · 时令餐厅

Vue 3 + Vite + JavaScript 单页餐厅首页。使用 Composition API 与 `<script setup>`。

## 本地开发

建议使用 Node.js 24 LTS。首次安装使用 `npm ci`，随后运行 `npm run dev`。

- `npm run build`：生成 `dist/` 静态产物。
- `npm run preview`：在本地预览生产构建。

## 修改页面

- `src/data/menu.js`：四道菜的名称、价格、分类、食材、风味说明和图片。
- `src/components/`：导航、首屏、菜单、餐厅介绍、预订和页脚组件。
- `src/styles/main.css`：保留原页面顺序的全局样式与移动端规则。
- `src/App.vue`：首页组件编排。

预订表单仅为演示，不发送网络请求，不生成真实订位。日期以访客本地时间计算。

## 发布

保留 `.openai/hosting.json` 中的 Sites 项目 ID，静态目录为 `dist`。通过 Sites 官方安装、构建、源码打包及部署工具发布。不要手工编辑 `dist/`，也不要提交 `node_modules/`。
