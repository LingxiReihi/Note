# React相关

## 从0开始安装Vite与React

### Vite安装

在当前项目文件夹中，执行以下命令可以将Vite安装到当前项目中：

```powershell
npm install -D vite
```

安装完成后，项目中会出现一个`node_modules`文件夹，他会包含`vite`包及其依赖包，以及后续可能安装的包，通常不需要对其进行太多的管理。除此之外还会出现一个`package-lock.json`项目包配置文件，并且原本的`package.json`会增加以下一段：

```json
"devDependencies": {
    "vite": "^8.2.1"
},
```

而`package-lock.json`文件夹中会出现`vite`包的详细配置文件。

### Vite开发使用及打包

安装好`Vite`后，可以使用以下命令运行`Vite`，实现编码时页面热更新：

```powershell
./node_modules/.bin/vite
./node_modules/.bin/vite dev
./node_modules/.bin/vite build
```

我们也可以在`package.json`中添加以下内容，实现通过`npm`指令快速运行以上指令：

```json
"scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
}
```

此时就可以在命令行中执行以下指令代替上面的一长串指令：

```powershell
npm run dev			# 开发模式
npm run build		# 构建打包
npm run preview		# 以构建包预览
```

此时项目中增加了许多可以通过指令重新安装的内容，以及打包出来的文件是可以通过`build`指令重新生成，这些内容是可以不用上传到远程库中的，所以可以在`.gitignore`中加入以下两个文件夹：

```
dist
node_modules
```

在下一次拉取到这个项目时，使用`npm`下载包文件即可将所需依赖包全部下载下来：

```powershell
npm install
```

## 数据驱动界面

## Next.js

### 什么是Next.js

浏览器请求网页的过程中，因为我们的项目打包后只有一个`index.html`文件，渲染时需要先通过该文件请求下载对应的`css`和`js`文件后才可以正常渲染网页，当网页比较大的时候，这种渲染方式会导致很长时间的白屏（首屏慢），并且因为只有一个没有什么内容的`html`文件，所以搜索引擎在爬虫获取到我们网站内容（[SEO](https://baike.baidu.com/item/搜索引擎优化/3132)）时无法获取到完整的信息，导致搜索引擎可能不会对我们的网站进行推送。

而`Next.js`则是为了解决这一问题而产生的，它可以实现直接通过网址访问不同的页面，同时可以将页面预先渲染成真实的HTML，解决获取页面404、首屏慢及SEO差的问题。

