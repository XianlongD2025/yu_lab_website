# Yu Lab website

清华大学化学系 Yu Lab 课题组网站。纯静态站点（HTML + CSS，无框架、无构建步骤），
可直接托管到 GitHub Pages，之后绑定自定义域名。

## 文件结构

| 文件 | 内容 |
| --- | --- |
| `index.html` | 首页（Hero / 研究方向 / 工作方式 / Selected work / News / 招聘） |
| `people.html` | 成员页（PI / 博后 / 博士 / 硕士 / 校友） |
| `publications.html` | 论文页（代表作 + 按年份筛选的完整列表） |
| `styles.css` | 所有样式，三页共用。改配色、字号在这里改 |

## 怎么修改内容（非程序员也能改）

所有文字都直接写在 `.html` 文件里，用任意文本编辑器打开即可修改。

- **改文字**：找到对应句子，直接替换。
- **改配色**：打开 `styles.css` 最上面的 `:root`，改 `--teal`（品牌绿）或 `--ink`（近黑）。
- **加一位成员**：在 `people.html` 里复制一个 `<div class="person">…</div>` 整块，改名字/职位/方向。
- **加一篇论文**：在 `publications.html` 的 `#pub-list` 里复制一个 `<div class="pub" data-year="2026">…</div>` 整块，
  改标题、作者、期刊、年份（`data-year` 要和显示的年份一致，筛选才准）。
- **换配图**：现在灰色斜纹块是占位（写着 `[ photo ]`、`[ TOC graphic ]`）。
  把图片放进 `images/` 文件夹，然后把占位 `<div>` 换成 `<img src="images/xxx.jpg" alt="…" style="width:100%;height:100%;object-fit:cover">`。
- **改邮箱/链接**：搜索 `guocanyu@mail.tsinghua.edu.cn` 或 `href="#"` 替换成真实地址。

改完直接双击 `index.html` 就能在浏览器里预览。

## 本地预览

双击 `index.html` 即可。或在本目录运行：

```bash
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000
```

## 部署到 GitHub Pages

仓库 Settings → Pages → Source 选 `Deploy from a branch` → 分支 `main` / 目录 `/ (root)` → Save。
一两分钟后会得到一个 `https://<用户名>.github.io/<仓库名>/` 的演示网址。

## 绑定自定义域名

1. 在仓库根目录新建一个名为 `CNAME` 的文件，内容就是你的域名，例如：

   ```
   www.yulab.org
   ```

2. 到你的域名服务商处添加 DNS：
   - 用二级域名（如 `www`）→ 添加 `CNAME` 记录指向 `<用户名>.github.io`
   - 用根域名（如 `yulab.org`）→ 添加 4 条 `A` 记录指向 GitHub Pages 的 IP：
     `185.199.108.153` / `185.199.109.153` / `185.199.110.153` / `185.199.111.153`
3. 回到 Settings → Pages 填入域名并勾选 `Enforce HTTPS`（证书签发需几分钟到几小时）。
