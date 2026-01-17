# AI Resume Builder · 尤佳郁
一个基于 Vite + Vue 3 + Tailwind CSS 打造的深色系、科技感十足的 AI 工程师简历生成器 。 <br/> 支持模块拖拽排序、模板与主题切换、草稿保存、JSON 导出、PDF 打印等功能，并展示了 AI 协作能力与 Prompt Engineering 实战。
 <blockquote/>
## ✨ 功能特性
- 炫酷首页 + 动画
  - 深色渐变背景 + 霓虹高光 + 毛玻璃效果
  - 头部标题支持类似 ChatGPT 的打字机动画
- AI 技能矩阵
  - 展示 Prompt Engineering、AI Agent 开发、大模型 API 调用等能力
  - 使用 Tailwind 实现渐变背景与悬停光晕动画
- 简历模块管理
  - 模块列表可 显示 / 隐藏 / 删除
  - 支持 拖拽排序 ，实时更新预览顺序
  - 支持添加 自定义模块 （补充额外经历 / 技能 / 项目）
- 模板与主题系统
  - 模板切换：AI 深色模板、极简深色模板
  - 主题切换：翡翠绿 / 极光紫 / 霓虹蓝
  - 支持全局 字体族 （Sans / Serif / Mono）与 字号大小 调整
  - 可调节模块间距：紧凑 / 适中 / 宽松
- 内容与交互
  - 头部展示真实个人信息（姓名、政治面貌、意向、联系方式、GitHub）
  - 教育背景、竞赛荣誉、实习经历、项目经历、AI 协作声明等模块
- 数据与导出能力
  - 保存草稿 ：使用 localStorage 自动恢复上次编辑状态
  - 导出 JSON ：导出当前简历配置（模块、排序、主题、头像等）
  - 导出 PDF ：调用浏览器 print ，自动隐藏控制面板，仅导出简历主体
- 自定义头像
  - 上传本地头像，自动显示在简历头部圆形头像框中
## 🧱 技术栈
- 构建工具：Vite
- 前端框架：Vue 3（ <script setup> 语法）
- 样式系统：Tailwind CSS
- 语言：JavaScript
- 其他：
  - localStorage 用于草稿保存
  - 浏览器原生 window.print() 用于 PDF 导出

##  目录结构（核心部分）
```
.
├── index.html
├── package.json
├── vite.config.js
├── postcss.config.js
├── tailwind.config.js
└── src
    ├── main.js          # Vue 入口文件
    ├── App.vue          # 简历编辑器 & 预览核心逻辑
    └── assets
        └── main.css     # Tailwind 引入 + 自定义动画与卡片
        样式
```
## 🚀 本地运行
```
# 安装依赖
npm install

# 开发环境
npm run dev

# 生产构建
npm run build

# 预览构建结果
npm run preview
```
启动开发服务器后，浏览器访问：

```
http://localhost:5173
```
即可看到完整的简历编辑页面。

Builder

思考过程

下面是一份可以直接放到 GitHub 的 README，你可以按需要再微调项目名、截图和 License。

# AI Resume Builder · 尤佳郁
一个基于 Vite + Vue 3 + Tailwind CSS 打造的深色系、科技感十足的 AI 工程师简历生成器 。 <br/> 支持模块拖拽排序、模板与主题切换、草稿保存、JSON 导出、PDF 打印等功能，并展示了 AI 协作能力与 Prompt Engineering 实战。
 <blockquote/>
## ✨ 功能特性
- 炫酷首页 + 动画
  - 深色渐变背景 + 霓虹高光 + 毛玻璃效果
  - 头部标题支持类似 ChatGPT 的打字机动画
- AI 技能矩阵
  - 展示 Prompt Engineering、AI Agent 开发、大模型 API 调用等能力
  - 使用 Tailwind 实现渐变背景与悬停光晕动画
- 简历模块管理
  - 模块列表可 显示 / 隐藏 / 删除
  - 支持 拖拽排序 ，实时更新预览顺序
  - 支持添加 自定义模块 （补充额外经历 / 技能 / 项目）
- 模板与主题系统
  - 模板切换：AI 深色模板、极简深色模板
  - 主题切换：翡翠绿 / 极光紫 / 霓虹蓝
  - 支持全局 字体族 （Sans / Serif / Mono）与 字号大小 调整
  - 可调节模块间距：紧凑 / 适中 / 宽松
