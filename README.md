# hykfft.github.io

静态站点，通过 GitHub Pages 从 `main` 分支根目录部署。

## 文件说明

| 文件 | 用途 |
|------|------|
| `index.html` | 站点首页，纯 HTML + CSS，无外部依赖 |
| `CNAME` | 自定义域名声明（`hykfft.dpdns.org`） |
| `.nojekyll` | 告知 GitHub Pages 跳过 Jekyll 处理，直接部署静态文件 |

## 托管说明

- **GitHub Pages**：从 `main` 分支根目录构建，配置在仓库 Settings → Pages 中完成。
- **Cloudflare**：当前仅作 DNS 解析（灰云模式）。NS 切换及 HTTPS/代理设置需由协调者在 Cloudflare 控制台手动完成，本仓库不保存任何凭证或账户信息。

## 维护

内容更新请提 PR 至 `main`，审核通过后合并即可触发 Pages 重新部署。
