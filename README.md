# 🌌 Simple 3D Panorama Viewer (HTML + Three.js)

一个轻量级、无需构建工具、单页面的 3D 全景图查看器。基于 Three.js 开发，支持多场景切换、平滑的惯性拖拽和滚轮视场缩放。

> PS: 目前只支持 6 张图的全景照片，即前、后、左、右、上、下

**如果这个项目对你有帮助，请右上角点个 Star ⭐ 支持一下！谢谢！**

## ✨ 特性

- 🚀 **零依赖安装**：通过 CDN (npmmirror) 引入资源，打开即用。
- ⚙️ **配置简单**：通过 JSON 配置多个场景。
- 🎮 **极致手感**：优化了拖拽惯性、旋转速度，支持鼠标滚轮改变 FOV（视野范围），体验接近专业漫游软件。
- 📱 **全屏适配**：自动适应浏览器窗口大小。

## 📂 目录结构

在使用前，请确保你的文件目录结构如下：

```text
Project/
│
├── index.html          <-- 主程序文件
├── README.md           <-- 说明文档
│
└── scenes/             <-- 存放全景图片的文件夹
    ├── scene1/         <-- 场景1
    │   ├── pano_f.jpg  (前)
    │   ├── pano_b.jpg  (后)
    │   ├── pano_l.jpg  (左)
    │   ├── pano_r.jpg  (右)
    │   ├── pano_u.jpg  (上)
    │   ├── pano_d.jpg  (下)
    │
    ├── scene2/         <-- 场景2
    │   └── ...
```

## 🛠️ 如何获取全景图片 (F12 大法)

如果你手头没有全景图切片，可以去一些主流的全景漫游网站（如 720yun、贝壳看房等）“提取”素材用于学习测试。

1.  **打开浏览器开发者工具**：
    在全景图网页上，按键盘 `F12` (或右键 -> 检查)。
2.  **切换到 Network 面板**：
    点击顶部的 `Network` (网络) 标签。
3.  **筛选图片**：
    在筛选栏选择 `Img`，或者在搜索框输入 `.jpg`。
4.  **寻找切片**：
    转动全景图的视角，你会看到网络请求中加载了很多图片。寻找代表 6 个方位的图片，通常文件名中包含如下字符：
    - `f` (Front / 前)
    - `b` (Back / 后)
    - `l` (Left / 左)
    - `r` (Right / 右)
    - `u` (Up / 上)
    - `d` (Down / 下)
5.  **保存并重命名**：
    右键图片 -> `Open in new tab` -> 保存到你的 `scenes/xxx/` 文件夹下，并按照代码中的约定重命名（例如 `pano_f.jpg`）。

> **提示**：如果发现查看器里前后颠倒或上下颠倒，请调整 `index.html` 代码中 `fileOrder` 数组的顺序，或者直接交换文件名。

## 🚀 快速开始

由于浏览器的 CORS 安全策略，**不能**直接双击 `index.html` 打开，否则图片无法加载。你需要一个本地服务器。

### 方法 1：使用 VS Code (推荐)

1.  安装插件 **Live Server**。
2.  在 `index.html` 上右键，选择 **"Open with Live Server"**。

### 方法 2：使用 Python

打开终端进入项目目录，运行：

```bash
# Python 3.x
python -m http.server
```

然后访问 `http://localhost:8000`。

### 方法 3：使用 Node.js

```bash
npm install -g http-server
http-server
```

## ⚙️ 自定义配置

打开 `index.html`，找到 `scenesConfig` 区域即可添加或修改场景：

```javascript
const scenesConfig = [
  {
    id: "scene1",
    name: "主卧",
    path: "./scenes/scene1/", // 别忘了最后的斜杠
  },
  // ... 添加更多
];
```

## 🤝 贡献与支持

这是一个纯静态的 Demo 项目，欢迎 贡献 Pull request。

**最后，别忘了点亮上方的小星星 ⭐ (Star)，这是我更新的动力！**
