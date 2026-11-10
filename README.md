# 静态站点（项目介绍 / 使用文档 / 隐私政策）

这个目录可以直接部署到 GitHub Pages、Cloudflare Pages、Netlify、Vercel 或任意静态托管。
页面不依赖构建、CDN 或外部字体，上传后即可访问。

```
site/
├─ index.html          # 项目介绍（首页）
├─ guide.html          # 使用文档
├─ privacy.html        # 隐私政策（中英）
├─ permissions.html    # 权限说明
├─ style.css
├─ icon-128.png
├─ screenshots/        # 界面预览（与 store/screenshots 一致）
└─ README.md
```

## 本地预览

在当前目录执行：

```bash
npx serve .
# 或
python -m http.server 8080
```

如果在主仓库中，从仓库根目录执行：

```bash
npx serve site
```

## 部署到独立仓库（推荐）

本目录适合单独放到一个仓库，例如：
`https://github.com/LibraSunBoy/book-mark-sync-desc`

1. 把 `site/` 下的**全部内容**放到该仓库根目录，推送到 `main`。
2. 打开仓库 **Settings → Pages**。
3. **Build and deployment → Source** 选择 **Deploy from a branch**。
4. Branch 选择 `main`，目录选择 `/ (root)`，点击 Save。
5. 发布地址为 `https://<user>.github.io/<repo>/`。

本仓库对应的地址是：

```
https://librasunboy.github.io/book-mark-sync-desc/
```

可选：在仓库根目录放一个空的 `.nojekyll` 文件，跳过 Jekyll 处理。

### 自定义域名（bookmarkdock.app）

1. 在 **Settings → Pages → Custom domain** 填写 `bookmarkdock.app`；
2. 按 GitHub 提示配置 DNS（A 记录 / CNAME）；
3. 勾选 **Enforce HTTPS**；
4. 确认以下地址可匿名访问：
   - `https://bookmarkdock.app/`
   - `https://bookmarkdock.app/guide.html`
   - `https://bookmarkdock.app/privacy.html`
   - `https://bookmarkdock.app/permissions.html`

如果暂不使用自定义域名，请把 `store/listing.zh-CN.md` 与 `store/listing.en.md` 里的
主页和隐私政策地址改成实际的 Pages 地址。

## 部署在主仓库（可选）

如果不想拆仓库，也可以保留主仓库的 `site/` 目录，并使用主仓库里的
`.github/workflows/pages.yml`：

1. 在 GitHub 仓库 **Settings → Pages → Source** 选择 **GitHub Actions**；
2. 推送 `site/` 变更，工作流会自动上传 `site/` 并发布。

两种方式二选一即可，不要同时启用，避免出现两个不同的站点地址。

## 上线前检查

- [ ] 首页、使用文档、隐私政策、权限说明四个页面互相可跳转；
- [ ] 隐私政策可匿名访问，HTTPS；
- [ ] 页面标题与扩展名称一致；
- [ ] 文中不出现“我们收集…”这类与零遥测矛盾的表述；
- [ ] 页面中的 GitHub / Gitee 链接可访问；
- [ ] 联系邮箱可用（`dev@bookmarkdock.app`）。
