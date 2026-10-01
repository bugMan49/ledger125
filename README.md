# 收支记账本

手机端优先的收支记账网页。单文件、纯前端、无需服务器和构建步骤。

**在线使用：** 部署到 GitHub Pages 后，用手机浏览器打开仓库的 Pages 地址即可。

## 功能

- **三类账目**：收入 / 必要支出 / 可选支出，其中「必要支出」是独立分类（默认选中），列表带「必要」徽标，统计中单独成栏
- **移动端优先**：底部四页导航（记账 / 明细 / 统计 / 设置）、大号金额输入框（自动唤起数字键盘）、触控区域 ≥ 44px、适配 iPhone 刘海与底部横条、支持「添加到主屏幕」当 App 用
- **数据持久化**：记录实时存入浏览器本地存储，重开页面 / 重启手机自动加载历史数据；localStorage 不可用时自动降级到 sessionStorage 或内存，并给出提示
- **备份与恢复**：导出 `.json` 备份（按记录去重导入，可换手机恢复）、导出 `.csv` 表格（带 BOM，Excel 不乱码）
- **统计分析**：收入 / 必要支出 / 可选支出 / 结余汇总，必要支出占支出比例，近 6 个月趋势图，按分类构成排行
- **筛选**：按类型 + 按月份组合筛选

## 部署到 GitHub Pages

### 方式一：网页上传（不需要安装任何工具）

1. 打开 <https://github.com/new> 新建仓库，例如命名 `ledger`，选择 **Public**，点 **Create repository**
2. 在仓库页面点 **uploading an existing file**
3. 把本目录下的 `index.html` 拖进去，点 **Commit changes**
4. 进入仓库 **Settings → Pages**，`Source` 选 **Deploy from a branch**，`Branch` 选 **main** + **/ (root)**，点 **Save**
5. 等 1–2 分钟，访问 `https://你的用户名.github.io/ledger/`

### 方式二：命令行

```bash
git init
git add index.html README.md
git commit -m "收支记账本：手机端优先的收支记录网页"
git branch -M main
git remote add origin https://github.com/你的用户名/ledger.git
git push -u origin main
```

然后在 **Settings → Pages** 里把 Source 设为 `main` / `/ (root)`。

## 文件说明

| 文件 | 用途 |
| --- | --- |
| `index.html` | 主程序，GitHub Pages 默认打开这个文件 |
| `收支记账本.html` | 同一份程序的中文文件名副本，方便直接下载后双击本地使用 |

## 数据存储说明

- 数据保存在**访问者的浏览器**里（按域名区分），不会上传到任何服务器，仓库里也不含任何个人数据
- 因为是纯静态页面，**不同设备之间的数据不互通**；换设备时用「设置 → 导出备份文件」再在新设备「从备份恢复」
- 注意：如果之后同时用 `https://用户名.github.io/ledger/` 和本地双击打开的 `file://` 版本，两者数据是分开的

## 技术说明

- 单个 HTML 文件，内含全部 CSS 与原生 JavaScript，无外部依赖、无 CDN 请求
- 可直接双击本地打开使用，也可放到任意静态托管上（GitHub Pages / Cloudflare Pages / Vercel 均可）
