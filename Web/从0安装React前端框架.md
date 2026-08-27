# 从0安装React前端框架

### 什么是React

React是一个前端框架，他与Vue类似，都是基于“组件”“状态”“数据驱动界面”等概念进行设计。使用React框架进行前端编写，除了安装React之外还需要安装构建框架。

### React安装及Vite的中React构建插件安装

在项目的根目录执行：

```powershell
npm install react react-dom
```

继续安装构建插件：

```powershell
npm install -D @vitejs/plugin-react
```

安装后需要添加`vite.config.js`才可以生效：

```js
// vite.config.js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
```



