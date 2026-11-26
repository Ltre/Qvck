# Cloudflare Workers 部署准备

本分支基于 `dev/2611-s1-e1`，与 GitHub Pages 的 `pages` 分支分离。

## 当前范围

- 将现有 `灵感速记.html` 原样作为 Workers Static Assets 的网站首页部署。
- 不改动原有网页功能；当前笔记仍保存在浏览器本地。
- 暂不配置 D1、R2、KV、用户登录或云端同步。
- 部署工作流仅支持手动触发，不会因推送自动发布。

## 首次部署前需要人工完成

1. 在 Cloudflare 账号创建具有 Workers 部署所需最小权限的 API Token。
2. 在 GitHub 仓库 Settings → Environments 创建名为 `cloudflare` 的环境，建议启用必要的部署审批与分支限制，只允许 `cloudflare` 分支。
3. 在该环境的 Secrets 中创建 `CLOUDFLARE_API_TOKEN`，粘贴 Token；不要写进代码或聊天。
4. 在该环境的 Variables 中创建 `CLOUDFLARE_ACCOUNT_ID`，填写 Cloudflare Account ID。
5. 在 GitHub Actions 手动运行 `Deploy Cloudflare Worker`，选择 `cloudflare` 分支。

注意：Cloudflare Workers 的公开访问地址和部署成功状态，必须以实际运行结果为准。配置 API Token 时应仅授予必要权限。后续接入数据库或应用密钥时使用 Cloudflare 资源绑定及 Secrets，不将敏感值放入前端。
