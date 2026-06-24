<div align="center">

# <image src="assets/icon.png" height="35"/> 𝑺𝒊𝒅𝒆𝑭𝒍𝒐𝒘 · 𝑴𝒂𝒈𝒊𝒄𝑾𝒆𝒃

来自 𝙋𝙧𝙤𝙟𝙚𝙘𝙩 𝙎𝙞𝙙𝙚𝙁𝙡𝙤𝙬 的魔法预告官网

</div>


## 🛠 技术栈

| 模块 | 技术 | 用途 |
|---|---|---|
| 结构与样式 | HTML5 + Tailwind CSS (CDN) | 响应式布局与排版 |
| 背景粒子 | **Three.js** r128 | 900 枚圆形尘埃 + 自转 |
| 动画编排 | **GSAP** 3.12.5 | 5 幕时间线精确控制 |

---

## 🚀 快速开始

### 1. 双击打开

```
双击 index.html → 浏览器自动打开
```

### 2. 本地静态服务器

```bash
# Python 3
python -m http.server 8080

# Node.js
npx serve .

# 然后访问
http://localhost:8080
```

### 3. 部署到任何静态托管

上传 `index.html` + `assets/` 目录到：
- GitHub Pages / Vercel / Netlify / Cloudflare Pages
- 任意 Nginx / Apache 静态资源服务器

---

## 📁 目录结构

```
SideFlow_WebSite/
├── index.html              # 主页面
├── assets/
│   ├── icon.png            # SideFlow 品牌图标
│   ├── github.png          # GitHub 链接图标
│   ├── CreativeN.png       # IntelliMarkets 链接图标
│   └── bilibili-color.png  # Bilibili 链接图标
└── README.md               # 本文件
```

---

## 🎯 响应式断点

| 断点 | 目标设备 | 组件尺寸 | 列数 |
|---|---|---|---|
| 默认 | 桌面 / 大屏 | 230 × 160 px | 4 列 |
| `max-width: 960px` | 平板 / 大屏手机 | 200 × 140 px | 4 列 |
| `max-width: 640px` | 主流手机 | 150 × 105 px | 3 列 |
| `max-width: 420px` | iPhone SE / 超小屏 | 128 × 92 px | 2 列 |

所有核心文字均使用 `clamp(最小, 动态, 最大)` 保证不出现字过小或溢出。

---

## 🎬 动画时间线（Timeline）

```
 0.00s │ 边缘极光从右侧亮起（opacity: 0 → 1）
 0.45s │ 组件开始飞入（staggered，逐枚 0.05s 延迟）
       │ Three.js 粒子 blur(18px) → blur(0)，size 0.35 → 1.2
 1.00s │ 极光衰减（opacity: 1 → 0.25）
 1.25s │ 组件开始退向背景网格墙（Z: 0 → -500, scale: 1 → 0.72）
       │ Three.js 粒子同步后退（Z: 0 → -45, scale: 1 → 0.55）
 1.35s │ 网格墙渐显，带 12deg 透视倾斜
 1.80s │ 高斯毛玻璃遮罩扩散，背景组件进一步虚化
 2.00s │ 'PROJECT SIDEFLOW' Label 淡入
 2.15s │ 主标题「魔法将在屏幕边缘发生」扫光渐入
 2.35s │ 副标题淡入
 2.55s │ CTA 胶囊按钮上浮淡入
 2.70s │ 底部三枚社交图标出现
 3.10s │ 主标题开启自动循环扫光（持续 6s 循环）
```

---

## 🔗 相关链接

- [SideFlow · GitHub (暂未公开)](https://github.com/SRInternet-Studio/SideFlow/)
- [IntelliMarkets · 插件市场](https://github.com/IntelliMarkets/SideFlow_Plugins_Index)

---

## 📝 自定义提示

### 调整组件内容

修改 `<div class="widget" data-widget="N"> ... </div>` 内部 HTML 即可。目前内置：

| `data-widget` | 展示内容 |
|---|---|
| 1 | Python 代码片段（剪贴板功能） |
| 2 | MagiClass 日程课表（打勾对齐符） |
| 3 | 局域网连接二维码 + 链接 |
| 4 | DeepSeek AI 对话气泡（闪烁光标） |
| 5 | 多模态文件缩略图 + OCR 提示 |
| 6 | 灵感速记 Quote |
| 7 | 今日任务清单 |

### 调整文字 / 主标题 / 副标题

- 主标题：`<h1 class="main-title">魔法将在屏幕边缘发生</h1>`
- 副标题：`.subtitle` 内部
- 按钮：`.cta` 内部文字

### 调整动画节奏

在文件底部 `<script>` 块的 `window.addEventListener('load', () => { ... })` 中：

- 想让动画更长 → 把 `duration` 值都乘以同一个系数（例如 `1.2`）
- 想让组件更多 / 更少 → 添加或删除 `.widget` DOM 节点，JS 会自动遍历
- 想更换主题色 → 搜索 `#00F2FE` / `#4FACFE` / `#001624` 并替换

### 调整组件列数 / 间距

编辑 `index.html` 内 JS 段：

```js
let cols;
if (W >= 960) cols = 4;    // ← 改这里
else if (W >= 640) cols = 3;
...
const gap = 14;            // ← 组件间距 (px)
```

---

## ⚠ 浏览器兼容性

| 浏览器 | 兼容情况 |
|---|---|
| Chrome / Edge 96+ | ✅ 完美 |
| Firefox 100+ | ✅ 完美 |
| Safari 15+ | ✅ 完美 |
| Safari 14- | ⚠ `backdrop-filter` 可能需要 `-webkit-` 前缀（已包含）|
| IE / 旧版 Edge | ❌ 不支持 |

页面使用的所有 JS 库均通过 CDN 加载，无需本地依赖。

---

## 📄 License

本仓库为 Project SideFlow 的官方主页静态资源，遵循与 SideFlow 主项目一致的开源协议。详情请见 [LICENSE](LICENSE)。