# 打字练习

两个单文件网页打字游戏，无后端、无外部依赖，可以装到桌面当 App 用（PWA）。

| 页面 | 内容 |
|---|---|
| `index.html` | 入口，二选一 |
| `hanzi.html` | 汉字打字：200 个地名与多音字 + 45 句名言，两种模式 |
| `russian.html` | 俄语打字：A1 300 词，练 ЙЦУКЕН 键位 |

两个游戏都带轮次、错词重练、准确率统计和本地存档。

## 目录

```
typing/
├── index.html
├── hanzi.html
├── russian.html
├── manifest.json
├── sw.js
├── icons/
│   ├── icon-192.png
│   ├── icon-512.png
│   └── icon-maskable-512.png
└── README.md
```

## 部署到 GitHub Pages

```bash
cd ~/Desktop/typing
git init
git add .
git commit -m "打字练习 1.0"
git branch -M main
git remote add origin https://github.com/<用户名>/typing.git
git push -u origin main
```

仓库页面 → **Settings → Pages** → Source 选 `Deploy from a branch`，Branch 选 `main`，目录 `/ (root)`。

访问 `https://<用户名>.github.io/typing/`。Chrome 地址栏右侧会出现安装图标，装好后独立窗口运行。

> PWA 必须走 HTTPS 或 localhost。`file://` 直接打开能玩，但不会注册 Service Worker。

## 更新版本

改完任何文件后，把 `sw.js` 里的 `VERSION` 加 1，否则浏览器继续用旧缓存。

## 数据

进度存在浏览器 localStorage：

| 游戏 | 键名 |
|---|---|
| 汉字打字 · 词语 | `hanzi.typing.v1` |
| 汉字打字 · 句子 | `hanzi.sent.v1` |
| 俄语打字 | `ru.typing.v1` |

换域名、换浏览器、清缓存都会丢，也不跨设备同步。

## 输入提醒

汉字打字要用**英文输入法**打拼音字母；中文输入法开着会直接上屏汉字。
