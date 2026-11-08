# 未来法庭 Render 部署包

`web/` 已注入官方 SDK（`worldline.js` + `futureCourtHandoff`），并包含 `global-items.json`。`render.yaml` 负责静态站点、CORS、CORP 和 wasm/pck 的 MIME。

## 部署

1. 把仓库根目录的 `render.yaml` 和 `web/` 推到 GitHub。
2. Render Dashboard → New → Blueprint → 连接该仓库 → Apply。
3. 等待部署完成，站点地址为 `https://<service-name>.onrender.com/`。
4. 入口填 `https://<service-name>.onrender.com/index.html`。

## 验收

- 根地址和 `/index.html` 都返回 200。
- 浏览器 Console 无 CORS/CSP 错误。
- 非满血、带旧道具从大厅进入，确认 `WL.ready()` 读档。
- 成功结局收到 `persisted:true`，放弃辩护收到失败回执。
- 自动预检：`node check.mjs <URL>` 和 `verify-online.ps1 -Url <URL> -RunOfficialCheck`。

Render 免费静态站点不休眠；但免费服务可能受账号配额限制，比赛期间不要删除服务。
