# zero-to-tech-4-5 · Next.js 版（模块 4.5 配套代码）

4.5 的终点成品：把 4.4 的 React 项目整体搬到 Next.js。网站长相不变；变的是路由层（手搓 `useRoute` → 文件夹路由）和入口（`index.html` + `main.jsx` + `App.jsx` → `app/`）。

## 跑起来

```bash
pnpm install
pnpm dev          # http://localhost:3000   （Next 默认端口是 3000）
```

生产构建使用 `pnpm build`，生成的静态站点位于 `out/`，可由 Nginx 提供访问。GitHub Actions 会在推送和拉取请求时检查静态构建；当前不包含自动部署。
`zero-to-tech-demos/` 是独立的学习资料目录，不随本仓库提交；可以按需单独克隆：

```bash
git clone https://github.com/joylibo/zero-to-tech-demos.git
```

## 项目结构

```
app/                     ← 文件夹 = 路由
  layout.jsx             ← 全站外壳（页面包裹 + import 8 个 css）
  page.jsx               ← /         → 渲染 <HomeView />
  text-lab/page.jsx      ← /text-lab → 渲染 <TextLabView />
components/
  Nav.jsx                ← <Link> + usePathname（"use client"）
  HomeView.jsx           ← 4.4 的 HomePage 改名
  TextLabView.jsx        ← 4.4 的 TextLabPage 改名
  PageHeading.jsx        ← 同 4.4
  InputCard.jsx          ← 同 4.4（"use client"）
  ResultCard.jsx         ← 同 4.4（"use client"）
  AnimatedCardGrid.jsx   ← 同 4.4（"use client"）
css/                     ← 8 个 css，同 4.4
data/site.js             ← 同 4.4
next.config.mjs          ← 配置静态导出
```

相比 4.4，没了 `index.html`、`src/main.jsx`、`src/App.jsx`、`src/router/useRoute.js`——这一坨被 `app/` 取代了。
