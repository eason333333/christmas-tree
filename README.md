# christmas-tree-v17.6

两个单文件圣诞树网页，都不需要 Node、不需要构建，双击就能打开，也能直接丢到 GitHub Pages / Netlify / Vercel / 对象存储。

| 文件 | 风格 | 依赖 |
|---|---|---|
| `christmas-tree-v17.6.html` | 礼物盒开场 + CSS 圣诞树 + 烟花 + 雪花 | 零依赖，完全离线可用 |
| `christmas-tree-particles-v17.6.html` | Three.js 3D 粒子圣诞树 + 辉光 + 飘雪 + 手势 | 仅 Three.js 走 CDN（首次打开需联网） |

---

## 一、浪漫卡片版 `christmas-tree-v17.6.html`

- 礼物盒开场：点击礼物盒 → 光芒爆发 + 粒子炸开 → 进入主场景
- CSS 圣诞树：彩虹渐变树身、树顶星星、闪烁彩灯、装饰球
- 漫天雪花 + 星空 + 极光 + Canvas 烟花 + 点击飘爱心
- Web Audio 实时合成《Jingle Bells》（右上角 🎵 开关）
- 合并自开源项目 [xuboboo/christmas-tree](https://github.com/xuboboo/christmas-tree)（MIT License）

自定义：搜索 `const CONFIG`，改 `message` / `signature` 即可。

---

## 二、3D 粒子版 `christmas-tree-particles-v17.6.html`

改自开源项目 [Roisten/Romantic-Christmas-Tree](https://github.com/Roisten/Romantic-Christmas-Tree)（Apache-2.0 License），做了这些改造：

- **手势识别改成可选**：原版启动时会先等摄像头 + 手势模型，模型加载失败就永远卡在 Loading；现在主场景立刻渲染，只有点「✋ 手势模式」才会请求摄像头
- **新增鼠标/手指交互**：拖动旋转、单击让粒子散开再聚回、滚轮拉近拉远
- **新增背景音乐**：右下角 🔔，Web Audio 实时合成《Jingle Bells》
- **失败兜底**：Three.js 若 12 秒内没加载出来，会显示文字提示而不是一直黑屏转圈
- **可放私照**：点「📷 换照片」选一个照片文件夹（或图片），照片会变成拍立得挂在树里，散开和手势捏合时会放大展示

操作说明：

- 拖动 = 旋转视角，单击空白 = 散开/聚回，滚轮 = 远近
- `H` 隐藏文字 UI
- 手势模式：手掌左右移动转动树，握拳切换造型，捏合抓取照片（需要 https + 摄像头授权）

---

## 部署到 GitHub Pages（自己上传）

### 方式 A：网页上传（不用装 git）

1. 在 GitHub 新建仓库，例如 `christmas-tree`，选 Public。
2. 进入仓库 → `Add file` → `Upload files`，把要用的 `.html` 拖进去 → `Commit changes`。
3. 仓库 → `Settings` → 左侧 `Pages` → `Source` 选 `Deploy from a branch`，Branch `main` / 目录 `/ (root)` → `Save`。
4. 等 1 分钟左右，访问：
   `https://<你的用户名>.github.io/christmas-tree/christmas-tree-particles-v17.6.html`
   （卡片版把文件名换成 `christmas-tree-v17.6.html`）

想让根地址直接打开，就把想当首页的那个文件重命名为 `index.html` 再上传。

### 方式 B：命令行

```bash
git clone https://github.com/<你的用户名>/christmas-tree.git
cd christmas-tree
# 把 html 文件复制进来（想直接访问根路径就命名为 index.html）
git add .
git commit -m "add christmas tree page"
git push
```

然后在 `Settings → Pages` 开启，规则同上。

### 小提示

- 卡片版零外部请求，任何网络环境都稳；粒子版首次打开要从 unpkg 拉 Three.js（约 600KB），国内偶尔慢，多刷一次就好，加载失败会有提示。
- 粒子版比卡片版吃显卡，老手机/集显笔记本可能掉帧，属正常。
- 音乐由浏览器实时合成，iOS 需关闭静音开关才听得到；微信里没声音就点「在浏览器中打开」。
- 手势模式需要 https（GitHub Pages 本身就是 https）和摄像头授权，拒绝授权不影响其它功能。

🎄 Merry Christmas!
