# hykfft.github.io — 江山时序（许可合规部署版）

本站托管「[江山时序 Jiangshan Atlas](https://github.com/DeanChensj/jiangshan-map)」的静态页面，部署于 GitHub Pages，域名 [hykfft.dpdns.org](http://hykfft.dpdns.org)。

## 功能说明

| 功能 | 状态 | 说明 |
|------|------|------|
| 时间轴 · 疆域演变 | ✅ 完整 | 战国 → 今 18 个历史时期 |
| 政权高亮 / 一级政区 | ✅ 完整 | polity + region 两层 |
| 城市点地溯源 | ✅ 完整 | 全朝代沿革与史事纪要 |
| 人物行迹 / 历史事件 | ✅ 完整 | 人物路线弧线与逐站展开 |
| 万能搜索 · 深链分享 | ✅ 完整 | `?year=` `?person=` 等参数 |
| 古今名关 / 诗词名胜 | ✅ 完整 | 专属图标与卡片 |
| 舆图寻址挑战 | ✅ 完整 | 古地名猜题模式 |
| 古琴雅乐 | ✅ 完整 | 公有领域录音 |
| **郡 / 州 / 府级边界** | ❌ 已移除 | 源自 CHGIS V6，条款禁止再分发（见下文） |
| **透视镜现代省界** | ❌ 已移除 | 源自 DataV GeoAtlas，再分发条款未确认 |

## 许可证与数据来源

### 代码与大部分数据

| 内容 | 来源 | 许可 |
|------|------|------|
| 代码（HTML/CSS/JS） | [DeanChensj/jiangshan-map](https://github.com/DeanChensj/jiangshan-map) | GPL-3.0 |
| 政权疆域（polity） | aourednik/historical-basemaps 起点，史籍手工重绘 | GPL-3.0 |
| 一级政区（region） | 史籍手工绘制 | GPL-3.0 |
| 古地名 / 事件 / 行迹 | 史籍整理 | GPL-3.0 |
| 河流、湖泊、周边国家 | 公有领域 | 公有领域 |
| 地形晕渲 | AWS Terrain Tiles（SRTM/GMTED2010/ETOPO1，公有领域） | GPL-3.0（图片） |
| 古琴录音 | Wikimedia Commons | 公有领域 |

### 已移除的受限数据

**郡 / 州 / 府级边界（`prefecture` 层）**  
源自 CHGIS V6（哈佛大学费正清中国研究中心 & 复旦大学历史地理研究中心）及 Robert M. Hartwell China Historical GIS。  
原始条款：**仅限学术、非商业用途，不得再分发，不适用 GPL-3.0**。  
本部署已在构建时从 `js/atlas_snapshots.js` 和 `js/atlas_boot.js` 中彻底剥离该图层，部署产物中不含任何 CHGIS 数据。  
引用格式：*CHGIS, Version: 6. © Fairbank Center for Chinese Studies of Harvard University and the Center for Historical Geographical Studies at Fudan University, 2016.*

**现代省界（DataV GeoAtlas）**  
「透视镜」功能所用现代中国省界数据来自阿里云 DataV GeoAtlas，其再分发条款无法在当前条件下确认，因此依照用户要求将 `js/china_geo_data.js` 中的 `PROVINCE_OUTLINES` 置为空数组，历史水系、湖泊、地名标注等公有领域数据仍保留。

如需含完整图层的版本，请访问上游原作者官网：https://deanchen.me/jiangshan-map/

### 上游溯源

- 上游仓库：[DeanChensj/jiangshan-map](https://github.com/DeanChensj/jiangshan-map)
- 本部署基于上游 commit：`a801119578d6dd16f5d85fd49efc387195a1b895`（2026-11-10 08:47:50 UTC）

## 文件结构

```
/                           ← 根目录（GitHub Pages 从 main 分支根部署）
├── index.html              ← 教育科普门户首页
├── topics/                 ← 旧版专题书签兼容重定向（→ /landscape/topics/）
├── CNAME                   ← 自定义域名 hykfft.dpdns.org
├── .nojekyll               ← 告知 GitHub Pages 跳过 Jekyll 处理
├── LICENSE                 ← GPL-3.0 全文
├── sitemap.xml / robots.txt / llms.txt
└── landscape/              ← 江山时序历史地图应用（全部地图资源在此）
    ├── index.html          ← 地图主页面
    ├── css/style.css
    ├── js/                 ← atlas_snapshots.js 已剥离 prefecture；china_geo_data.js 已移除省界
    ├── assets/             ← 音频、地形晕渲、图标等
    ├── topics/             ← 35 个朝代专题页面
    ├── geojson/
    └── manifest.webmanifest
```

## 托管说明

- **GitHub Pages**：从 `main` 分支根目录部署，配置在仓库 Settings → Pages。
- 地图应用访问路径：`https://hykfft.dpdns.org/landscape/`
- 旧分享链接 `/?year=...` 等参数会自动跳转到 `/landscape/?year=...`
- 旧 `/topics/*.html` 书签会自动跳转到 `/landscape/topics/*.html`
- **Cloudflare**：当前仅作 DNS 解析。NS 切换及 HTTPS/代理设置需由协调者在 Cloudflare 控制台完成，本仓库不保存任何凭证。

## 维护

内容更新请提 PR 至 `main`，审核通过合并后 GitHub Pages 自动重新部署。
