# 格式清理工具（Format Cleaner）

一款为中文内容创作者打造的在线格式处理工具，支持 Word 文档导入、纯文本导出、图片打包下载。基于 Cloudflare Pages 部署，零后端、秒加载。

👉 **在线访问：** https://format-cleaner.pages.dev

---

## 功能一览

### Word 文档处理

- **上传 .docx** — 拖拽或点击上传 Word 文档（2007+）
- **导出纯文本** — 提取文档正文，自动清理格式，图片位置用【图片 N】占位
- **下载图片包** — 将文档内所有图片打包为 zip 一键下载
- 上传后自动显示文档名和图片数量，视觉反馈清晰

### 格式处理

- **清格式 + 加空格** — 清除富文本残留，中英文之间自动加空格，保留段落间空行
- **仅清格式** — 纯清除 HTML / Word 粘贴残留，不动空格
- **仅加空格** — 保留原文，只在中文与英文/数字之间补上空格
- **清除空行** — 将所有空行去除，适合不需要段落间距的场景

### 标点处理

- **替换引号「」** — 将中文弯引号 `""` 转换为直角引号 `「」`
- **还原引号 `""`** — 将 `「」` 还原为标准中文弯引号

### 查找替换

支持自定义正则替换，适用于批量修改特定词汇或格式。

### 快捷键

| 快捷键 | 效果 |
|--------|------|
| `Shift + Delete` | 快速清除格式 |
| `Shift + Backspace` | 快速清除格式 |

---

## 使用场景

- 厂商发来 Word 通稿，需要快速转为纯文本发布
- 从网页、Word、WPS 复制的文章需要清理格式后再发布
- 多平台发布时统一引号风格（`""` vs `「」`）
- 批量替换特定词汇（配合正则使用）
- 快速为文章补全中英文之间的空格（符合排版规范）

---

## 技术细节

- **前端：** 纯原生 HTML + CSS + JavaScript，无框架依赖
- **Word 解析：** [mammoth.js](https://github.com/mwilliamson/mammoth.js) 将 .docx 转为 HTML 再提取纯文本
- **图片提取：** [JSZip](https://github.com/Stuk/jszip) 解压 .docx（本质是 ZIP），提取 `word/media/` 下图片
- **部署：** Cloudflare Pages（自动 HTTPS CDN）
- **隐私：** 所有处理均在浏览器本地完成，数据不经过任何服务器

---

## 本地运行

克隆后直接打开 `index.html` 即可，无需任何构建步骤。

```bash
git clone https://github.com/evaun/format-cleaner.git
cd format-cleaner
open index.html
```

---

## 部署到 Cloudflare Pages

```bash
npx wrangler pages deploy . --project-name=format-cleaner
```

或通过 GitHub Actions 绑定仓库实现自动部署。

---

> Crafted by Zacky Zhang @ IGN China