- 内容与交互
  - 头部展示真实个人信息（姓名、政治面貌、意向、联系方式、GitHub）
  - 教育背景、竞赛荣誉、实习经历、项目经历、AI 协作声明等模块
- 数据与导出能力
  - 保存草稿 ：使用 localStorage 自动恢复上次编辑状态
  - 导出 JSON ：导出当前简历配置（模块、排序、主题、头像等）
  - 导出 PDF ：调用浏览器 print ，自动隐藏控制面板，仅导出简历主体
- 自定义头像
  - 上传本地头像，自动显示在简历头部圆形头像框中
## 🧱 技术栈
- 构建工具：Vite
- 前端框架：Vue 3（ <script setup> 语法）
- 样式系统：Tailwind CSS
- 语言：JavaScript
- 其他：
  - localStorage 用于草稿保存
  - 浏览器原生 window.print() 用于 PDF 导出
## 📁 目录结构（核心部分）
```
.
├── index.html
├── package.json
├── vite.config.js
├── postcss.config.js
├── tailwind.config.js
└── src
    ├── main.js          # Vue 入口文件
    ├── App.vue          # 简历编辑器 & 预览核心逻辑
    └── assets
        └── main.css     # Tailwind 引入 + 自定义动画与卡片
        样式
```
## 🚀 本地运行
```
# 安装依赖
npm install

# 开发环境
npm run dev

# 生产构建
npm run build

# 预览构建结果
npm run preview
```
启动开发服务器后，浏览器访问：

```
http://localhost:5173
```
即可看到完整的简历编辑页面。

## 🕹 使用说明
### 1. 基本操作流程
1. 启动项目： npm run dev
2. 打开浏览器预览页面
3. 通过顶部控制面板调整模板 / 主题 / 字体 / 间距
4. 使用「模块管理」调整模块顺序、显示状态、添加自定义模块
5. 上传头像、填写/修改模块内容（如有需要可直接在代码中改文案）
6. 完成后：
   - 使用「导出 JSON」备份配置
   - 使用「导出 PDF」得到正式版简历
### 2. 模块管理
- 「模块管理」区展示一个模块列表（教育、荣誉、实习 / 项目、AI 协作、自定义等）
- 每行支持：
  - 拖拽 ：长按左侧“≡”拖动改变顺序
  - 隐藏 / 显示 ：不想展示的模块可以临时隐藏
  - 删除 ：完全移除该模块（可通过添加自定义模块补回）
### 3. 模板与主题设置
- 模板选择 ：
  - AI 工程师 · 深色模板
  - 极简深色模板
- 主题颜色 ：
  - 翡翠绿 （默认）
  - 极光紫
  - 霓虹蓝
- 字体设置 ：
  - Sans / Serif / Mono
- 字号与间距 ：
  - 字号：小 / 中 / 大
  - 模块间距：紧凑 / 适中 / 宽松
### 4. 草稿保存与导出
- 保存草稿 ：
  - 点击「保存草稿」后，当前状态会写入 localStorage
  - 再次打开页面时会自动恢复
- 导出 JSON ：
  - 点击「导出 JSON」，会下载 resume.json
  - 内容包含模板、主题、模块列表、头像 base64 等信息
- 导出 PDF ：
  - 点击「导出 PDF」，调用浏览器打印
  - 控制面板、模块管理等带有 .no-print 的区域会自动隐藏
  - 在打印对话框选择「另存为 PDF」即可
## 🤝 AI 协作说明
本项目在开发过程中，通过 Trae 的 AI Builder 模式与大模型进行深度协作，包括但不限于：

- 简历信息结构设计与模块拆分
- Tailwind CSS 主题体系与动画效果设计
- 动态模块管理、拖拽排序、草稿保存等交互逻辑实现
- 处理脚手架初始化过程中的问题（例如 npm 命名冲突）并进行手动修复
这部分也在页面中以「AI 协作实战声明」模块形式呈现，体现了 Prompt Engineering 能力 与 与 AI 协同开发的实战经验 。

## 🔧 自定义与二次开发
你可以基于本项目做进一步扩展，例如：

- 为模块内容增加在线表单编辑（而不是改代码）
- 支持导入 JSON 恢复配置（与导出 JSON 对应）
- 支持多份简历配置切换（实习版 / 校招版 / 英文版）
- 集成真实的大模型 API，在页面中直接调试 Prompt 和 Agent 工作流

