# 乘法星球 · 口诀大冒险（GitHub Pages / iPad 版）

这是可以直接部署到 GitHub Pages 的版本。已加入 PWA 配置，iPad 用 Safari 打开后可以 **添加到主屏幕**，像 App 一样全屏运行，并在首次加载后离线使用。

> 如果拿到的是 `.zip` 压缩包，请先解压，再把解压出来的文件和 `icons` 文件夹一起上传到仓库根目录；不要只把 zip 文件放进仓库。

## 文件说明

请把下面这些文件放到**仓库根目录**，并保留 `icons` 文件夹：

```text
index.html
manifest.json
sw.js
icons/
  icon-192.png
  icon-512.png
  icon-maskable-512.png
  apple-touch-icon.png
README.md
```

> `index.html` 必须在仓库根目录。不要把整个 `github-pages` 文件夹原样上传成子文件夹，否则网址会变成 `https://用户名.github.io/仓库名/github-pages/`。

## 上传到 GitHub Pages

1. 新建一个 **Public** 仓库，例如 `multiplication-planet`。
2. 在仓库首页选择 **Add file → Upload files**，把本文件夹里的文件（含 `icons` 文件夹）上传到仓库根目录，提交到 `main` 分支。
3. 打开仓库的 **Settings → Pages**。
4. 在 **Build and deployment** 中：
   - Source 选择 **Deploy from a branch**
   - Branch 选择 **main**
   - Folder 选择 **/ (root)**
   - 点击 **Save**
5. 等待 1～2 分钟，访问：

   `https://你的用户名.github.io/仓库名/`

   例如：`https://xiaoming.github.io/multiplication-planet/`

## 在 iPad 上安装

1. 用 **Safari** 打开上面的网址。
2. 点 Safari 工具栏的 **分享** 按钮。
3. 选择 **添加到主屏幕**，名称会显示为「乘法星球」。
4. 以后从主屏幕图标打开即可，全屏运行。

首次打开需要联网加载，之后 Service Worker 会缓存页面，支持离线打开。

## 学习数据

- 星星、错题统计和历史记录保存在这台 iPad 的 Web App 本地存储中。
- 同一个主屏幕图标长期使用，数据通常会保留在这台 iPad 上。
- 清除浏览器网站数据、删除主屏幕图标或更换域名，可能导致记录丢失。
- 这是正常现象，游戏本身不联网、不上传任何学习数据。

## 更新游戏

替换 `index.html` 后，把 `sw.js` 第一行的缓存版本改一下，例如：

```js
var CACHE_NAME = "multiply-planet-v2";
```

重新上传这两个文件。iPad 上首次打开可能仍是旧版，再打开一次就会更新；必要时删除主屏幕图标后重新添加。

## 常见问题

**打开后没有图标或不能离线？**
- 确认是通过 `https://` 访问 GitHub Pages，而不是直接双击本地文件。
- 确认 `manifest.json`、`sw.js` 和 `icons` 文件夹都已上传。
- 第一次打开后停留几秒，让 Service Worker 完成安装，再添加到主屏幕。

**添加主屏幕后没有全屏？**
- 必须使用 Safari 的「添加到主屏幕」，不要用其他浏览器的普通书签。

**声音/朗读没有？**
- 先点一下页面，让浏览器允许播放声音。
- 中文朗读依赖 iPad 系统自带的中文语音；没有语音时不影响答题。
