# 危化品门户 (Hazmat Portal)

一个现代化的危险化学品管理门户网站，基于 Vue 3 + TypeScript + Tailwind CSS 构建。

## 🚀 项目特性

- **现代化技术栈**: Vue 3 + TypeScript + Vite
- **响应式设计**: 基于 Tailwind CSS 的移动端优先设计
- **组件化架构**: 使用 Vue 3 Composition API
- **路由管理**: Vue Router 4 单页面应用
- **状态管理**: Pinia 状态管理
- **图标系统**: Heroicons + Lucide Vue 图标库
- **无障碍设计**: Headless UI 组件库
- **代码规范**: ESLint + TypeScript 严格模式

## 📦 技术栈

### 核心框架
- [Vue 3](https://vuejs.org/) - 渐进式 JavaScript 框架
- [TypeScript](https://www.typescriptlang.org/) - JavaScript 的超集
- [Vite](https://vitejs.dev/) - 下一代前端构建工具

### UI 和样式
- [Tailwind CSS](https://tailwindcss.com/) - 实用优先的 CSS 框架
- [Headless UI](https://headlessui.com/) - 无样式的可访问 UI 组件
- [Heroicons](https://heroicons.com/) - 精美的 SVG 图标
- [Lucide Vue](https://lucide.dev/) - 简洁的图标库

### 路由和状态
- [Vue Router](https://router.vuejs.org/) - Vue.js 官方路由
- [Pinia](https://pinia.vuejs.org/) - Vue 状态管理库

## 🛠️ 开发环境要求

- Node.js >= 18.0.0
- npm >= 8.0.0 或 yarn >= 1.22.0

## 📥 安装和运行

### 1. 克隆项目

```bash
git clone https://github.com/lengmodkx/hazmat-portal.git
cd hazmat-portal
```

### 2. 安装依赖

```bash
npm install
# 或
yarn install
```

### 3. 启动开发服务器

```bash
npm run dev
# 或
yarn dev
```

访问 [http://localhost:5173](http://localhost:5173) 查看应用。

### 4. 构建生产版本

```bash
npm run build
# 或
yarn build
```

### 5. 预览生产版本

```bash
npm run preview
# 或
yarn preview
```

## 📁 项目结构

```
hazmat-portal/
├── public/                 # 静态资源
│   └── favicon.ico
├── src/
│   ├── assets/            # 资源文件
│   │   └── main.css       # 全局样式
│   ├── components/        # 可复用组件
│   │   ├── Footer.vue     # 页脚组件
│   │   └── Navbar.vue     # 导航栏组件
│   ├── router/            # 路由配置
│   │   └── index.ts
│   ├── stores/            # Pinia 状态管理
│   ├── views/             # 页面组件
│   │   ├── HomeView.vue   # 首页
│   │   ├── ProductsView.vue # 产品展示
│   │   ├── SafetyView.vue   # 安全信息
│   │   ├── AboutView.vue    # 关于我们
│   │   └── ContactView.vue  # 联系我们
│   ├── App.vue            # 根组件
│   └── main.ts            # 应用入口
├── index.html             # HTML 模板
├── package.json           # 项目配置
├── tailwind.config.js     # Tailwind 配置
├── tsconfig.json          # TypeScript 配置
└── vite.config.ts         # Vite 配置
```

## 🎯 功能模块

### 主要页面
- **首页**: 展示公司概况和核心服务
- **产品展示**: 危化品产品目录和详细信息
- **安全信息**: 安全规范、应急处理和培训资料
- **关于我们**: 公司介绍、资质证书和发展历程
- **联系我们**: 联系方式、在线咨询和地理位置

### 核心特性
- 响应式设计，支持移动端和桌面端
- 现代化的用户界面和交互体验
- 快速的页面加载和流畅的动画效果
- 无障碍访问支持
- SEO 友好的页面结构

## 🔧 开发脚本

```bash
# 开发服务器
npm run dev

# 类型检查
npm run type-check

# 代码检查和修复
npm run lint

# 构建生产版本
npm run build

# 仅构建（不进行类型检查）
npm run build-only

# 预览生产版本
npm run preview
```

## 🎨 样式和主题

项目使用 Tailwind CSS 进行样式管理，支持：
- 自定义颜色主题
- 响应式断点
- 暗色模式支持（可扩展）
- 组件级样式封装

## 📱 浏览器支持

- Chrome >= 87
- Firefox >= 78
- Safari >= 14
- Edge >= 88

## 🤝 贡献指南

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 👨‍💻 作者

- **lengmodkx** - [GitHub](https://github.com/lengmodkx)

## 🙏 致谢

感谢以下开源项目：
- [Vue.js](https://vuejs.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Vite](https://vitejs.dev/)
- [TypeScript](https://www.typescriptlang.org/)

---

如有问题或建议，请提交 [Issue](https://github.com/lengmodkx/hazmat-portal/issues) 或联系作者。