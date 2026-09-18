## 快捷指令（推荐，最方便）

直接用快捷指令切换 / 清除定位，无需打开选点页面：

- **wloc 设置地理位置**：https://www.icloud.com/shortcuts/a82717d8fdad4e6280866fcf911173f7
- **wloc 清理恢复位置**：https://www.icloud.com/shortcuts/f42632d406504f24a2cd163af4fe012f

<details>
<summary><b>自部署 Worker（推荐）</b></summary>

公共选点页面有请求上限，建议部署自己的实例：

- **Workers**: `https://wloc-spoofer.wloc.workers.dev/`
- **Pages**: `https://wloc-pages.pages.dev/`

**一键部署（Workers）：**

[![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button)](https://deploy.workers.cloudflare.com/?url=https://github.com/Make120/Apple/tree/main/worker)

> 一键部署仅支持 Workers 模式，点击按钮后按提示授权即可完成部署。

**手动部署（Workers）：**

```bash
# 1. 克隆仓库
git clone https://github.com/Yu9191/wloc.git
cd wloc/worker

# 2. 安装依赖
npm install

# 3. 登录 Cloudflare（首次需要）
npx wrangler login

# 1. 部署
npm run deploy
```

部署成功后会得到你自己的 Worker 地址（如 `https://wloc-spoofer.<你的子域名>.workers.dev`），用这个地址选点即可。

> 免费账户每天 10 万次请求，个人使用完全够用。

<details>
<summary>高级：Pages 部署</summary>

Pages 部署不支持一键按钮，需要手动执行：

```bash
git clone https://github.com/Yu9191/wloc.git
cd wloc/worker
npm install
npm run pages:deploy
```

> 必须走 `npm run pages:deploy`（它带 `-c wrangler.pages.jsonc`）。直接跑
> `wrangler pages deploy dist` 会丢掉配置里的 compatibility 设定。

部署时会提示设置 production branch，输入 `main` 即可。部署成功后得到 `https://<项目名>.pages.dev` 地址。

Pages 和 Workers 功能完全一致，按需选择即可。

</details>
